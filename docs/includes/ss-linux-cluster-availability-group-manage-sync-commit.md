## <a name="managing-synchronous-commit-mode"></a>Gestione della modalità con commit singolo

>[!WARNING]
>In alcuni casi un gruppo di disponibilità di SQL Server in modalità con commit sincrono in Linux potrebbe essere vulnerabile alla perdita di dati. Vedere le informazioni dettagliate seguenti relative alla causa principale e la soluzione alternativa per evitare la perdita di dati. Questo problema verrà risolto nelle versioni future.

###<a name="pacemaker-notification-for-availability-group-resource-promotion"></a>Notifica di Pacemaker per l'innalzamento di livello delle risorse del gruppo di disponibilità

Prima della versione CTP 1.4, l'agente delle risorse Pacemaker per i gruppi di disponibilità non può sapere se una replica contrassegnata come `SYNCHRONOUS_COMMIT` è effettivamente aggiornata o meno. La sincronizzazione della replica con la replica primaria potrebbe essersi interrotta senza che ciò sia noto. L'agente potrebbe quindi alzare di livello una replica non aggiornata impostandola come primaria e se l'operazione avesse esito positivo ciò comporterebbe la perdita di dati. 

SQL Server 2017 CTP 1.4 aggiunge `sequence_number` a `sys.availability_groups` per risolvere questo problema. `sequence_number` è un valore BIGINT a incremento progressivo costante che rappresenta il livello di aggiornamento della replica del gruppo di disponibilità locale in relazione al resto del sistema. L'esecuzione di failover, operazioni di aggiunta o rimozione di repliche e altre operazioni relative ai gruppi di disponibilità comporta l'aggiornamento di questo numero. Il numero viene aggiornato nella replica primaria e quindi inviato a quelle secondarie. Una replica secondaria aggiornata avrà quindi lo stesso numero della replica primaria.

Quando Pacemaker decide di alzare di livello una replica e impostarla come primaria, invia prima di tutto una notifica a tutte le repliche per estrarre il numero di sequenza e archiviarlo. Successivamente, quando Pacemaker cerca effettivamente di alzare di livello una replica impostandola come primaria, l'operazione viene eseguita solo se il numero di sequenza della replica è il più alto di tutti i numeri di sequenza. In caso contrario, la replica rifiuta l'operazione. In questo modo, solo la replica con il numero di sequenza più alto può essere alzata di livello e impostata come primaria e non si verifica alcuna perdita dei dati.

Si noti che ciò funziona solo se almeno una replica disponibile per l'innalzamento di livello ha lo stesso numero di sequenza della replica primaria precedente. Poiché l'agente delle risorse richiede che Pacemaker invii notifiche a tutte le repliche, la risorsa di disponibilità deve essere configurata con `notify=true`. Per ogni risorsa `ocf:mssql:ag` esistente, l'utente dovrà aggiornare la configurazione con `notify=true` prima di aggiornare il pacchetto `mssql-server-ha` a CTP 1.4, altrimenti la risorsa entra in stato di errore. 

### <a name="how-to-avoid-potential-for-data-loss"></a>Come evitare potenziali perdite di dati 

Nel caso seguente un gruppo di disponibilità può ancora essere vulnerabile alla perdita di dati. In un cluster che include cinque nodi, se c'è un gruppo di disponibilità con repliche in tre istanze di SQL Server, è possibile che la replica primaria e una replica secondaria siano più avanzate rispetto all'altra replica secondaria. In questo caso, il valore di `sequence_number` in `sys.availability_groups` sarà superiore rispetto alle altre repliche. In questa situazione, se le due repliche perdono la connettività con il resto del cluster, Pacemaker può vedere i tre nodi rimanenti come un quorum e consentire l'innalzamento di livello della replica latente come primaria. Questa situazione comporta un rischio di perdita di dati.

sql2017 introduce una nuova funzionalità per forzare la disponibilità di un certo numero di repliche secondarie prima che sia possibile eseguire il commit delle transazioni nella replica primaria. `REQUIRED_COPIES_TO_COMMIT` consente di impostare un numero di repliche che devono eseguire il commit nel log delle transazioni del database di replica secondaria prima che una transazione possa procedere. È possibile usare questa opzione con `CREATE AVAILABILITY GROUP` o `ALTER AVAILABILITY GROUP`. Vedere [CREATE AVAILABILITY GROUP](http://msdn.microsoft.com/library/ff878399.aspx).

Per evitare la potenziale perdita di dati descritta in precedenza, impostare `REQUIRED_COPIES_TO_COMMIT` sul numero massimo di repliche sincronizzate. Le versioni future includeranno una logica predefinita per la gestione automatica dell'impostazione di `REQUIRED_COPIES_TO_COMMIT`.
Quando l'opzione `REQUIRED_COPIES_TO_COMMIT` è impostata, le transazioni nei database di replica primaria attendono fino a quando non viene eseguito il commit della transazione nel numero richiesto di log delle transazioni del database di replica secondaria sincrona. Se non c'è un numero sufficiente di repliche secondarie sincrone online, le transazioni vengono interrotte fino a quando non riprende la comunicazione con un numero sufficiente di repliche secondarie.

L'esempio seguente imposta un gruppo di disponibilità denominato [ag1] su `REQUIRED_COPIES_TO_COMMIT = 2`. 

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1]
SET (REQUIRED_COPIES_TO_COMMIT = 2)
```

Nell'esempio precedente se il gruppo di disponibilità ha due repliche secondarie, attende fino a quando entrambe le repliche secondarie non riconoscono il commit. Se una replica smette di rispondere, le transazioni vengono bloccate.
