---
title: Note sulla versione di SQL Server 2014 | Microsoft Docs
ms.custom: 
ms.date: 01/31/2017
ms.prod: sql-server-2014
ms.technology: server-general
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf4c4922-80b3-4be3-bf71-228247f97004
caps.latest.revision: "100"
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3c507363ad05be7410ae69fc6d5f6748ad1738cb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-2014-release-notes"></a>SQL Server 2014 Release Notes
Nel presente documento Note sulla versione vengono descritti i problemi noti di cui è necessario essere a conoscenza prima di installare o risolvere problemi relativi a [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
## <a name="top"></a>Sommario  
[1.0 Prima di installare](#BeforeInstall)  
  
[2.0 Documentazione sul prodotto](#ProdDoc)  
  
[3.0 Motore di database](#DBEngine)  
  
[4.0 Reporting Services](#SSRS)  
  
[5.0 SQL Server 2014 in macchine virtuali di Microsoft Azure](#AzureVM)  
  
[6.0 Analysis Services](#SSAS)  
  
[7.0 Data Quality Services](#DQS)  
  
[8.0 Gestione spazio aggiornamenti](#UA)  
  
## <a name="BeforeInstall"></a>1.0 Prima di installare  
  
### <a name="11-limitations-and-restrictions-in-sql-server-2014-rtm"></a>1.1 Limitazioni e restrizioni in SQL Server 2014 RTM  
  
#### <a name="111-general-limitations-and-restrictions"></a>1.1.1 Limitazioni e restrizioni generali  
  
1.  L'aggiornamento da SQL Server 2014 CTP 1 a SQL Server 2014 RTM NON è supportato.  
  
2.  L'installazione side-by-side di SQL Server 2014 CTP 1 e SQL Server 2014 RTM NON è supportata.  
  
3.  Il collegamento o il ripristino di un database SQL Server 2014 CTP 1 a SQL Server 2014 RTM NON è supportato.  
  
**Soluzione alternativa:** nessuna.  
  
#### <a name="12-considerations-for-upgrading-sql-server-2014-ctp-2-to-sql-server-2014-rtm-and-downgrading-from-sql-server-2014-rtm-to-sql-server-2014-ctp-2"></a>1.2 Considerazioni per l'aggiornamento di SQL Server 2014 CTP 2 a SQL Server 2014 RTM e il downgrade da SQL Server 2014 RTM a SQL Server 2014 CTP 2  
  
#### <a name="121-upgrading-from-sql-server-2014-ctp-2-to-sql-server-rtm-is-fully-supported"></a>1.2.1 L'aggiornamento da SQL Server 2014 CTP 2 a SQL Server RTM è completamente supportato.  
In particolare, è possibile:  
  
1.  Collegare un database SQL Server 2014 CTP 2 a un'istanza di SQL Server 2014 RTM.  
  
2.  Ripristinare in un'istanza di SQL Server 2014 RTM un backup di database creato in SQL Server 2014 CTP 2.  
  
3.  Aggiornamento sul posto a SQL Server 2014 RTM.  
  
4.  Aggiornamento in sequenza a SQL Server 2014 RTM. È necessario passare alla modalità di failover manuale prima di avviare l'aggiornamento in sequenza. Per informazioni dettagliate, fare riferimento alla pagina [Aggiornamento dei server dei gruppi di disponibilità con tempi di inattività e perdita dei dati minimi](http://msdn.microsoft.com/library/dn178483.aspx) .  
  
5.  Non è possibile visualizzare i dati raccolti dai set di raccolta prestazioni delle transazioni installati in SQL Server 2014 CTP 2 tramite SQL Server Management Studio in SQL Server 2014 RTM e viceversa. Utilizzare SQL Server Management Studio in SQL Server CTP 2014 2 per visualizzare i dati raccolti dal set di raccolta installato in SQL Server 2014 CTP 2 e utilizzare SQL Server Management Studio in SQL Server 2014 RTM per visualizzare i dati raccolti dal set di raccolta installato in SQL Server 2014 RTM.  
  
### <a name="122-downgrading-from-sql-server-2014-rtm-to-sql-server-2014-ctp-2"></a>1.2.2 Downgrade da SQL Server 2014 RTM a SQL Server 2014 CTP 2  
Questa caratteristica non è supportata.  
  
**Soluzione alternativa:** per il downgrade non sono disponibili soluzioni alternative. Si consiglia di eseguire il backup del database prima di eseguire l'aggiornamento a SQL Server 2014 RTM.  
  
![Icona freccia usata con il collegamento Torna all'inizio](../sql-server/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Torna all'inizio](#top)  
  
## <a name="13-incorrect-version-of-streaminsight-client-on-sql-server-2014-mediaisocab"></a>1.3 Versione non corretta di StreamInsight Client su supporto/ISO/CAB di SQL Server 2014  
La versione errata di StreamInsight.msi e StreamInsightClient.msi si trova nel percorso seguente in supporto/ISO/CAB di SQL Server (StreamInsight\\\<Architecture\>\\\<ID Lingua\>).  
  
**Soluzione alternativa** : scaricare e installare la versione corretta dalla [pagina per il download di SQL Server 2014 Feature Pack](http://go.microsoft.com/fwlink/?LinkID=306709).  
  
## <a name="ProdDoc"></a>2.0 Documentazione sul prodotto  
  
### <a name="21-report-builder-content-is-not-available-in-some-languages"></a>2.1 Il contenuto di Generatore report non è disponibile in alcune lingue  
**Problema:** il contenuto di Generatore report non è disponibile nelle seguenti lingue.  
  
-   Greco (el-GR)  
  
-   Norvegese (Bokmål) (nb-NO)  
  
-   Finlandese (fi-FI)  
  
-   Danese (da-DK)  
  
In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]il contenuto è disponibile in un file CHM fornito con il prodotto in queste lingue. I file CHM non vengono più forniti con il prodotto e il contenuto di Generatore report è disponibile solo su MSDN. MSDN non supporta queste lingue. Generatore report è stato rimosso da TechNet e non è più disponibile nelle lingue supportate.  
  
**Soluzione alternativa:** nessuna.  
  
### <a name="22-powerpivot-content-is-not-available-in-some-languages"></a>2.2 Il contenuto di PowerPivot non è disponibile in alcune lingue  
**Problema:** il contenuto di Power Pivot non è disponibile nelle seguenti lingue.  
  
-   Greco (el-GR)  
  
-   Norvegese (Bokmål) (nb-NO)  
  
-   Finlandese (fi-FI)  
  
-   Danese (da-DK)  
  
-   Ceco (cs-CZ)  
  
-   Ungherese (hu-HU)  
  
-   Olandese (Paesi Bassi) (nl-NL)  
  
-   Polacco (pl-PL)  
  
-   Svedese (sv-SE)  
  
-   Turco (tr-TR)  
  
-   Portoghese (Portogallo) (pt-PT)  
  
In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], il contenuto era disponibile in TechNet ed era disponibile in queste lingue. Il contenuto è stato rimosso da TechNet e non è più disponibile in queste lingue supportate.  
  
**Soluzione alternativa:** nessuna.  
  
![Icona freccia usata con il collegamento Torna all'inizio](../sql-server/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Torna all'inizio](#top)  
  
## <a name="DBEngine"></a>3.0 Motore di database  
  
### <a name="31-changes-made-for-standard-edition-in-sql-server-2014-rtm"></a>3.1 Modifiche apportate alla Standard Edition in SQL Server 2014 RTM  
SQL Server 2014 Standard presenta le seguenti modifiche:  
  
-   La funzionalità di estensione del pool di buffer consente di utilizzare la dimensione massima pari a fino 4 volte la memoria configurata.  
  
-   La memoria massima è aumentata da 64 GB a 128 GB.  
  
### <a name="32-in-memory-oltp-issues"></a>3.2 Problemi OLTP in memoria  
  
#### <a name="321-memory-optimization-advisor-flags-default-constraints-as-incompatible"></a>3.2.1 L'Ottimizzazione guidata per la memoria contrassegna i vincoli predefiniti come incompatibili  
**Problema:** l'Ottimizzazione guidata per la memoria in SQL Server Management Studio contrassegna tutti i vincoli predefiniti come incompatibili. Non tutti i vincoli predefiniti sono supportati in una tabella ottimizzata per la memoria; l'ottimizzazione guidata non opera una distinzione tra i tipi di vincoli predefiniti supportati e quelli non supportati. Tra i vincoli predefiniti supportati sono incluse tutte le costanti, le espressioni e le funzioni predefinite supportate all'interno di stored procedure compilate in modo nativo. Per visualizzare l'elenco delle funzioni supportate nelle stored procedure compilate in modo nativo, fare riferimento alla pagina [Costrutti supportati in stored procedure compilate in modo nativo](http://msdn.microsoft.com/library/dn452279(v=sql.120).aspx).  
  
**Soluzione alternativa:** se si desidera utilizzare l'ottimizzazione guidata per individuare i blocchi, ignorare i vincoli predefiniti compatibili. Per utilizzare l'Ottimizzazione guidata per la memoria per la migrazione delle tabelle con vincoli predefiniti compatibili, ma senza altri blocchi, attenersi alla procedura seguente:  
  
1.  Rimuovere i vincoli predefiniti dalla definizione della tabella.  
  
2.  Utilizzare l'Ottimizzazione guidata per produrre uno script di migrazione nella tabella.  
  
3.  Aggiungere nuovamente i vincoli predefiniti allo script di migrazione.  
  
4.  Eseguire lo script di migrazione.  
  
#### <a name="322-informational-message-file-access-denied-incorrectly-reported-as-an-error-in-the-sql-server-2014-error-log"></a>3.2.2 Il messaggio informativo "accesso file negato" viene erroneamente restituito come errore nel log degli errori di SQL Server 2014  
**Problema:** quando si riavvia un server con database che contengono tabelle ottimizzate per la memoria, è possibile che venga visualizzato il tipo seguente di messaggi di errore nel log degli errori di SQL Server 2014:  
  
```  
[ERROR]Unable to delete file C:\Program Files\Microsoft SQL   
Server\....old.dll. This error may be due to a previous failure to unload   
memory-optimized table DLLs.  
```  
  
In realtà si tratta di un messaggio informativo e non è richiesto alcun intervento da parte dell'utente.  
  
**Soluzione alternativa:** nessuna. È un messaggio informativo.  
  
#### <a name="323-missing-index-details-incorrectly-report-included-columns-for-memory-optimized-table"></a>3.2.3 Nei dettagli sugli indici mancanti sono erroneamente segnalate colonne incluse per la tabella ottimizzata per la memoria  
**Problema:** se SQL Server 2014 rileva un indice mancante per una query in una tabella ottimizzata per la memoria, segnala un indice mancante in SHOWPLAN_XML e nelle DMV dell'indice mancante, ad esempio sys.dm_db_missing_index_details. In alcuni casi, i dettagli sugli indici mancanti contengono le colonne incluse. Poiché tutte le colonne sono incluse in modo implicito in tutti gli indici nelle tabelle ottimizzate per la memoria, non è consentito specificare in modo esplicito le colonne incluse con gli indici ottimizzati per la memoria.  
  
**Soluzione alternativa:** non specificare la clausola INCLUDE con gli indici nelle tabelle ottimizzate per la memoria.  
  
#### <a name="324-missing-index-details-omit-missing-indexes-if-a-hash-index-exists-but-is-not-suitable-for-the-query"></a>3.2.4 Nei dettagli sugli indici mancanti vengono omessi gli indici mancanti se esiste un indice hash che non è adatto per la query  
**Problema:** se si dispone di un indice HASH sulle colonne di una tabella ottimizzata per la memoria a cui fa riferimento una query, ma l'indice non può essere usato per la query, SQL Server 2014 non segnalerà sempre un indice mancante in SHOWPLAN_XML e nella DMV sys.dm_db_missing_index_details.  
  
In particolare, se una query contiene predicati di uguaglianza che interessano un subset delle colonne chiave dell'indice o se contiene predicati di disuguaglianza che interessano colonne chiave dell'indice, l'indice HASH non può essere utilizzato così com'è ed è necessario un altro indice per eseguire la query in modo efficace.  
  
**Soluzione alternativa:** se si utilizzano gli indici hash, controllare le query e i piani di query per determinare se le query possono trarre vantaggio dalle operazioni Index Seek su un subset della chiave di indice o sui predicati di disuguaglianza. Se è necessario eseguire la ricerca su un subset della chiave di indice, utilizzare un indice NON CLUSTER oppure un indice HASH esattamente sulle colonne in cui eseguire la ricerca. Se è necessario eseguire la ricerca in un predicato di disuguaglianza, utilizzare un indice NON CLUSTER anziché HASH.  
  
#### <a name="325-failure-when-using-a-memory-optimized-table-and-memory-optimized-table-variable-in-the-same-query-if-the-database-option-readcommittedsnapshot-is-set-to-on"></a>3.2.5 Si verifica un errore quando si utilizza una tabella ottimizzata per la memoria e una variabile di tabella ottimizzata per la memoria nella stessa query, se l'opzione di database READ_COMMITTED_SNAPSHOT è impostata su ON  
**Problema:** se l'opzione di database READ_COMMITTED_SNAPSHOT è impostata su ON e si accede sia a una tabella ottimizzata per la memoria sia a una variabile di tabella ottimizzata per la memoria nella stessa istruzione al di fuori del contesto di una transazione utente, è possibile che venga visualizzato il messaggio di errore seguente:  
  
```  
Msg 41359  
A query that accesses memory optimized tables using the READ COMMITTED  
isolation level, cannot access disk based tables when the database option  
READ_COMMITTED_SNAPSHOT is set to ON. Provide a supported isolation level  
for the memory optimized table using a table hint, such as WITH (SNAPSHOT).  
```  
  
**Soluzione alternativa:** usare l'hint di tabella WITH (SNAPSHOT) con la variabile di tabella o impostare l'opzione di database MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT su ON, tramite l'istruzione seguente:  
  
```  
ALTER DATABASE CURRENT   
SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON  
```  
  
#### <a name="326-procedure-and-query-execution-statistics-for-natively-compiled-stored-procedures-record-worker-time-in-multiples-of-1000"></a>3.2.6 Nelle statistiche di esecuzione di stored procedure e query per le stored procedure compilate in modo nativo il tempo del processo viene registrato in multipli di 1000  
**Problema:** dopo avere abilitato la raccolta delle statistiche di esecuzione di stored procedure o query per le stored procedure compilate in modo nativo usando sp_xtp_control_proc_exec_stats o sp_xtp_control_query_exec_stats, *_worker_time verrà visualizzato in multipli di 1000 nelle DMV sys.dm_exec_procedure_stats e sys.dm_exec_query_stats. Le esecuzioni di query con un tempo del processo inferiore a 500 microsecondi verranno segnalate con un valore worker_time pari a 0.  
  
**Soluzione alternativa:** nessuna. È opportuno non fare affidamento sul valore worker_time segnalato nelle DMV delle statistiche di esecuzione per le query con esecuzione rapida nelle stored procedure compilate in modo nativo.  
  
#### <a name="327-error-with-showplanxml-for-natively-compiled-stored-procedures-that-contain-long-expressions"></a>3.2.7 Si verifica un errore con SHOWPLAN_XML per le stored procedure compilate in modo nativo che contengono espressioni lunghe  
**Problema:** se una stored procedure compilata in modo nativo contiene un'espressione lunga, l'acquisizione di SHOWPLAN_XML per la stored procedure, tramite l'opzione T-SQL SET SHOWPLAN_XML ON o l'opzione "Visualizza piano di esecuzione stimato" in Management Studio, può causare l'errore seguente:  
  
```  
Msg 41322. MAT/PIT export/import encountered a failure for memory  
optimized table or natively compiled stored procedure with object ID  
278292051 in database ID 6. The error code was  
0xc00cee81.  
```  
  
**Soluzione alternativa:** sono disponibili due soluzioni.  
  
1.  Aggiungere le parentesi all'espressione, in modo analogo all'esempio seguente:  
  
    Anziché:  
  
    ```  
    SELECT @v0 + @v1 + @v2 + ... + @v199  
    ```  
  
    Scrivere:  
  
    ```  
    SELECT((@v0 + ... + @v49) + (@v50 + ... + @v99)) + ((@v100 + ... + @v149) + (@v150 + ... + @v199))  
    ```  
  
2.  Creare una seconda stored procedure con un'espressione leggermente semplificata per l'uso con lo showplan. La forma generale del piano deve essere la stessa. Ad esempio, anziché:  
  
    ```  
    SELECT @v0 +@v1 +@v2 +...+@v199  
    ```  
  
    Scrivere:  
  
    ```  
    SELECT @v0 +@v1  
    ```  
  
#### <a name="328-using-a-string-parameter-or-variable-with-datepart-and-related-functions-in-a-natively-compiled-stored-procedure-results-in-an-error"></a>3.2.8 L'utilizzo di un parametro di stringa o di una variabile con DATEPART e funzioni correlate in una stored procedure compilata in modo nativo genera un errore  
**Problema:** quando si usa un parametro o una variabile con un tipo di dati stringa, ad esempio (var)char o n(var)char, con le funzioni predefinite DATEPART, DAY, MONTH e YEAR in una stored procedure compilata in modo nativo, viene visualizzato un messaggio di errore indicante che il tipo di dati datetimeoffset non è supportato con le stored procedure compilate in modo nativo.  
  
**Soluzione alternativa:** assegnare la variabile o il parametro di stringa a una nuova variabile di tipo datetime2 e utilizzare tale variabile nella funzione DATEPART, DAY, MONTH o YEAR. Esempio:  
  
```  
DECLARE @d datetime2 = @string  
DATEPART(weekday, @d)  
```  
  
#### <a name="329-native-compilation-advisor-flags-delete-from-clauses-incorrectly"></a>3.2.9 Assistente compilazione nativa contrassegna in modo errato le clausole DELETE FROM  
**Problema:** Assistente compilazione nativa contrassegna in modo errato le clausole DELETE FROM all'interno di una stored procedure come incompatibili.  
  
**Soluzione alternativa:** nessuna.  
  
### <a name="33-register-through-ssms-adds-dac-meta-data-with-mismatched-instance-ids"></a>3.3 La registrazione tramite SSMS aggiunge metadati DAC con ID istanza non corrispondenti  
**Problema:** quando si esegue la registrazione o l'eliminazione di un pacchetto di applicazione livello dati (con estensione dacpac) tramite SQL Server Management Studio, le tabelle sysdac* non vengono aggiornate correttamente per consentire a un utente di eseguire query nella cronologia di dacpac per il database.  I valori id_instance per sysdac_history_internal e sysdac_instances_internal non corrispondono, quindi non è possibile creare un join.  
  
**Soluzione alternativa:** questo problema è stato corretto con la ridistribuzione del feature pack di [Data-Tier Application Framework](https://www.microsoft.com/download/details.aspx?id=42295).  Dopo l'applicazione dell'aggiornamento, tutte le nuove voci della cronologia useranno il valore elencato per id_instance nella tabella sysdac_instances_internal.  
  
Se si è già verificato il problema relativo ai valori instance_id non corrispondenti, per correggere la mancata corrispondenza dei valori è necessario connettersi al server come utente con privilegi di scrittura per il database MSDB e aggiornare i valori instance_id in modo che corrispondano.  Se si sono verificati più eventi di registrazione e annullamento della registrazione dello stesso database, può essere necessario esaminare data e ora per vedere quali record corrispondono ai valori instance_id correnti.  
  
1.  Connettersi al server in SQL Server Management Studio utilizzando un account di accesso con autorizzazioni di aggiornamento per MSDB.  
  
2.  Aprire una nuova query utilizzando il database MSDB.  
  
3.  Eseguire la query per visualizzare tutte le istanze di applicazione livello dati attive.  Individuare l'istanza che si vuole correggere e annotare il valore instance_id:  
  
    `select * from` sysdac_instances_internal  
  
4.  Eseguire la query per visualizzare tutte le voci della cronologia:  
  
    `select * from` sysdac_history_internal  
  
5.  Identificare le righe che devono corrispondere all'istanza da correggere  
  
6.  Aggiornare il valore sysdac_history_internal.instance_id con il valore annotato nel passaggio 3 (dalla tabella sysdac_instances_internal):  
  
    `update` sysdac_history_internal `set` instance_id = '\<valore del passaggio 3\>' `where` \<espressione corrispondente alle righe da aggiornare\>  
  
![Icona freccia usata con il collegamento Torna all'inizio](../sql-server/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Torna all'inizio](#top)  
  
## <a name="SSRS"></a>4.0 Reporting Services  
  
### <a name="41-the-sql-server-2012-reporting-services-native-mode-report-server-cannot-run-side-by-side-with-sql-server-2014-reporting-services-sharepoint-components"></a>4.1 Il server di report in modalità nativa SQL Server 2012 Reporting Services non può essere eseguito side-by-side con componenti di SharePoint di SQL Server 2014 Reporting Services  
**Problema:** il servizio Windows in modalità nativa di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 'SQL Server Reporting Services' (ReportingServicesService.exe) non viene avviato se sono presenti componenti di SharePoint di [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] installati nello stesso server.  
  
**Soluzione alternativa:** disinstallare i componenti di SharePoint di [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] e riavviare il servizio Windows di Microsoft SQL Server 2012 Reporting Services.  
  
**Altre informazioni:**  
  
La modalità nativa di[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non può essere eseguita side-by-side con nessuno degli elementi seguenti:  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Componente aggiuntivo per prodotti SharePoint  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Servizio condiviso di SharePoint  
  
L'installazione side-by-side impedisce l'avvio del servizio Windows in modalità nativa di [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Nel log degli eventi di Windows saranno presenti messaggi di errore simili ai seguenti:  
  
```  
Log Name:   Application  
Source:          Report Server (<SQL instance ID>)  
Event ID:        117  
Task Category:   Startup/Shutdown  
Level:           Error  
Keywords:        Classic  
Description:     The report server database is an invalid version.  
  
Log Name:      Application  
Source:        Report Server (<SQL instance ID>)  
Event ID:      107  
Task Category: Management  
Level:         Error  
Keywords:      Classic  
Description:   Report Server (DENALI) cannot connect to the report server database.  
```  
  
Per ulteriori informazioni, vedere [Suggerimenti e risoluzione dei problemi relativi a SQL Server 2014 Reporting Services](http://go.microsoft.com/fwlink/?LinkID=391254).  
  
### <a name="42-required-upgrade-order-for-multi-node-sharepoint-farm-to-sql-server-2014-reporting-services"></a>4.2 Ordine obbligatorio per l'aggiornamento della farm di SharePoint a nodi multipli a SQL Server 2014 Reporting Services  
**Problema:** il rendering del report in una farm a nodi multipli ha esito negativo se le istanze del servizio SharePoint Shared di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] vengono aggiornate prima di tutte le istanze del componente aggiuntivo di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] per prodotti SharePoint.  
  
**Soluzione alternativa:** in una farm di SharePoint a nodi multipli,  
  
1.  aggiornare prima tutte le istanze del componente aggiuntivo di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] per prodotti SharePoint.  
  
2.  quindi, aggiornare tutte le istanze del servizio SharePoint Shared di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
Per ulteriori informazioni, vedere [Suggerimenti e risoluzione dei problemi relativi a SQL Server 2014 Reporting Services](http://go.microsoft.com/fwlink/?LinkID=391254).  
  
![Icona freccia usata con il collegamento Torna all'inizio](../sql-server/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Torna all'inizio](#top)  
  
## <a name="AzureVM"></a>5.0 SQL Server 2014 RTM in macchine virtuali di Microsoft Azure  
  
### <a name="51-the-add-azure-replica-wizard-returns-an-error-when-configuring-an-availability-group-listener-in-windows-azure"></a>5.1 La procedura guidata Aggiungi replica Azure restituisce un errore durante la configurazione di un listener del gruppo di disponibilità in Windows Azure  
**Problema:** se un gruppo di disponibilità ha un listener, la procedura guidata Aggiungi replica Azure restituisce un errore durante il tentativo di configurare il listener in Windows Azure.  
  
Ciò è dovuto al fatto che i listener del gruppo di disponibilità richiedono l'assegnazione di un indirizzo IP in ogni subnet che ospita repliche del gruppo di disponibilità, inclusa la subnet di Azure.  
  
**Soluzione alternativa:**  
  
1.  Nella pagina Listener, assegnare un indirizzo IP statico libero al listener del gruppo di disponibilità nella subnet di Azure che ospiterà la replica del gruppo di disponibilità.  
  
    In questo modo, la procedura guidata sarà in grado di completare l'aggiunta della replica in Windows Azure.  
  
2.  Al termine della procedura guidata, sarà necessario completare la configurazione del listener in Windows Azure come descritto in [Configurazione del listener per i gruppi di disponibilità AlwaysOn in Windows Azure](http://msdn.microsoft.com/library/dn376546.aspx)  
  
![Icona freccia usata con il collegamento Torna all'inizio](../sql-server/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Torna all'inizio](#top)  
  
## <a name="SSAS"></a>6.0 Analysis Services  
  
### <a name="61-msolap5-must-be-downloaded-installed-and-registered-for-a-sharepoint-2010-new-farm-configured-with-sql-server-2014"></a>6.1 È necessario scaricare, installare e registrare MSOLAP.5 per una nuova farm SharePoint 2010 configurata con SQL Server 2014  
**Problema:**  
  
-   Per una farm SharePoint 2010 configurata con una distribuzione di SQL Server 2014 RTM, non è possibile connettere le cartelle di lavoro di PowerPivot ai modelli di dati perché il provider a cui si fa riferimento nella stringa di connessione non è installato.  
  
**Soluzione alternativa:**  
  
1.  Scaricare il provider MSOLAP.5 dal Feature Pack di [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] . Installare il provider nei server applicazioni in cui viene eseguito Excel Services. Per ulteriori informazioni, vedere la sezione "Microsoft Analysis Services OLE DB Provider per Microsoft SQL Server 2012 SP1" in [Microsoft SQL Server 2012 SP1 Feature Pack](http://www.microsoft.com/download/details.aspx?id=35580).  
  
2.  Registrare MSOLAP.5 come provider attendibile con Excel Services di SharePoint. Per ulteriori informazioni, vedere [Aggiungere MSOLAP.5 come provider di dati attendibile in Excel Services](http://technet.microsoft.com/library/hh758436.aspx).  
  
**Altre informazioni:**  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] include MSOLAP.6. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] e [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssGemini](../includes/ssgemini-md.md)] usano MSOLAP.5. Se MSOLAP.5 non è installato nel computer in cui viene eseguito Excel Services, non sarà possibile caricare i modelli di dati tramite Excel Services.  
  
### <a name="62-msolap5-must-be-downloaded-installed-and-registered-for-a-sharepoint-2013-new-farm-configured-with-sql-server-2014"></a>6.2 È necessario scaricare, installare e registrare MSOLAP.5 per una nuova farm SharePoint 2013 configurata con SQL Server 2014  
**Problema:**  
  
-   Per una farm SharePoint 2013 configurata con una distribuzione di [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] , non è possibile connettere le cartelle di lavoro di Excel che fanno riferimento al provider MSOLAP.5 ai modelli di dati tabulari perché il provider a cui si fa riferimento nella stringa di connessione non è installato.  
  
**Soluzione alternativa:**  
  
1.  Scaricare il provider MSOLAP.5 dal Feature Pack di [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] . Installare il provider nei server applicazioni in cui viene eseguito Excel Services. Per ulteriori informazioni, vedere la sezione "Microsoft Analysis Services OLE DB Provider per Microsoft SQL Server 2012 SP1" in [Microsoft SQL Server 2012 SP1 Feature Pack](http://www.microsoft.com/download/details.aspx?id=35580).  
  
2.  Registrare MSOLAP.5 come provider attendibile con Excel Services di SharePoint. Per ulteriori informazioni, vedere [Aggiungere MSOLAP.5 come provider di dati attendibile in Excel Services](http://technet.microsoft.com/library/hh758436.aspx).  
  
**Altre informazioni:**  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] include MSOLAP.6. ma le cartelle di lavoro di PowerPivot di SQL Server 2014 utilizzano MSOLAP.5. Se MSOLAP.5 non è installato nel computer in cui viene eseguito Excel Services, non sarà possibile caricare i modelli di dati tramite Excel Services.  
  
### <a name="63-corrupt-data-refresh-schedules"></a>6.3 Pianificazione dell'aggiornamento dati danneggiata  
**Problema:**  
  
-   Viene aggiornata una pianificazione dell'aggiornamento e la pianificazione viene danneggiata ed è inutilizzabile.  
  
**Soluzione alternativa:**  
  
1.  In Microsoft Excel cancellare le proprietà avanzate personalizzate. Vedere la sezione "Soluzione alternativa" dell'articolo della Knowledge Base [KB 2927748](http://support.microsoft.com/kb/2927748).  
  
**Altre informazioni:**  
  
-   Quando si aggiorna una pianificazione dell'aggiornamento dati per una cartella di lavoro, se la lunghezza serializzata della pianificazione dell'aggiornamento è inferiore alla pianificazione originale, le dimensioni del buffer non vengono aggiornate correttamente e le informazioni sulla nuova pianificazione vengono unite a quelle della pianificazione precedente con il conseguente danneggiamento della pianificazione.  
  
![Icona freccia usata con il collegamento Torna all'inizio](../sql-server/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Torna all'inizio](#top)  
  
## <a name="DQS"></a>7.0 Data Quality Services  
  
### <a name="71-no-cross-version-support-for-data-quality-services-in-master-data-services"></a>7.1 Nessun supporto tra versioni di Data Quality Services in Master Data Services  
**Problema:** non sono supportati gli scenari riportati di seguito.  
  
-   Master Data Services 2014 ospitato in un database del motore di database di SQL Server in SQL Server 2012 con Data Quality Services 2012 installato.  
  
-   Master Data Services 2012 ospitato in un database del motore di database di SQL Server in SQL Server 2014 con Data Quality Services 2014 installato.  
  
**Soluzione alternativa:** utilizzare la stessa versione di Master Data Services del database del motore di database e Data Quality Services.  
  
![Icona freccia usata con il collegamento Torna all'inizio](../sql-server/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Torna all'inizio](#top)  
  
## <a name="UA"></a>8.0 Problemi di Gestione spazio aggiornamenti  
  
### <a name="81--sql-server-2014-upgrade-advisor-reports-irrelevant-upgrade-issues-for-sql-server-reporting-services"></a>8.1 Preparazione aggiornamento di SQL Server 2014 segnala problemi di aggiornamento irrilevanti per SQL Server Reporting Services  
**Problema:** Gestione spazio aggiornamenti di SQL Server fornito con i supporti di SQL Server 2014 segnala erroneamente più errori durante l'analisi del server SQL Server Reporting Services.  
  
**Soluzione alternativa:** questo problema è stato risolto in Preparazione aggiornamento di SQL Server fornito nel [Feature Pack di SQL Server 2014 per SSUA](http://go.microsoft.com/fwlink/?LinkID=306709).  
  
### <a name="82--sql-server-2014-upgrade-advisor-reports-an-error-when-analyzing-sql-server-integration-services-server"></a>8.2 Preparazione aggiornamento di SQL Server 2014 segnala un errore durante l'analisi del server SQL Server Integration Services  
**Problema:** Gestione spazio aggiornamenti di SQL Server fornito con i supporti di SQL Server 2014 segnala un errore durante l'analisi del server SQL Server Integration Services.  L'errore visualizzato all'utente è il seguente:  
  
```  
The installed version of Integration Services does not support Upgrade Advisor.   
The assembly information is "Microsoft.SqlServer.ManagedDTS, Version=11.0.0.0,   
Culture=neutral, PublicKeyToken=89845dcd8080cc91  
```  
  
**Soluzione alternativa:** questo problema è stato risolto in Preparazione aggiornamento di SQL Server fornito nel [Feature Pack di SQL Server 2014 per SSUA](http://go.microsoft.com/fwlink/?LinkID=306709).  
  
![Icona freccia usata con il collegamento Torna all'inizio](../sql-server/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Torna all'inizio](#top)  
  
[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
