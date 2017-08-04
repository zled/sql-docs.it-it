---
title: Introduzione a SSMA per DB2 (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 48ca32fc-1830-4d1f-add7-480ba5ad02e8
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8b84d83b0f72d1a8130792532b191639f521225e
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="getting-started-with-ssma-for-db2-db2tosql"></a>Introduzione a SSMA per DB2 (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) per DB2 consente rapidamente gli schemi di database DB2 per convertire [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schemi, caricare degli schemi risultanti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e la migrazione dei dati da DB2 a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
In questo argomento introduce il processo di installazione e quindi consente di acquisire familiarità con l'interfaccia utente SSMA.  
  
## <a name="installing-ssma"></a>L'installazione di SSMA  
Per l'utilizzo di SSMA, è innanzitutto necessario installare il programma client SSMA in un computer che può accedere al database di origine DB2 sia l'istanza di destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. I provider OLE DB di DB2 nel computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Questi componenti supportano la migrazione dei dati e l'emulazione delle funzioni di sistema DB2. Per istruzioni sull'installazione, vedere [l'installazione di SSMA per DB2ToSQL DB2 &#40; &#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md).  
  
Per avviare SSMA, fare clic su **avviare**, scegliere **tutti i programmi**, scegliere  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per DB2**, quindi fare clic su  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per DB2**.  
  
## <a name="ssma-for-db2-user-interface"></a>SSMA per l'interfaccia utente di DB2  
Dopo l'installazione di SSMA, è possibile utilizzare SSMA per la migrazione dei database di DB2 per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È utile per acquisire familiarità con l'interfaccia utente SSMA prima di iniziare. Il diagramma seguente mostra l'interfaccia utente per SSMA, incluse le finestre di esplorazione dei metadati, metadati, le barre degli strumenti, riquadro di output e riquadro elenco errori:  
  
![Interfaccia utente di SSMA](../../ssma/db2/media/ssma_db2_ui.png "interfaccia utente di SSMA")  
  
Per avviare una migrazione, è innanzitutto necessario creare un nuovo progetto. Quindi, connettersi a un database DB2. Dopo la connessione ha esito positivo, gli schemi di DB2 verranno visualizzato in Visualizzatore metadati DB2. È possibile quindi oggetti pulsante destro del mouse in Visualizzatore metadati DB2 per eseguire attività quali la creano di report che valutano le conversioni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È anche possibile eseguire queste attività tramite i menu e barre degli strumenti.  
  
È inoltre necessario connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Dopo la connessione ha esito positivo, una gerarchia di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database verranno visualizzati nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati. Dopo la conversione degli schemi DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schemi, selezionare tali schemi convertiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati e quindi sincronizzare gli schemi con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Dopo la sincronizzazione di convertire gli schemi con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile tornare a Visualizzatore metadati DB2 e la migrazione dei dati da schemi di DB2 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
Per ulteriori informazioni su queste attività e su come eseguire tali operazioni, vedere [la migrazione di database DB2 a SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md).  
  
Nelle sezioni seguenti vengono descritte le funzionalità dell'interfaccia utente SSMA.  
  
### <a name="metadata-explorers"></a>Finestre di esplorazione dei metadati  
SSMA contiene due finestre di esplorazione dei metadati per individuare ed eseguire azioni su DB2 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
#### <a name="db2-metadata-explorer"></a>DB2 Visualizzatore metadati  
Visualizzatore metadati DB2 Mostra informazioni sugli schemi di DB2. Tramite Visualizzatore metadati DB2, è possibile eseguire le attività seguenti:  
  
-   Esplorare gli oggetti in ogni schema.  
  
-   Selezionare gli oggetti per la conversione e quindi convertire gli oggetti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi. Per ulteriori informazioni, vedere [DB2ToSQL la conversione di schemi di DB2 &#40; &#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
-   Selezionare le tabelle per la migrazione dei dati e quindi migrare i dati da tali tabelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per ulteriori informazioni, vedere [la migrazione di database DB2 a SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md).  
  
#### <a name="sql-server-metadata-explorer"></a>Visualizzatore metadati SQL Server  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Visualizzatore metadati Mostra le informazioni su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Quando ci si connette a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], recupera i metadati relativi a tale istanza e la archivia nel file di progetto SSMA.  
  
È possibile utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati per selezionare gli oggetti di database DB2 convertiti e quindi sincronizzare gli oggetti con l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
### <a name="metadata"></a>Metadati  
A destra di ogni Visualizzatore metadati sono schede che descrivono l'oggetto selezionato. Ad esempio, se si seleziona una tabella in Visualizzatore metadati DB2, verranno visualizzate sei schede: **tabella**, **SQL**, **del mapping dei tipi, Report**, **proprietà**, e **dati**. Il **Report** scheda contiene informazioni solo dopo aver creato un report che contiene l'oggetto selezionato. Se si seleziona una tabella in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, verranno visualizzate tre schede: **tabella**, **SQL**, e **dati**.  
  
La maggior parte delle impostazioni dei metadati sono di sola lettura. Tuttavia, è possibile modificare i metadati seguenti:  
  
-   In Visualizzatore metadati DB2, è possibile alter procedure e i mapping dei tipi. Per convertire le procedure modificate e i mapping dei tipi, è possibile apportare modifiche prima di convertire gli schemi.  
  
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, è possibile modificare il [!INCLUDE[tsql](../../includes/tsql_md.md)] per le stored procedure. Per visualizzare le modifiche in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], apportare queste modifiche prima di caricare gli schemi in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Le modifiche apportate in un Visualizzatore metadati vengono riflesse nei metadati del progetto, non nei database di origine o di destinazione.  
  
### <a name="toolbars"></a>Barre degli strumenti  
SSMA è due barre degli strumenti: una barra degli strumenti del progetto e una barra degli strumenti di migrazione.  
  
#### <a name="the-project-toolbar"></a>La barra degli strumenti del progetto  
La barra degli strumenti del progetto contiene pulsanti per l'utilizzo di progetti, la connessione a DB2 e connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Questi pulsanti sono simili a quelli nel **File** menu.  
  
#### <a name="migration-toolbar"></a>Barra degli strumenti di migrazione  
La tabella seguente illustra la migrazione di comandi della barra degli strumenti:  
  
|Pulsante|Funzione|  
|------|--------|  
|**Creazione di Report**|Converte gli oggetti selezionati di DB2 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi, quindi viene creato un report che mostra come esito positivo della conversione.<br /><br />Questo comando è disabilitato a meno che non vengono selezionati gli oggetti in Visualizzatore metadati DB2.|  
|**Converti Schema**|Converte gli oggetti selezionati di DB2 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti.<br /><br />Questo comando è disabilitato a meno che non vengono selezionati gli oggetti in Visualizzatore metadati DB2.|  
|**La migrazione dei dati**|Esegue la migrazione di dati dal database di DB2 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Prima di eseguire questo comando, è necessario convertire gli schemi di DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schemi, quindi caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br />Questo comando è disabilitato a meno che non vengono selezionati gli oggetti in Visualizzatore metadati DB2.|  
|**Arresta**|Arresta il processo corrente.|  
  
### <a name="menus"></a>Menu  
Nella tabella seguente viene illustrato i menu SSMA.  
  
|Menu|Description|  
|----|-----------|  
|**File**|Contiene i comandi per l'utilizzo di progetti, la connessione a DB2 e connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|**Modifica**|Contiene i comandi per la ricerca e l'utilizzo del testo nelle pagine di dettagli, ad esempio la copia [!INCLUDE[tsql](../../includes/tsql_md.md)] dal riquadro dei dettagli SQL. Contiene inoltre il **gestire segnalibri** opzione, in cui sarà in grado di visualizzare un elenco di segnalibri. È possibile utilizzare i pulsanti sul lato destro della finestra di dialogo per gestire i segnalibri.|  
|**Visualizza**|Contiene il **sincronizzare i metadati Explorers** comando. Che consente di sincronizzare gli oggetti tra Visualizzatore metadati DB2 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati. Contiene inoltre i comandi per visualizzare e nascondere il **Output** e **elenco errori** riquadri e un'opzione **layout** per gestire il layout.|  
|**Strumenti**|Contiene i comandi per creare report ed eseguire la migrazione di oggetti e dati. Fornisce inoltre l'accesso per il **impostazioni globali** e **impostazioni progetto** finestre di dialogo.|  
|**?**|Fornisce l'accesso di SSMA Guida in linea e di ottenere il **su** la finestra di dialogo.|  
  
### <a name="output-pane-and-error-list-pane"></a>Riquadro di output e il riquadro elenco errori  
Il **vista** menu sono disponibili comandi per attivare o disattivare la visibilità del riquadro di Output e il riquadro elenco errori:  
  
-   Il riquadro di output mostra i messaggi di stato da SSMA durante la conversione degli oggetti di sincronizzazione dell'oggetto e migrazione dei dati.  
  
-   Nel riquadro elenco errori Mostra messaggi di errore, avviso e informativi in un elenco ordinabile.  
  
## <a name="see-also"></a>Vedere anche  
[La migrazione dei dati di DB2 in SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
[Riferimento all'interfaccia utente &#40; DB2ToSQL &#41;](../../ssma/db2/user-interface-reference-db2tosql.md)  
  

