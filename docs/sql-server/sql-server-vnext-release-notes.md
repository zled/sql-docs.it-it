---
title: "Note sulla versione di SQL Server vNext | Microsoft Docs"
ms.custom: ""
ms.date: "03/12/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
caps.latest.revision: 41
author: "craigg-msft"
ms.author: "craigg"
manager: "jhubbard"
caps.handback.revision: 39
---
# Note sulla versione di SQL Server vNext
Questo argomento descrive i limiti e i problemi relativi a [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

- Per informazioni sulle novità introdotte in questa versione, vedere [Novità di SQL Server vNext](../sql-server/what-s-new-in-sql-server-vnext.md).
- Le [note sulla versione di SQL Server in Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes) sono pubblicate nella nuova e sempre aggiornata piattaforma della documentazione.
- Le [note sulla versione di SQL Server Reporting Services](../reporting-services/note-sulla-versione-di-reporting-services.md) sono pubblicate all'interno della sezione di Reporting Services.

 **Per provarlo:**    
   -   [![Download da Evaluation Center](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  Scaricare [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] da **[Evaluation Center](http://go.microsoft.com/fwlink/?LinkID=829477)**


## <a name="sql-server-vnext-ctp-13-february--2017"></a>SQL Server vNext CTP 1.3 (febbraio 2017)
### <a name="supported-installation-scenarios-ctp-13"></a>Scenari di installazione supportati (CTP 1.3)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è disponibile solo come versione di prova.  Le distribuzioni di produzione non sono supportate. Si consiglia di installare e provare [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] in una macchina virtuale.

### <a name="documentation-ctp-13"></a>Documentazione (CTP 1.3)
- **Problema e impatto sul cliente:** la documentazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è limitata e il contenuto è incluso nel set di documentazione di [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)].  Il contenuto di articoli specifici di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è indicato con **Si applica a:**. 
- **Problema e impatto sul cliente:** per [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] non è disponibile contenuto offline.

### <a name="sql-server-integration-services-ssis-ctp-13"></a>SQL Server Integration Services (SSIS) (CTP 1.3)
#### <a name="cdc-components-not-supported-in-this-ctp-release"></a>Componenti CDC non supportati in questa versione CTP
-   **Problema e impatto sul cliente:** l'attività di controllo, l'origine e la barra di divisione CDC non sono supportate in questa versione CTP.
-   **Soluzione alternativa:** non esistono soluzioni alternative.


![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-12-january--2017"></a>SQL Server vNext CTP 1.2 (gennaio 2017)
### <a name="supported-installation-scenarios-ctp-12"></a>Scenari di installazione supportati (CTP 1.2)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è disponibile solo come versione di prova.  Le distribuzioni di produzione non sono supportate. Si consiglia di installare e provare [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] in una macchina virtuale.

### <a name="sql-server-database-engine-ctp-12"></a>Motore di database di SQL Server (CTP 1.2)
- **Problema e impatto sul cliente:** in alcuni casi, il servizio MSSQLSERVER rimane bloccato nello stato "Iniziale".
- **Soluzione alternativa:** per risolvere questo problema:
  -  Creare una dipendenza tra il servizio `mssqlserver` e il servizio `keyiso`. A tale scopo, è possibile eseguire questo comando da un prompt dei comandi con privilegi elevati: `sc config mssqlserver depend= keyiso`
  - Riavviare il computer.

### <a name="documentation-ctp-12"></a>Documentazione (CTP 1.2)
- **Problema e impatto sul cliente:** la documentazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è limitata e il contenuto è incluso nel set di documentazione di [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)].  Il contenuto di articoli specifici di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è indicato con **Si applica a:**. 
- **Problema e impatto sul cliente:** per [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] non è disponibile contenuto offline.
 
### <a name="sql-server-integration-services-ssis-ctp-12"></a>SQL Server Integration Services (SSIS) (CTP 1.2)
#### <a name="deleting-the-ssis-catalog-may-fail-when-ssis-scale-out-is-installed"></a>L'eliminazione del catalogo SSIS può avere esito negativo se è installata la funzionalità di scalabilità orizzontale di SSIS
**Problema e impatto sul cliente:** quando la funzionalità di scalabilità orizzontale di SSIS è installata in un computer, l'eliminazione del database di catalogo SSISDB può avere esito negativo e restituire l'errore seguente: "Non è stato possibile eliminare l'account di accesso *'accountaccesso'* perché l'utente è connesso".
   
**Soluzione alternativa**:
-   In un computer con il master di scalabilità orizzontale, eseguire il comando "services.msc" per aprire la finestra Servizi. Arrestare il servizio Cluster Master di SQL Server Integration Services.
-   Nei computer con il ruolo di lavoro di scalabilità orizzontale, che si connettono al master, eseguire il comando "services.msc" per aprire la finestra Servizi. Arrestare il servizio Cluster Worker di SQL Server Integration Services.

È ora possibile eliminare il database di catalogo SSISDB.

### <a name="sql-server-master-data-services-ctp-12"></a>SQL Server Master Data Services (CTP 1.2)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>La transazione può non funzionare quando il tipo di log delle transazioni dell'entità viene impostato su attributo
**Problema e impatto sul cliente:** quando il tipo di log delle transazioni dell'entità è impostato su **Attributo** in [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] (il valore predefinito è **Membro**), eseguire gli scenari seguenti:

* Le transazioni relative alle modifiche dell'entità non vengono visualizzate nel sito Web.
* Non è possibile aprire la pagina **Transazioni** sul sito Web e invertire una transazione.
* Non è possibile aggiornare un'entità con un'annotazione della transazione nel sito Web.

**Soluzione alternativa:** non esistono soluzioni alternative.

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>La versione di copia può non funzionare se **Copy only committed version** (Copia solo la versione di cui è stato eseguito il commit) è impostata su false
-  **Problema e impatto sul cliente:** se **Copy only committed version** (Copia solo la versione di cui è stato eseguito il commit) è impostata su **No** (il valore predefinito è **Yes** (Sì)), l'operazione di copia della versione può avere esito negativo. Non viene restituito alcune messaggio di errore.
-  **Soluzione alternativa:** non esistono soluzioni alternative.

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-11-december--2016"></a>SQL Server vNext CTP 1.1 (dicembre 2016)
### <a name="supported-installation-scenarios-ctp-11"></a>Scenari di installazione supportati (CTP 1.1)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è disponibile solo come versione di prova.  Le distribuzioni di produzione non sono supportate. Si consiglia di installare e provare [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] in una macchina virtuale.

In particolare, anche se gli scenari seguenti possono adattarsi alle proprie esigenze, non sono stati testati attentamente e **non** sono supportati in [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]:
- Disinstallazione della versione CTP 1.1.
- Installazione side-by-side con altre versioni di SQL Server.
- Aggiornamento da versioni precedenti di SQL Server.
- I componenti del feature pack di SQL Server non sono disponibili come parte dell'installazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

### <a name="documentation-ctp-11"></a>Documentazione (CTP 1.1)
- **Problema e impatto sul cliente:** la documentazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è limitata e il contenuto è incluso nel set di documentazione di [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)].  Il contenuto di articoli specifici di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è indicato con **Si applica a:**. 
- **Problema e impatto sul cliente:** per [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] non è disponibile contenuto offline.

### <a name="sql-server-master-data-services-ctp-11"></a>SQL Server Master Data Services (CTP 1.1)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>La transazione può non funzionare quando il tipo di log delle transazioni dell'entità viene impostato su attributo
**Problema e impatto sul cliente:** quando il tipo di log delle transazioni dell'entità è impostato su **Attributo** in [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] (il valore predefinito è **Membro**), eseguire gli scenari seguenti:

* Le transazioni relative alle modifiche dell'entità non vengono visualizzate nel sito Web.
* Non è possibile aprire la pagina **Transazioni** sul sito Web e invertire una transazione.
* Non è possibile aggiornare un'entità con un'annotazione della transazione nel sito Web.

**Soluzione alternativa:** non esistono soluzioni alternative.

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>La versione di copia può non funzionare se **Copy only committed version** (Copia solo la versione di cui è stato eseguito il commit) è impostata su false
-  **Problema e impatto sul cliente:** se **Copy only committed version** (Copia solo la versione di cui è stato eseguito il commit) è impostata su **No** (il valore predefinito è **Yes** (Sì)), l'operazione di copia della versione può avere esito negativo. Non viene restituito alcune messaggio di errore.
-  **Soluzione alternativa:** non esistono soluzioni alternative.

### <a name="sql-server-integration-services-ssis-ctp-11"></a>SQL Server Integration Services (SSIS) (CTP 1.1)
#### <a name="deleting-the-ssis-catalog-may-fail-when-ssis-scale-out-is-installed"></a>L'eliminazione del catalogo SSIS può avere esito negativo se è installata la funzionalità di scalabilità orizzontale di SSIS
**Problema e impatto sul cliente:** quando la funzionalità di scalabilità orizzontale di SSIS è installata in un computer, l'eliminazione del database di catalogo SSISDB può avere esito negativo e restituire l'errore seguente: "Non è stato possibile eliminare l'account di accesso *'accountaccesso'* perché l'utente è connesso".
   
**Soluzione alternativa**:
-   In un computer con il master di scalabilità orizzontale, eseguire il comando "services.msc" per aprire la finestra Servizi. Arrestare il servizio Cluster Master di SQL Server Integration Services.
-   Nei computer con il ruolo di lavoro di scalabilità orizzontale, che si connettono al master, eseguire il comando "services.msc" per aprire la finestra Servizi. Arrestare il servizio Cluster Worker di SQL Server Integration Services.

È ora possibile eliminare il database di catalogo SSISDB.

#### <a name="odbc-components-are-not-supported-in-this-ctp-release"></a>I componenti ODBC non sono supportati in questa versione CTP
**Problema e impatto sul cliente:** l'origine, la destinazione e la gestione connessione ODBC non sono supportate in questa versione CTP.

**Soluzione alternativa:** non esistono soluzioni alternative.

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-10-november-2016"></a>SQL Server vNext CTP 1.0 (novembre 2016)
### <a name="supported-installation-scenarios-ctp10"></a>Scenari di installazione supportati (CTP&1;.0)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è disponibile solo come versione di prova.  Le distribuzioni di produzione non sono supportate. Si consiglia di installare e provare [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] in una macchina virtuale.

In particolare, anche se gli scenari seguenti possono adattarsi alle proprie esigenze, non sono stati testati attentamente e **non** sono supportati in [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]:
- Disinstallazione della versione CTP 1.0.
- Installazione side-by-side con altre versioni di SQL Server.
- Aggiornamento da versioni precedenti di SQL Server.
- I componenti del feature pack di SQL Server non sono disponibili come parte dell'installazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

### <a name="documentation-ctp-10"></a>Documentazione (CTP 1.0)
- **Problema e impatto sul cliente:** la documentazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è limitata e il contenuto è incluso nel set di documentazione di [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)].  Il contenuto in articoli specifici di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è indicato con **Si applica a:**. 
- **Problema e impatto sul cliente:** per [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] non è disponibile contenuto offline.

### <a name="sql-server-database-engine-ctp-10"></a>Motore di database di SQL Server (CTP 1.0)
-  **Problema e impatto sul cliente:** la funzionalità `STRING_AGG` in CTP1 restituisce il tipo LOB (ad esempio, `NVARCHAR(MAX)`). In una successiva versione di CTP, questo comportamento potrebbe cambiare e `STRING_AGG` potrebbe restituire `NVARCHAR(4000)` se i valori di input non sono tipi LOB. È possibile che venga generato un errore di overflow se i risultati concatenati non rientrano in `NVARCHAR(4000)`.

-  **Problema e impatto sul cliente:** evitare gli utilizzi di parole chiave non riservate, ad esempio `WITHIN`, come alias delle espressioni `STRING_AGG`. Ad esempio, `SELECT Company.Name, STRING_AGG(Product.Name, ',') AS WITHIN FROM TableA;`. In una successiva versione di CTP, il token `WITHIN` dopo la chiamata `STRING_AGG` può essere usato come parte della funzione `STRING_AGG`.

-  **Soluzione alternativa:** evitare di usare alias `WITHIN` o aggiungere `AS WITHIN` come specifica di un alias per evitare conflitti con modifiche future che possono essere aggiunte alla funzione `STRING_AGG`.


### <a name="sql-server-integration-services-ctp-10"></a>SQL Server Integration Services (CTP 1.0)
#### <a name="stop-operation-in-ssis-catalog-may-fail"></a>L'operazione di arresto nel catalogo SSIS può avere esito negativo
**Problema e impatto sul cliente:** l'arresto di un'operazione in [!INCLUDE[ssIS_md](../includes/ssis-md.md)] mediante [!INCLUDE[ssManStudio_md](../includes/ssmanstudio-md.md)] o la stored procedure catalog.stop_operation può avere esito negativo e restituire l'errore seguente: "Errore di .NET Framework durante l'esecuzione dell'aggregazione o routine definita dall'utente 'stop_operation_internal'".

-  **Soluzione alternativa:** aprire Gestione attività Windows. Nella scheda **Processi** trovare il processo denominato **ISServerExec** e fare clic su **Termina attività** per terminare il processo.

#### <a name="create-dump-of-ssis-pacakge-execution-may-fail"></a>La creazione di dump dell'esecuzione del pacchetto SSIS può avere esito negativo
**Problema e impatto sul cliente:** la creazione di un dump per l'esecuzione di un pacchetto usando la stored procedure catalog.create_execution_dump può avere esito negativo e restituire l'errore seguente: "Errore di .NET Framework durante l'esecuzione dell'aggregazione o routine definita dall'utente 'create_execution_dump_internal'".

-  **Soluzione alternativa:** aprire Gestione attività Windows. Nella scheda **Processi** trovare il processo denominato **ISServerExec**, fare clic con il pulsante destro del mouse sul processo e quindi fare clic su **Crea file di dettagli**.

#### <a name="get-perf-counter-of-ssis-package-execution-may-fail"></a>I contatori delle prestazione per l'esecuzione del pacchetto SSIS possono avere esito negativo
**Problema e impatto sul cliente:** l'esecuzione di query sui contatori delle prestazioni di [!INCLUDE[ssIS_md](../includes/ssis-md.md)] mediante la funzione con valori di tabella catalog.dm_execution_performance_counters può avere esito negativo e restituire l'errore seguente: "Errore di .NET Framework durante l'esecuzione dell'aggregazione o routine definita dall'utente 'get_execution_perf_counters'".

-  **Soluzione alternativa**: usare Monitoraggio prestazioni di Windows per monitorare direttamente i valori dei contatori delle prestazioni. Non sono disponibili soluzioni alternative per i contatori delle prestazioni per l'esecuzione di un pacchetto specifico.

#### <a name="deleting-catalog-may-fail-when-ssis-scale-out-master-is-installed"></a>L'eliminazione del catalogo può avere esito negativo se è installato il master di scalabilità orizzontale di SSIS
**Problema e impatto sul cliente:** quando la funzionalità di scalabilità orizzontale di [!INCLUDE[ssIS_md](../includes/ssis-md.md)] viene installata in un computer, l'eliminazione del catalogo **SSISDB** può avere esito negativo e restituire l'errore: "Non è stato possibile eliminare l'account di accesso '...' perché l'utente è connesso". 

**Soluzione alternativa**: 
* In un computer con il master di scalabilità orizzontale eseguire il comando "services.msc" per aprire la finestra **Servizi** e interrompere il servizio **Cluster Master di SQL Server Integration Services**. 

* Nei computer con il ruolo di lavoro di scalabilità orizzontale, che si connettono al master, eseguire il comando "services.msc" per aprire la finestra **Servizi**. Arrestare il servizio **Cluster Worker di SQL Server Integration Services**. 

A questo punto, si è in grado di eliminare il catalogo **SSISDB**.

#### <a name="odbc-connector-in-ssis-is-not-supported"></a>Il connettore ODBC non è supportato in SSIS
-  **Problema e impatto sul cliente:** il connettore ODCB in [!INCLUDE[ssIS_md](../includes/ssis-md.md)] non è supportato.
-  **Soluzione alternativa:** non esistono soluzioni alternative.

### <a name="sql-server-reporting-services-ctp-10"></a>SQL Server Reporting Services (CTP 1.0)

SQL Server Reporting Services non ha rilasciaro nuove funzionalità per [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

### <a name="sql-server-master-data-services-ctp-10"></a>SQL Server Master Data Services (CTP 1.0)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>La transazione può non funzionare quando il tipo di log delle transazioni dell'entità viene impostato su attributo
**Problema e impatto sul cliente:** quando il tipo di log delle transazioni dell'entità è impostato su **Attributo** in [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] (il valore predefinito è **Membro**), eseguire gli scenari seguenti:

* Le transazioni relative alle modifiche dell'entità non vengono visualizzate nel sito Web.
* Non è possibile aprire la pagina **Transazioni** sul sito Web e invertire una transazione.
* Non è possibile aggiornare un'entità con un'annotazione della transazione nel sito Web.

**Soluzione alternativa:** non esistono soluzioni alternative.

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>La versione di copia può non funzionare se **Copy only committed version** (Copia solo la versione di cui è stato eseguito il commit) è impostata su false
**Problema e impatto sul cliente:** se **Copy only committed version** (Copia solo la versione di cui è stato eseguito il commit) è impostata su **No** (il valore predefinito è **Yes** (Sì)), l'operazione di copia della versione può avere esito negativo. Non viene restituito alcune messaggio di errore.

**Soluzione alternativa:** non esistono soluzioni alternative.
 
### <a name="sql-server-management-studio-ssms-ctp-10"></a>SQL Server Management Studio (SSMS) (CTP 1.0)
SQL Server Management Studio è un download separato.  Per le informazioni più aggiornate, vedere [Note sulla versione di SQL Server Management Studio](https://msdn.microsoft.com/library/mt238486.aspx).

##  <a name="infotipimageshiproominfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Coinvolgimento del team di progettazione di SQL Server 
- [Stack Overflow (tag sql-server) - ask technical questions](http://stackoverflow.com/questions/tagged/sql-server) (Domande tecniche su Stack Overflow)
- [MSDN Forums - ask technical questions](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver) (Domande tecniche sui forum MSDN)
- [Microsoft Connect - report bugs and request features](https://connect.microsoft.com/SQLServer/Feedback) (Segnalazione di bug e richiesta di funzionalità di Microsoft Connect)
- [Reddit - general discussion about R](https://www.reddit.com/r/SQLServer/) (Discussione generale su R in Reddit)


![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
