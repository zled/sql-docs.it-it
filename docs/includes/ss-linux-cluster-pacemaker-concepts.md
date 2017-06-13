## <a name="pacemakerNotify"></a>Comprendere l'agente di risorse di SQL Server per pacemaker

Prima della versione CTP 1.4, l'agente di risorsa Pacemaker per gruppi di disponibilità potrebbe non sapere se una replica è contrassegnata come `SYNCHRONOUS_COMMIT` o non è stato effettivamente aggiornato. La sincronizzazione della replica con la replica primaria potrebbe essersi interrotta senza che ciò sia noto. In questo modo l'agente può alzare di livello una replica non aggiornata a principale - che, se l'operazione riesce, potrebbe causare la perdita di dati. 

SQL Server 2017 CTP 1.4 aggiunto `sequence_number` a `sys.availability_groups` per risolvere questo problema. `sequence_number`è un valore BIGINT a incremento progressivo costante che rappresenta la replica del gruppo di disponibilità locale di aggiornamento è rispetto al resto delle repliche del gruppo di disponibilità. Eseguire failover, l'aggiunta o rimozione di repliche e altre operazioni di gruppo di disponibilità aggiornare questo numero. Il numero viene aggiornato nel server primario, quindi inserito alle repliche secondarie. In questo modo una replica secondaria è aggiornata avrà la stessa sequence_number del database primario. 

Quando Pacemaker decide di alzare di livello una replica primaria, prima invia una notifica a tutte le repliche per estrarre il numero di sequenza e archiviarlo (questo caso si parla di alzare di pre-livello notifica). Successivamente, quando Pacemaker esegue effettivamente un tentativo di promuovere una replica primaria, la replica solo promuove se stesso se il numero di sequenza è il più elevato di tutti i numeri di sequenza da tutte le repliche e rifiuta l'operazione Alza di livello in caso contrario. In questo modo, solo la replica con il numero di sequenza più alto può essere alzata di livello e impostata come primaria e non si verifica alcuna perdita dei dati. 

Si noti che ciò funziona solo se almeno una replica disponibile per l'innalzamento di livello ha lo stesso numero di sequenza della replica primaria precedente. A tale scopo, il comportamento predefinito prevede che l'agente di risorsa Pacemaker impostare automaticamente `REQUIRED_COPIES_TO_COMMIT` in modo che almeno uno sincrono commit secondario replica è aggiornato e disponibile per essere la destinazione di un failover automatico. Con ogni azione di monitoraggio, il valore di `REQUIRED_COPIES_TO_COMMIT` viene calcolato (e aggiornati se necessario) come ('numero di repliche con commit sincrono' / 2). Quindi, in fase di failover, sarà necessario l'agente di risorsa (`total number of replicas`  -  `required_copies_to_commit` repliche) per rispondere alla pre-promuovere notifica per essere in grado di alzare di livello uno di essi al database primario. La replica con il più elevato `sequence_number` verrà alzata di livello database primario. 

Ad esempio, si consideri il caso di un gruppo di disponibilità con tre repliche sincrone - una replica primaria e due repliche secondarie con commit sincrono.

- `REQUIRED_COPIES_TO_COMMIT`3 / 2 = 1

- Il numero di repliche per rispondere ai pre-fini dell'azione di richiesto è 1-3 = 2. Pertanto 2 repliche devono essere per il failover deve essere attivata. Ciò significa che, nel caso di interruzione primaria, se una delle repliche secondarie non risponde e risponde solo una delle repliche secondarie per la pre-promuovere azione, l'agente di risorsa non può garantire che il database secondario che ha risposto ha sequence_number il più elevato, e non viene attivato un failover.

Un utente può scegliere di ignorare il comportamento predefinito e configurare la risorsa del gruppo di disponibilità per non impostare `REQUIRED_COPIES_TO_COMMIT` automaticamente come indicato in precedenza.

>[!IMPORTANT]
>Quando `REQUIRED_COPIES_TO_COMMIT` è 0 è rischio di perdita di dati. In caso di interruzione dell'istanza primaria, l'agente di risorsa non verrà attivata automaticamente un failover. L'utente deve decidere se si desidera attendere per il sito primario ripristinare o eseguire manualmente il failover.

Per impostare `REQUIRED_COPIES_TO_COMMIT` su 0, eseguire:

```bash
sudo pcs resource update <**ag1**> required_copies_to_commit=0
```

Per ripristinare l'impostazione valore calcolato, eseguire:

```bash
sudo pcs resource update <**ag1**> required_copies_to_commit=
```

>[!NOTE]
>Aggiornamento delle proprietà di risorsa fa sì che tutte le repliche arrestare e riavviare. Ciò significa primario verrà temporaneamente essere abbassato di livello secondario, quindi promosso nuovamente che casue temporaneo scriverà indisponibilità. Il nuovo valore per REQUIRED_COPIES_TO_COMMIT verrà essere impostato solo una volta le repliche vengono riavviate, in modo non istantaneo all'esecuzione del comando PC.

## <a name="balancing-high-availability-and-data-protection"></a>Bilanciamento del carico di elevata disponibilità e protezione dei dati 

Il comportamento predefinito precedente si applica anche in caso di 2 repliche sincrone (primarie + secondarie). Pacemaker utilizzerà `REQUIRED_COPIES_TO_COMMIT = 1` per verificare che il database secondario è sempre aggiornata per la protezione dati massimo replica.  

>[!WARNING]
>Questo include maggiore rischio di mancata disponibilità della replica primaria a causa di interruzioni pianificate o meno per la replica secondaria. L'utente può scegliere di modificare il comportamento predefinito dell'agente di risorse ed eseguire l'override di `REQUIRED_COPIES_TO_COMMIT` su 0:

```bash
sudo pcs resource update <**ag1**> required_copies_to_commit=0
```

Quando sottoposto a override, l'agente di risorse utilizzerà la nuova impostazione per `REQUIRED_COPIES_TO_COMMIT` e arrestare il calcolo. Ciò significa che gli utenti devono aggiornare manualmente conseguenza (ad esempio, se si aumenta il numero di repliche).

Nelle tabelle seguenti vengono descritti i risultati di un'interruzione del servizio per le repliche primarie o secondarie in configurazioni risorsa gruppo di disponibilità diverso:

### <a name="availability-group---2-sync-replicas"></a>Gruppo di disponibilità - 2 repliche di sincronizzazione

| |Interruzione primaria |Interruzione di una replica secondaria
|:---|:--- |:--- |
|`REQUIRED_COPIES_TO_COMMIT=0`|Utente deve eseguire un FAILOVER manuale. <br>Potrebbe essere la perdita di dati.<br> Nuovo database primario è L/S |Primario è di lettura/scrittura, esecuzione senza perdita di dati
|`REQUIRED_COPIES_TO_COMMIT=1` * |Cluster rilasciano automaticamente il FAILOVER <br>Senza perdita di dati. <br> Nuovo database primario rifiuterà tutte le connessioni fino a quando non primario precedente consente di recuperare e gruppo di disponibilità come database secondario. |Primario rifiuterà tutte le connessioni finché non viene ripristinato secondario.

\*Agente di risorse di SQL Server per il comportamento predefinito Pacemaker.

### <a name="availability-group---3-sync-replicas"></a>Gruppo di disponibilità - 3 repliche di sincronizzazione

| |Interruzione primaria |Interruzione di una replica secondaria
|:---|:--- |:--- |
|`REQUIRED_COPIES_TO_COMMIT=0`|Utente deve eseguire un FAILOVER manuale. <br>Potrebbe essere la perdita di dati. <br>Nuovo database primario è L/S |Il filegroup primario è L/S
|`REQUIRED_COPIES_TO_COMMIT=1` * |Cluster rilasciano automaticamente il FAILOVER. <br>Senza perdita di dati. <br>Nuovo database primario è RW |Il filegroup primario è L/S 

\*Agente di risorse di SQL Server per il comportamento predefinito Pacemaker.