---
title: Introduzione a SSMA per Sybase (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: c4098516-f0fc-4690-97bb-3766dfd43156
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6a25db175cd6d67b71a0fc72bde969898e4bdadd
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="getting-started-with-ssma-for-sybase-sybasetosql"></a>Introduzione a SSMA per Sybase (SybaseToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) per Sybase consente rapidamente gli schemi di database di Sybase Adaptive Server Enterprise (ASE) per convertire [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o schemi di SQL Azure, caricare degli schemi risultanti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, e la migrazione dei dati da Sybase ASE a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
In questo argomento introduce il processo di installazione e quindi consente di acquisire familiarità con l'interfaccia utente SSMA.  
  
## <a name="installing-and-licensing-ssma"></a>L'installazione e la gestione delle licenze di SSMA  
Per l'utilizzo di SSMA, è innanzitutto necessario installare il programma client SSMA in un computer che può accedere sia l'istanza di origine di Sybase ASE e l'istanza di destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Per usare la migrazione di dati lato Server, è necessario installare il pacchetto di estensione e almeno uno dei provider di Sybase (OLE DB o ADO.NET) nel computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Questi componenti supportano la migrazione dei dati e l'emulazione di Sybase ASE delle funzioni di sistema. Per istruzioni sull'installazione, vedere [l'installazione di SSMA per Sybase &#40; SybaseToSQL &#41; ](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md).  
  
Per avviare SSMA, fare clic su **avviare**, scegliere **tutti i programmi**, scegliere  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per Sybase**, quindi selezionare  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per Sybase**. La prima volta che si avvia SSMA, verrà visualizzata una finestra di dialogo Gestione licenze. È necessario ottenere una licenza SSMA utilizzando un Windows Live ID prima di poter usare SSMA. Istruzioni di gestione delle licenze sono incluse con le istruzioni di installazione nel [l'installazione di SSMA per Sybase Client &#40; SybaseToSQL &#41; ](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md) argomento.  
  
## <a name="ssma-for-sybase-user-interface"></a>SSMA per l'interfaccia utente di Sybase  
Dopo aver installato e concesso in licenza SSMA, è possibile utilizzare SSMA per eseguire la migrazione dei database Sybase ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. È utile per acquisire familiarità con l'interfaccia utente SSMA prima di iniziare. Il diagramma seguente mostra l'interfaccia utente per SSMA, incluse le finestre di esplorazione dei metadati, metadati, le barre degli strumenti, riquadro di output e riquadro elenco errori:  
  
![SSMA per l'interfaccia utente di Sybase](../../ssma/sybase/media/ssmaforsybaseuserinterface.jpg "SSMA per l'interfaccia utente di Sybase")  
  
Per avviare una migrazione, è innanzitutto necessario creare un nuovo progetto. Quindi, connettersi Sybase ASE. Dopo la connessione ha esito positivo, verrà visualizzata una gerarchia di database di Sybase ASE in Visualizzatore metadati Sybase. È possibile quindi oggetti pulsante destro del mouse in Visualizzatore metadati Sybase per eseguire le attività, ad esempio creano report che valutano le conversioni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. È anche possibile eseguire queste attività tramite i menu e barre degli strumenti.  
  
È inoltre necessario connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Dopo la connessione ha esito positivo, una gerarchia di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database di SQL Azure verranno visualizzata nei [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure. Dopo la conversione degli schemi Sybase ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o schemi di SQL Azure, selezionare tali schemi convertiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure, quindi caricare degli schemi in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
Dopo aver caricato gli schemi convertiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è possibile tornare a Visualizzatore metadati Sybase e la migrazione dei dati dal database Sybase ASE in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database di SQL Azure.  
  
Per ulteriori informazioni su queste attività e su come eseguire tali operazioni, vedere [migrazione Sybase ASE database a SQL Server - database SQL di Azure &#40; SybaseToSQL &#41; ](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md).  
  
Nelle sezioni seguenti vengono descritte le funzionalità dell'interfaccia utente SSMA.  
  
### <a name="metadata-explorers"></a>Finestre di esplorazione dei metadati  
SSMA contiene due finestre di esplorazione dei metadati per individuare ed eseguire azioni su Sybase ASE e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database di SQL Azure.  
  
#### <a name="sybase-metadata-explorer"></a>Visualizzatore metadati di Sybase  
Visualizzatore metadati Sybase Mostra le informazioni sui database nell'istanza di origine di Sybase ASE.  
  
Tramite Visualizzatore metadati Sybase, è possibile eseguire le attività seguenti:  
  
-   Selezionare le tabelle in ogni database.  
  
-   Selezionare gli oggetti per la conversione e quindi convertire gli oggetti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o la sintassi SQL Azure. Per ulteriori informazioni, vedere [convertire gli oggetti di Database di Sybase ASE &#40; SybaseToSQL &#41; ](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
-   Selezionare gli oggetti per la migrazione dei dati e quindi migrare i dati da tali oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Per ulteriori informazioni, vedere [migrazione Sybase ASE dati in SQL Server - database SQL di Azure &#40; SybaseToSQL &#41; ](../../ssma/sybase/migrating-sybase-ase-data-into-sql-server-azure-sql-db-sybasetosql.md).  
  
#### <a name="sql-server-or-sql-azure-metadata-explorer"></a>SQL Server o SQL Azure metadati Explorer  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]o Visualizzatore metadati di SQL Azure Mostra le informazioni su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Quando ci si connette a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, SSMA recupera i metadati relativi a tale istanza e viene memorizzato nel file di progetto.  
  
È possibile utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure metadati Explorer per selezionare gli oggetti di database Sybase ASE convertiti e quindi caricare (sincronizzazione) gli oggetti nell'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
Per ulteriori informazioni, vedere [il caricamento di convertire gli oggetti di Database in SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/loading-converted-database-objects-into-sql-server-sybasetosql.md).  
  
### <a name="metadata"></a>Metadati  
A destra di ogni Visualizzatore metadati sono schede che descrivono l'oggetto selezionato. Ad esempio, se si seleziona una tabella in Visualizzatore metadati Sybase, verranno visualizzate sei schede: **tabella**, **SQL**, **del mapping dei tipi**, **dati, le proprietà** e **Report**. Il **Report** scheda contiene informazioni solo dopo aver creato un report contenente l'oggetto selezionato. Se si seleziona una tabella in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure, verranno visualizzate tre schede: **tabella**, **SQL**, e **dati**.  
  
La maggior parte delle impostazioni dei metadati sono di sola lettura. Tuttavia, è possibile modificare i metadati seguenti:  
  
-   In Visualizzatore metadati Sybase, è possibile alter procedure e i mapping dei tipi. È necessario apportare queste modifiche prima di convertire gli schemi.  
  
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oppure Visualizzatore metadati di SQL Azure, è possibile modificare il [!INCLUDE[tsql](../../includes/tsql_md.md)] per le stored procedure. È necessario apportare queste modifiche prima di caricare gli schemi in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Le modifiche apportate in un Visualizzatore metadati vengono riflesse nei metadati del progetto, non nei database di origine o di destinazione.  
  
### <a name="toolbars"></a>Barre degli strumenti  
SSMA è due barre degli strumenti: una barra degli strumenti del progetto e una barra degli strumenti di migrazione.  
  
#### <a name="the-project-toolbar"></a>La barra degli strumenti del progetto  
La barra degli strumenti del progetto contiene pulsanti per l'utilizzo di progetti, la connessione a Sybase ASE e connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Questi pulsanti sono simili a quelli nel **File** menu.  
  
#### <a name="migration-toolbar"></a>Barra degli strumenti di migrazione  
La barra degli strumenti di migrazione include i comandi seguenti:  
  
|Pulsante|Funzione|  
|----------|------------|  
|**Creazione di Report**|Converte gli oggetti selezionati Sybase ASE in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi, quindi viene creato un report che mostra come esito positivo della conversione.<br /><br />Questo comando è disponibile solo quando gli oggetti selezionati in Visualizzatore metadati Sybase.|  
|**Converti Schema**|Converte gli oggetti selezionati Sybase ASE in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli oggetti di SQL Azure.<br /><br />Questo comando è disponibile solo quando gli oggetti selezionati in Visualizzatore metadati Sybase.|  
|**La migrazione dei dati**|Esegue la migrazione di dati dal database Sybase ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Prima di eseguire questo comando, è necessario convertire gli schemi di Sybase [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o schemi di SQL Azure, quindi caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.<br /><br />Questo comando è disponibile solo quando gli oggetti selezionati in Visualizzatore metadati Sybase.|  
|**Arresta**|Arresta il processo corrente, ad esempio la conversione di oggetti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o la sintassi SQL Azure.|  
  
### <a name="menus"></a>Menu  
SSMA contiene i menu seguenti.  
  
|Menu|Description|  
|--------|---------------|  
|**File**|Contiene i comandi per l'utilizzo di progetti, la connessione a Sybase ASE e connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.|  
|**Modifica**|Contiene i comandi per la ricerca e l'utilizzo del testo nelle pagine di dettagli, ad esempio la copia [!INCLUDE[tsql](../../includes/tsql_md.md)] dal riquadro dei dettagli SQL. Contiene inoltre il **gestire segnalibri** opzione, in cui sarà in grado di visualizzare un elenco di segnalibri. È possibile utilizzare i pulsanti sul lato destro della finestra di dialogo per gestire i segnalibri.|  
|**Visualizza**|Contiene il **sincronizzare i metadati Explorers** comando. Ciò consente di sincronizzare gli oggetti tra Visualizzatore metadati Sybase e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure. Contiene inoltre i comandi per visualizzare e nascondere il **Output** e **elenco errori** riquadri e un'opzione **layout** per gestire il layout.|  
|**Strumenti**|Comandi per creare report, esportare i dati e la migrazione di oggetti e dati. Fornisce inoltre l'accesso per il **impostazioni globali** e **impostazioni progetto** finestre di dialogo.|  
|**Tester**|Contiene i comandi per creare test case, visualizzare i risultati di test e i comandi per la gestione di backup di database.|  
|**?**|Fornisce l'accesso di SSMA Guida in linea e di ottenere il **su** la finestra di dialogo.|  
  
### <a name="output-pane-and-error-list-pane"></a>Riquadro di output e il riquadro elenco errori  
Il **vista** menu sono disponibili comandi per attivare o disattivare la visibilità del riquadro di Output e il riquadro elenco errori:  
  
-   Il riquadro di Output Mostra i messaggi di stato da SSMA durante la conversione degli oggetti di sincronizzazione dell'oggetto e migrazione dei dati.  
  
-   Nel riquadro elenco errori Mostra messaggi di errore, avviso e informativi in un elenco che è possibile ordinare.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Sybase ASE a SQL Server: database SQL di Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Riferimento all'interfaccia utente &#40; SybaseToSQL &#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
  

