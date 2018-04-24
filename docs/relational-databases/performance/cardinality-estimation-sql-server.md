---
title: Stima della cardinalità (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 09/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: performance
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cardinality estimator
- CE (cardinality estimator)
- estimating cardinality
ms.assetid: baa8a304-5713-4cfe-a699-345e819ce6df
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 71d5c75e27a71a76f014376ad61a04a13bac389c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="cardinality-estimation-sql-server"></a>Stima della cardinalità (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  
Questo articolo illustra come valutare e scegliere la migliore configurazione di stima della cardinalità per il sistema SQL. Per la maggior parte dei sistemi è disponibile la stima della cardinalità più recente perché è la più accurata. La stima della cardinalità prevede il numero di righe che verranno probabilmente restituite dalla query. La stima della cardinalità è usata da Query Optimizer per generare il piano di query ottimale. Con stime più accurate, Query Optimizer è in genere in grado di produrre un piano di query migliore.  
  
Il sistema di applicazioni può includere una query importante il cui piano viene configurato su un piano più lento a causa della nuova stima di cardinalità. Una query di questo tipo potrebbe essere simile quanto segue:  
  
- Una query OLTP (elaborazione di transazioni online) che viene eseguita con una frequenza tale da determinare l'esecuzione simultanea di più istanze della query.  
- Un'istruzione SELECT con aggregazione sostanziale che viene eseguita durante l'orario lavorativo di OLTP.  
  
Sono implementate tecniche per identificare una query che risulta più lenta con la nuova stima della cardinalità. Inoltre, sono disponibili opzioni per la risoluzione del problema di prestazioni.  
  
  
## <a name="versions-of-the-ce"></a>Versioni della stima della cardinalità  
  
 Nel 1998 è stato incluso un aggiornamento importante della stima della cardinalità nell'ambito di Microsoft SQL Server 7.0, per cui il livello di compatibilità era 70. Gli aggiornamenti successivi sono iniziati con [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], con livelli di compatibilità 120 e superiori. Gli aggiornamenti della stima di cardinalità per i livelli 120 e superiori integrano presupposti e algoritmi che funzionano bene nel data warehousing moderno e nei carichi di lavoro OLTP.  
  
 **Livello di compatibilità:** per assicurarsi che il database sia impostato su un determinato livello, è possibile usare il codice Transact-SQL seguente per [COMPATIBILITY_LEVEL](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  

```sql  
SELECT ServerProperty('ProductVersion');  
go  
  
ALTER DATABASE <yourDatabase>  
    SET COMPATIBILITY_LEVEL = 130;  
go  
  
SELECT d.name, d.compatibility_level  
    FROM sys.databases AS d  
    WHERE d.name = 'yourDatabase';  
go  
```  
  
 Per un database di SQL Server impostato sul livello di compatibilità 120 o su un livello superiore, l'attivazione del [flag di traccia 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) impone al sistema di usare la stima di cardinalità di livello 70.  
  
 **Stima di cardinalità legacy:** per un database di SQL Server impostato sul livello di compatibilità 120 o superiore, è possibile attivare la stima di cardinalità di livello 70 a livello di database usando [MODIFICARE LA CONFIGURAZIONE CON AMBITO DATABASE](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).
  
```sql  
ALTER DATABASE
    SCOPED CONFIGURATION  
        SET LEGACY_CARDINALITY_ESTIMATION = ON;  
go  
  
SELECT name, value  
    FROM sys.database_scoped_configurations  
    WHERE name = 'LEGACY_CARDINALITY_ESTIMATION';  
```  
 
 Oppure, a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, l'[hint per la query](../../t-sql/queries/hints-transact-sql-query.md) `USE HINT ('FORCE_LEGACY_CARDINALITY_ESTIMATION')`.
 
 ```sql  
SELECT CustomerId, OrderAddedDate  
    FROM OrderTable  
    WHERE OrderAddedDate >= '2016-05-01'; 
    OPTION (USE HINT ('FORCE_LEGACY_CARDINALITY_ESTIMATION'));  
```
 
 **Query Store:** a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], Query Store è uno strumento utile per esaminare le prestazioni delle query. In [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] in **Esplora oggetti** nel nodo del database viene visualizzato un nodo **Query Store** quando Query Store è abilitato.  
  
```sql  
ALTER DATABASE <yourDatabase>  
    SET QUERY_STORE = ON;  
go  
  
SELECT  
        q.actual_state_desc AS [actual_state_desc-ofQueryStore],  
        q.desired_state_desc,  
        q.query_capture_mode_desc  
    FROM  
        sys.database_query_store_options  AS q;  
go  
  
ALTER DATABASE <yourDatabase>  
    SET QUERY_STORE CLEAR;  
```  
  
 > [!TIP] 
 > Si consiglia di installare la versione più recente di [Management Studio](http://msdn.microsoft.com/library/mt238290.aspx) e di aggiornarlo spesso.  
  
 Un'altra opzione per tenere traccia del processo relativo alle stime di cardinalità consiste nell'usare l'evento esteso denominato **query_optimizer_estimate_cardinality**. Il seguente codice T-SQL di esempio viene eseguito su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Scrive un file con estensione xel in C:\Temp\ (percorso modificabile). Quando si apre il file con estensione xel in [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)], le informazioni dettagliate sono visualizzate in modo intuitivo.  
  
```sql  
DROP EVENT SESSION Test_the_CE_qoec_1 ON SERVER;  
go  
  
CREATE EVENT SESSION Test_the_CE_qoec_1  
    ON SERVER  
    ADD EVENT sqlserver.query_optimizer_estimate_cardinality  
    (  
        ACTION (sqlserver.sql_text)  
            WHERE (  
                sql_text LIKE '%yourTable%'  
                and sql_text LIKE '%SUM(%'  
            )  
    )  
    ADD TARGET package0.asynchronous_file_target   
        (SET  
            filename = 'c:\temp\xe_qoec_1.xel',  
            metadatafile = 'c:\temp\xe_qoec_1.xem'  
        );  
go  
  
ALTER EVENT SESSION Test_the_CE_qoec_1  
    ON SERVER  
    STATE = START;  --STOP;  
go  
```  
  
 Per informazioni sugli eventi estesi specifici per [!INCLUDE[ssSDS](../../includes/sssds-md.md)], vedere [Eventi estesi nel database SQL](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/).  
  
  
## <a name="steps-to-assess-the-ce-version"></a>Procedura per valutare la versione della stima di cardinalità  
  
 Di seguito sono indicate alcune operazioni da eseguire per stabilire se una delle query più importanti presenta prestazioni inferiori con la stima di cardinalità più recente. Alcuni dei passaggi vengono completati eseguendo un esempio di codice presentato in una sezione precedente.  
  
1.  Aprire [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)]. Assicurarsi che il database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia impostato sul massimo livello di compatibilità disponibile.  
  
2.  Seguire questa procedura preliminare:  
  
    1.  Aprire [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)].  
  
    2.  Eseguire T-SQL per assicurarsi che il database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia impostato sul massimo livello di compatibilità disponibile.  
  
    3.  Assicurarsi che la configurazione `LEGACY_CARDINALITY_ESTIMATION` del database sia impostata su OFF.  
  
    4.  Eseguire un'istruzione CLEAR per cancellare il contenuto dell'archivio query. Naturalmente, verificare che l'archivio query sia impostato su ON.  
  
    5.  Eseguire l'istruzione: `SET NOCOUNT OFF;`  
  
3.  Eseguire l'istruzione: `SET STATISTICS XML ON;`  
  
4.  Eseguire la query importante.  
  
5.  Nel riquadro dei risultati, nella scheda **Messaggi** , notare il numero effettivo di righe interessate.  
  
6.  Nel riquadro dei risultati, nella scheda **Risultati** , fare doppio clic sulla cella che contiene le statistiche in formato XML. Viene visualizzato un piano di query grafico.  
  
7.  Fare clic con il pulsante destro del mouse nella prima casella del piano di query grafico e scegliere **Proprietà**.  
  
8.  Per un successivo confronto con una configurazione diversa, notare i valori per le proprietà seguenti:  
  
    -   **CardinalityEstimationModelVersion**.  
  
    -   **Numero stimato di righe**.  
  
    -   **Costo I/O stimato***Stimato* simili che riguardano le prestazioni effettive anziché le previsioni del numero di righe.  
  
    -   **Operazione logica** e **Operazione fisica**. *Parallelismo* è un valore adeguato.  
  
    -   **Modalità di esecuzione effettiva**. *Batch* è un valore adeguato, migliore di *Riga*.  
  
9. Confrontare il numero stimato di righe con il numero effettivo di righe. La stima di cardinalità è imprecisa del 1% (per eccesso o per difetto) o del 10%?  
  
10. Eseguire: `SET STATISTICS XML OFF;`  
  
11. Eseguire l'istruzione T-SQL per abbassare il livello di compatibilità del database di un livello (ad esempio da 130 a 120).  
  
12. Eseguire di nuovo tutti i passaggi non preliminari.  
  
13. Confrontare i valori delle proprietà della stima di cardinalità delle due esecuzioni.  
  
    - La percentuale di imprecisione con la stima di cardinalità più recente è inferiore rispetto a quella meno recente?  
  
14. Infine, confrontare i vari valori delle proprietà delle prestazioni delle due esecuzioni.  
  
    -   La query ha usato un piano diverso nelle due stime di cardinalità?  
  
    -   La query è risultata più lenta con la stima di cardinalità più recente?  
  
    -   A meno che la query non venga eseguita con prestazioni migliori e con un piano diverso con la stima di cardinalità precedente, quasi certamente è preferibile usare la stima di cardinalità più recente.  
  
    -   Se però la query viene eseguita con un piano più veloce con la stima di cardinalità precedente, è possibile forzare il sistema affinché usi il piano più veloce e ignori la stima di cardinalità. In questo modo si può usare la stima di cardinalità più recente per tutto, mantenendo il piano più veloce nel caso particolare.  
  
## <a name="how-to-activate-the-best-query-plan"></a>Come attivare il piano di query ottimale  
  
Si supponga che con la nuova stima di cardinalità venga generato un piano di query più lento per la query. Ecco alcune opzioni per attivare il piano più veloce.  
  
È possibile impostare il livello di compatibilità su un valore inferiore rispetto a quello più recente, per l'intero database.  
  
- In questo modo viene attivata la stima di cardinalità legacy, ma per tutte le query viene usata la stima di cardinalità precedente e meno accurata.  
  
- Il livello di compatibilità precedente non potrà inoltre usufruire degli importanti miglioramenti apportati a Query Optimizer.  
  
Per fare in modo che l'intero database, o solo una query specifica, usi la stima di cardinalità precedente mantenendo i miglioramenti di Query Optimizer, è possibile usare `LEGACY_CARDINALITY_ESTIMATION`.  
  
Per il massimo controllo, è possibile *forzare* il sistema SQL a usare il piano generato con la stima di cardinalità precedente durante i test. Dopo avere *aggiunto* il piano preferito, è possibile impostare l'intero database per l'uso della compatibilità e della stima di cardinalità più recenti. L'opzione viene elaborata successivamente.  
  
### <a name="how-to-force-a-particular-query-plan"></a>Come forzare un piano di query specifico  
  
L'archivio query offre diversi modi per forzare l'uso di un determinato piano di query:  
  
- Eseguire **sp_query_store_force_plan**.  
  
- In [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] espandere il nodo **Query Store**, fare clic con il pulsante destro del mouse su **Top Resource Consuming Nodes** (Primi nodi per consumo di risorse) e quindi su **View Top Resource Consuming Nodes** (Visualizza primi nodi per consumo di risorse). Verranno visualizzati i pulsanti **Forza piano** e **Annulla forzatura piano**.  
  
 Per altre informazioni sull'archivio query, vedere [Monitoraggio delle prestazioni con Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).  
  
  
## <a name="examples-of-ce-improvements"></a>Esempi di miglioramenti della stima di cardinalità  
  
Questa sezione descrive query di esempio che usufruiscono dai miglioramenti implementati nella stima di cardinalità nelle versioni recenti. Si tratta di informazioni in background che non richiedono un'azione specifica da parte dell'utente.  
  
### <a name="example-a-ce-understands-maximum-value-might-be-higher-than-when-statistics-were-last-gathered"></a>Esempio A. La stima di cardinalità riconosce che il valore massimo potrebbe essere superiore rispetto al momento in cui sono state raccolte le statistiche  
  
Si supponga che le statistiche per OrderTable siano state raccolte per l'ultima volta il 30-04-2016, quando il valore massimo per OrderAddedDate era 30-04-2016. La stima di cardinalità per il livello di compatibilità 120 (e livelli più elevati) comprende che le colonne in OrderTable con dati in ordine *crescente* potrebbero contenere valori maggiori rispetto al valore massimo registrato dalle statistiche. Questa consapevolezza migliora il piano di query per le istruzioni SQL SELECT come la seguente.  
  
```sql  
SELECT CustomerId, OrderAddedDate  
FROM OrderTable  
WHERE OrderAddedDate >= '2016-05-01';  
```  
  
### <a name="example-b-ce-understands-that-filtered-predicates-on-the-same-table-are-often-correlated"></a>Esempio B. La stima di cardinalità riconosce che i predicati filtrati nella stessa tabella sono spesso correlati  
  
Nell'istruzione SELECT seguente sono presenti predicati filtrati su Model e ModelVariant. Si comprende intuitivamente che quando Model è "Xbox" esiste la possibilità che ModelVariant sia "One" poiché Xbox ha una variante denominata One.  
  
Il livello 120 della stima di cardinalità riconosce che potrebbe esistere una correlazione tra le due colonne nella stessa tabella, ovvero Model e ModelVariant. La stima di cardinalità prevede in modo più preciso quante righe verranno restituite dalla query e Query Optimizer genera un piano più ottimale.  
  
```sql  
SELECT Model, Purchase_Price  
FROM dbo.Hardware  
WHERE Model  = 'Xbox'  AND  
      ModelVariant = 'One';  
```  
  
### <a name="example-c-ce-no-longer-assumes-any-correlation-between-filtered-predicates-from-different-tables"></a>Esempio C. La stima di cardinalità non presume più alcuna correlazione tra i predicati filtrati da tabelle diverse 
Una nuova ricerca estesa su carichi di lavoro moderni e dati di business effettivi rivelano che i filtri del predicato da tabelle diverse in genere non sono correlati tra loro. Nella query seguente, la stima di cardinalità presuppone che non esista alcuna correlazione tra s.type e r.date. La stima di cardinalità riduce quindi la stima del numero di righe restituite.  
  
```sql  
SELECT s.ticket, s.customer, r.store  
FROM dbo.Sales    AS s  
CROSS JOIN dbo.Returns  AS r  
WHERE s.ticket = r.ticket  AND  
      s.type   = 'toy'     AND  
      r.date   = '2016-05-11';  
```  
  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [Optimizing Your Query Plans with the SQL Server 2014 Cardinality Estimator](http://msdn.microsoft.com/library/dn673537.aspx) (Ottimizzazione dei piani di query con la stima di cardinalità di SQL Server 2014)  
 [Query Hints](../../t-sql/queries/hints-transact-sql-query.md)   (Hint per la query)  
 [Monitoraggio delle prestazioni tramite Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)    
 [Guida sull'architettura di elaborazione delle query](../../relational-databases/query-processing-architecture-guide.md)   
