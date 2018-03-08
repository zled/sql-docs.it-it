---
title: Introduzione a SSMA per Oracle (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSMA for Oracle, Metadata Explorers
- SSMA for Oracle, Toolbars
ms.assetid: df79664c-972e-4bef-865a-ce609789fee7
caps.latest.revision: "9"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: On Demand
ms.openlocfilehash: 1765ceb5cb1f4100d60a0f429635f9fc80d14e82
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="getting-started-with-ssma-for-oracle-oracletosql"></a>Introduzione a SSMA per Oracle (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) per Oracle consente rapidamente gli schemi di database Oracle per convertire [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schemi, caricare degli schemi risultanti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e la migrazione dei dati da Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
In questo argomento introduce il processo di installazione e quindi consente di acquisire familiarità con l'interfaccia utente SSMA.  
  
## <a name="installing-ssma"></a>L'installazione di SSMA  
Per l'utilizzo di SSMA, è innanzitutto necessario installare il programma client SSMA in un computer che può accedere al database Oracle di origine sia l'istanza di destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È quindi necessario installare un pacchetto di estensione e almeno uno dei provider Oracle (OLE DB o [!INCLUDE[vstecado](../../includes/vstecado_md.md)]) nel computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Questi componenti supportano la migrazione dei dati e l'emulazione delle funzioni di sistema Oracle. Per istruzioni sull'installazione, vedere [l'installazione di SSMA per OracleToSQL Oracle &#40; &#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md).  
  
Per avviare SSMA, fare clic su **avviare**, scegliere **tutti i programmi**, scegliere  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per Oracle**, quindi fare clic su  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per Oracle**.  
  
## <a name="ssma-for-oracle-user-interface"></a>SSMA per l'interfaccia utente di Oracle  
Dopo l'installazione di SSMA, è possibile utilizzare SSMA per eseguire la migrazione di database Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È utile per acquisire familiarità con l'interfaccia utente SSMA prima di iniziare. Il diagramma seguente mostra l'interfaccia utente per SSMA, incluse le finestre di esplorazione dei metadati, metadati, le barre degli strumenti, riquadro di output e riquadro elenco errori:  
  
![SSMA per l'interfaccia utente di Oracle](../../ssma/oracle/media/ssma_oracle_ui.jpg "SSMA per l'interfaccia utente di Oracle")  
  
Per avviare una migrazione, è innanzitutto necessario creare un nuovo progetto. Quindi, connettersi a un database Oracle. Dopo la connessione ha esito positivo, gli schemi di Oracle verranno visualizzato in Visualizzatore metadati Oracle. È possibile quindi oggetti pulsante destro del mouse in Visualizzatore metadati Oracle per eseguire attività quali la creano di report che valutano le conversioni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È anche possibile eseguire queste attività tramite i menu e barre degli strumenti.  
  
È inoltre necessario connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Dopo la connessione ha esito positivo, una gerarchia di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database verranno visualizzati nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati. Dopo la conversione degli schemi Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schemi, selezionare tali schemi convertiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati e quindi sincronizzare gli schemi con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Dopo la sincronizzazione di convertire gli schemi con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile tornare a Visualizzatore metadati Oracle e la migrazione dei dati da schemi di Oracle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
Per ulteriori informazioni su queste attività e su come eseguire tali operazioni, vedere [la migrazione di database Oracle a SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md).  
  
Nelle sezioni seguenti vengono descritte le funzionalità dell'interfaccia utente SSMA.  
  
### <a name="metadata-explorers"></a>Finestre di esplorazione dei metadati  
SSMA contiene due finestre di esplorazione dei metadati per individuare ed eseguire azioni in Oracle e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
#### <a name="oracle-metadata-explorer"></a>Visualizzatore metadati Oracle  
Visualizzatore metadati Oracle Mostra informazioni sugli schemi di Oracle. Tramite Visualizzatore metadati Oracle, è possibile eseguire le attività seguenti:  
  
-   Esplorare gli oggetti in ogni schema.  
  
-   Selezionare gli oggetti per la conversione e quindi convertire gli oggetti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi. Per ulteriori informazioni, vedere [OracleToSQL la conversione di schemi Oracle &#40; &#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md).  
  
-   Selezionare le tabelle per la migrazione dei dati e quindi migrare i dati da tali tabelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per ulteriori informazioni, vedere [la migrazione di dati Oracle in SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md).  
  
#### <a name="sql-server-metadata-explorer"></a>Visualizzatore metadati SQL Server  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Visualizzatore metadati Mostra le informazioni su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Quando ci si connette a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], recupera i metadati relativi a tale istanza e la archivia nel file di progetto SSMA.  
  
È possibile utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati per selezionare gli oggetti di database Oracle convertiti e quindi sincronizzare gli oggetti con l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Per ulteriori informazioni, vedere [il caricamento di convertire gli oggetti di Database in SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
### <a name="metadata"></a>Metadati  
A destra di ogni Visualizzatore metadati sono schede che descrivono l'oggetto selezionato. Ad esempio, se si seleziona una tabella in Visualizzatore metadati Oracle, verranno visualizzate sei schede: **tabella**, **SQL**, **del mapping dei tipi, Report**, **proprietà**, e **dati**. Il **Report** scheda contiene informazioni solo dopo aver creato un report che contiene l'oggetto selezionato. Se si seleziona una tabella in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, verranno visualizzate tre schede: **tabella**, **SQL**, e **dati**.  
  
La maggior parte delle impostazioni dei metadati sono di sola lettura. Tuttavia, è possibile modificare i metadati seguenti:  
  
-   In Visualizzatore metadati Oracle, è possibile alter procedure e i mapping dei tipi. Per convertire le procedure modificate e i mapping dei tipi, è possibile apportare modifiche prima di convertire gli schemi.  
  
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, è possibile modificare il [!INCLUDE[tsql](../../includes/tsql_md.md)] per le stored procedure. Per visualizzare le modifiche in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], apportare queste modifiche prima di caricare gli schemi in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Le modifiche apportate in un Visualizzatore metadati vengono riflesse nei metadati del progetto, non nei database di origine o di destinazione.  
  
### <a name="toolbars"></a>Barre degli strumenti  
SSMA è due barre degli strumenti: una barra degli strumenti del progetto e una barra degli strumenti di migrazione.  
  
#### <a name="the-project-toolbar"></a>La barra degli strumenti del progetto  
La barra degli strumenti del progetto contiene pulsanti per l'utilizzo di progetti, la connessione a Oracle e connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Questi pulsanti sono simili a quelli nel **File** menu.  
  
#### <a name="migration-toolbar"></a>Barra degli strumenti di migrazione  
La tabella seguente illustra la migrazione di comandi della barra degli strumenti:  
  
|Pulsante|Funzione|  
|------|--------|  
|**Creazione di Report**|Converte gli oggetti selezionati Oracle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi, quindi viene creato un report che mostra come esito positivo della conversione.<br /><br />Questo comando è disabilitato a meno che non vengono selezionati gli oggetti in Visualizzatore metadati Oracle.|  
|**Converti Schema**|Converte gli oggetti selezionati Oracle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti.<br /><br />Questo comando è disabilitato a meno che non vengono selezionati gli oggetti in Visualizzatore metadati Oracle.|  
|**La migrazione dei dati**|Esegue la migrazione di dati dal database di Oracle per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Prima di eseguire questo comando, è necessario convertire gli schemi di Oracle da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schemi, quindi caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br />Questo comando è disabilitato a meno che non vengono selezionati gli oggetti in Visualizzatore metadati Oracle.|  
|**Arresta**|Arresta il processo corrente.|  
  
### <a name="menus"></a>Menu  
Nella tabella seguente viene illustrato i menu SSMA.  
  
|Menu|Description|  
|----|-----------|  
|**File**|Contiene i comandi per l'utilizzo di progetti, la connessione a Oracle e connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|**Modifica**|Contiene i comandi per la ricerca e l'utilizzo del testo nelle pagine di dettagli, ad esempio la copia [!INCLUDE[tsql](../../includes/tsql_md.md)] dal riquadro dei dettagli SQL. Contiene inoltre il **gestire segnalibri** opzione, in cui sarà in grado di visualizzare un elenco di segnalibri. È possibile utilizzare i pulsanti sul lato destro della finestra di dialogo per gestire i segnalibri.|  
|**Visualizza**|Contiene il **sincronizzare i metadati Explorers** comando. Che consente di sincronizzare gli oggetti tra Visualizzatore metadati Oracle e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati. Contiene inoltre i comandi per visualizzare e nascondere il **Output** e **elenco errori** riquadri e un'opzione **layout** per gestire il layout.|  
|**Strumenti**|Contiene i comandi per creare report ed eseguire la migrazione di oggetti e dati. Fornisce inoltre l'accesso per il **impostazioni globali** e **impostazioni progetto** finestre di dialogo.|  
|**Tester**|Contiene i comandi per la creazione e utilizzo di test case, repository e il sistema di gestione dei backup.|  
|**?**|Fornisce l'accesso di SSMA Guida in linea e di ottenere il **su** la finestra di dialogo.|  
  
### <a name="output-pane-and-error-list-pane"></a>Riquadro di output e il riquadro elenco errori  
Il **vista** menu sono disponibili comandi per attivare o disattivare la visibilità del riquadro di Output e il riquadro elenco errori:  
  
-   Il riquadro di output mostra i messaggi di stato da SSMA durante la conversione degli oggetti di sincronizzazione dell'oggetto e migrazione dei dati.  
  
-   Nel riquadro elenco errori Mostra messaggi di errore, avviso e informativi in un elenco ordinabile.  
  
## <a name="see-also"></a>Vedere anche  
[La migrazione dei dati di Oracle in SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md)  
[Riferimento all'interfaccia utente &#40; OracleToSQL &#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  
