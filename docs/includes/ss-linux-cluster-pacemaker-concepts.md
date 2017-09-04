## <a name="pacemakerNotify"></a>Comprendere l'agente delle risorse SQL Server per Pacemaker

Prima della versione CTP 1.4, l'agente delle risorse Pacemaker per i gruppi di disponibilità non può sapere se una replica contrassegnata come `SYNCHRONOUS_COMMIT` è effettivamente aggiornata o meno. La sincronizzazione della replica con la replica primaria potrebbe essersi interrotta senza che ciò sia noto. L'agente potrebbe quindi alzare di livello una replica non aggiornata impostandola come primaria e, se l'operazione avesse esito positivo, ciò comporterebbe la perdita di dati. 

SQL Server CTP 2017 1.4 ha aggiunto `sequence_number` a `sys.availability_groups` per risolvere questo problema. `sequence_number` è un valore BIGINT a incremento progressivo costante che rappresenta il livello di aggiornamento della replica del gruppo di disponibilità locale in relazione al resto delle repliche del gruppo di disponibilità. L'esecuzione di failover, l'aggiunta o la rimozione di repliche e altre operazioni relative ai gruppi di disponibilità comporta l'aggiornamento di questo numero. Il numero viene aggiornato nella replica primaria e quindi inviato alle repliche secondarie. Una replica secondaria aggiornata avrà quindi lo stesso sequence_number della replica primaria. 

Quando Pacemaker decide di alzare di livello una replica e impostarla come primaria, invia prima di tutto una notifica a tutte le repliche per estrarre il numero di sequenza e archiviarlo (questa operazione viene chiamata notifica precedente all'innalzamento di livello). Successivamente, quando Pacemaker cerca effettivamente di alzare di livello una replica impostandola come primaria, l'operazione viene eseguita solo se il numero di sequenza della replica è il più alto di tutti i numeri di sequenza di tutte le repliche. In caso contrario, la replica rifiuta l'operazione. In questo modo, solo la replica con il numero di sequenza più alto può essere alzata di livello e impostata come primaria e non si verifica alcuna perdita dei dati. 

Si noti che ciò funziona solo se almeno una replica disponibile per l'innalzamento di livello ha lo stesso numero di sequenza della replica primaria precedente. A questo scopo, il comportamento predefinito prevede che l'agente delle risorse Pacemaker imposti automaticamente `REQUIRED_COPIES_TO_COMMIT` in modo che almeno una replica secondaria di commit sincrona sia aggiornata e disponibile a essere la destinazione di un failover automatico. Con ogni azione di monitoraggio, il valore di `REQUIRED_COPIES_TO_COMMIT` viene calcolato (e aggiornato se necessario) come ('numero di repliche di commit sincrone' / 2). Quindi, in fase di failover, l'agente di risorsa richiederà (repliche `total number of replicas`  -  `required_copies_to_commit`) di rispondere alla notifica pre-innalzamento per poter alzare una di queste al livello primario. La replica con il `sequence_number` più elevato verrà promossa al livello primario. 

Ad esempio, si consideri il caso di un gruppo di disponibilità con tre repliche sincrone: una replica primaria e due repliche secondarie con commit sincrono.

- `REQUIRED_COPIES_TO_COMMIT`  è pari a 3 / 2 = 1

- Il numero di repliche richiesto per rispondere all'azione di pre-innalzamento è 3 - 1 = 2. Pertanto, perché il failover sia attivato, 2 repliche devono essere innalzate. Ciò significa che, nel caso di interruzione primaria, se una delle repliche secondarie non risponde e solo una delle repliche secondarie risponde all'azione di pre-innalzamento, l'agente della risorsa non può garantire che la replica secondaria che ha risposto abbia il sequence_number più elevato, e non viene attivato un failover.

Un utente può scegliere di sostituire il comportamento predefinito e configurare la risorsa del gruppo di disponibilità per non impostare `REQUIRED_COPIES_TO_COMMIT` automaticamente, come indicato in precedenza.

>[!IMPORTANT]
>Quando `REQUIRED_COPIES_TO_COMMIT` è 0 esiste il rischio di perdita dei dati. In caso di interruzione della replica primaria, l'agente della risorsa non attiverà automaticamente un failover. L'utente deve decidere se vuole attendere il recupero della replica primaria o eseguire il failover manualmente.

Per impostare `REQUIRED_COPIES_TO_COMMIT` su 0, eseguire:

```bash
sudo pcs resource update <**ag_cluster**> required_copies_to_commit=0
```

Il comando equivalente se si usa crm (in SLES) è:

```bash
sudo crm resource param <**ag_cluster**> set required_synchronized_secondaries_to_commit 0
```

Per ripristinare il valore calcolato predefinito, eseguire:

```bash
sudo pcs resource update <**ag_cluster**> required_copies_to_commit=
```

>[!NOTE]
>L'aggiornamento delle proprietà della risorsa produce l'arresto e il riavvio di tutte le repliche. Ciò significa che la replica primaria verrà temporaneamente abbassata al livello secondario, quindi promossa nuovamente, con una conseguente indisponibilità di scrittura temporanea. Il nuovo valore per REQUIRED_COPIES_TO_COMMIT verrà impostato solo dopo il riavvio delle repliche, pertanto non sarà istantaneo all'esecuzione del comando pcs.

## <a name="balancing-high-availability-and-data-protection"></a>Bilanciamento della disponibilità elevata e della protezione dei dati 

Il comportamento predefinito precedente si applica anche in caso di 2 repliche sincrone (primaria + secondaria). Pacemaker imposterà `REQUIRED_COPIES_TO_COMMIT = 1` come valore predefinito per garantire che la replica secondaria sia sempre aggiornata per la massima protezione dei dati.  

>[!WARNING]
>Ciò comporta un maggiore rischio di indisponibilità della replica primaria a causa di interruzioni pianificate o meno della replica secondaria. L'utente può scegliere di modificare il comportamento predefinito dell'agente della risorsa ed eseguire l'override di `REQUIRED_COPIES_TO_COMMIT` su 0:

```bash
sudo pcs resource update <**ag1**> required_copies_to_commit=0
```

Dopo che è stato sottoposto a override, l'agente della risorsa userà la nuova impostazione per `REQUIRED_COPIES_TO_COMMIT` e arrestare il calcolo. Ciò significa che gli utenti devono aggiornarlo manualmente di conseguenza (ad esempio, se aumentano il numero di repliche).

Nelle tabelle seguenti vengono descritti i risultati di un'interruzione del servizio per le repliche primarie o secondarie in diverse configurazioni di risorse del gruppo di disponibilità:

### <a name="availability-group---2-sync-replicas"></a>Gruppo di disponibilità - 2 repliche sincrone

| |Interruzione primaria |Interruzione di una replica secondaria
|:---|:--- |:--- |
|`REQUIRED_COPIES_TO_COMMIT=0`|L'utente deve eseguire un FAILOVER manuale. <br>Potrebbe verificarsi la perdita di dati.<br> La nuova replica primaria è L/S |La replica primaria è L/S, esecuzione esposta alla perdita di dati
|`REQUIRED_COPIES_TO_COMMIT=1` * |IL cluster rilascerà automaticamente il FAILOVER <br>Nessuna perdita di dati. <br> La nuova replica primaria rifiuterà tutte le connessioni fino a quando verrà recuperata la replica primaria precedente e sarà unita al gruppo di disponibilità come replica secondaria. |La replica primaria rifiuterà tutte le connessioni fino al recupero della replica secondaria.

\* Comportamento predefinito dell'agente delle risorse SQL Server per Pacemaker.

### <a name="availability-group---3-sync-replicas"></a>Gruppo di disponibilità - 3 repliche sincrone

| |Interruzione primaria |Interruzione di una replica secondaria
|:---|:--- |:--- |
|`REQUIRED_COPIES_TO_COMMIT=0`|L'utente deve eseguire un FAILOVER manuale. <br>Potrebbe verificarsi la perdita di dati. <br>La nuova replica primaria è L/S |La replica primaria è L/S
|`REQUIRED_COPIES_TO_COMMIT=1` * |Il cluster rilascerà automaticamente il FAILOVER. <br>Nessuna perdita di dati. <br>La nuova replica primaria è L/S |La replica primaria è L/S 

\* Comportamento predefinito dell'agente delle risorse SQL Server per Pacemaker.