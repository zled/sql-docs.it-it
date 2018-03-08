---
title: Introduzione a SQL Server Migration Assistant per Access | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- error list pane
- getting started
- menus
- metadata explorers
- output pane
- toolbars
- user interface
- user interface overview
ms.assetid: 462a731f-08f1-44e1-9eeb-4deac6d2f6c5
caps.latest.revision: "24"
author: Shamikg
ms.author: Shamikg
manager: murato
ms.workload: On Demand
ms.openlocfilehash: 92a7e496075cb7e42c09bd89a1f17e1b296b9946
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="getting-started-with-sql-server-migration-assistant-for-access-accesstosql"></a>Introduzione a SQL Server Migration Assistant per Access (AccessToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) per l'accesso consente di convertire rapidamente oggetti di database di Access da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli oggetti di database SQL di Azure, caricare gli oggetti risultanti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, e la migrazione dei dati dall'accesso al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure. Se necessario, è anche possibile collegare le tabelle di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tabelle di database SQL di Azure in modo che è possibile continuare a utilizzare le applicazioni front-end di Access esistenti con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure.  
  
In questo argomento introduce il processo di installazione e consente di acquisire familiarità con l'interfaccia utente SSMA.  
  
## <a name="installing-ssma"></a>L'installazione di SSMA  
Per l'utilizzo di SSMA, è innanzitutto necessario installare il programma client SSMA in un computer che possa accedere a entrambi i database che si desidera eseguire la migrazione e l'istanza di destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure. Per istruzioni sull'installazione, vedere [l'installazione di SQL Server Migration Assistant per Access &#40; AccessToSQL &#41; ](../../ssma/access/installing-sql-server-migration-assistant-for-access-accesstosql.md).  
  
Per avviare SSMA, fare clic su **avviare**, scegliere **tutti i programmi**, scegliere **SQL Server Migration Assistant per Access**, quindi selezionare **SQL Server Migration Assistant per Access**.  
  
## <a name="using-ssma"></a>Utilizzo di SSMA  
Dopo l'installazione di SSMA, è utile per acquisire familiarità con l'interfaccia utente SSMA prima di utilizzare lo strumento per la migrazione dei database di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure. L'interfaccia utente SSMA, incluse le finestre di esplorazione dei metadati, metadati, le barre degli strumenti, riquadro di output e riquadro elenco errori vengono visualizzati nel diagramma seguente:  
  
![SSMA per l'interfaccia utente grafica di accesso](../../ssma/access/media/ssmaforaccessgui.gif "SSMA per l'interfaccia utente grafica di accesso")  
  
Per avviare una migrazione, creare un nuovo progetto e quindi aggiungere i database di Access a soluzioni di accesso ai metadati. È quindi possibile fare doppio clic su oggetti in Visualizzatore metadati di accesso per eseguire attività quali:
- Esportazione di un inventario degli oggetti di database di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure.
- Creazione di report che valutano le conversioni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure.
- Conversione di schemi di accesso per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o degli schemi di database SQL di Azure.

È anche possibile eseguire queste attività tramite i menu e barre degli strumenti.  
  
È inoltre necessario connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Dopo la connessione ha esito positivo, una gerarchia di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database viene visualizzato [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati. Dopo la conversione degli schemi di accesso per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schemi, è possibile selezionare questi schemi convertiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati e quindi caricare degli schemi in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Se si è scelto il database di SQL Azure dalla migrazione di elenco a discesa nella finestra di dialogo Nuovo progetto, è necessario connettersi al database SQL di Azure. Dopo la connessione ha esito positivo, una gerarchia di database di database SQL di Azure viene visualizzato in Visualizzatore metadati di database SQL Azure. Dopo la conversione degli schemi di accesso agli schemi di database SQL di Azure, è possibile selezionare questi schemi convertiti in Visualizzatore metadati di database SQL Azure e quindi caricare degli schemi in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Dopo aver caricato gli schemi convertiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, è possibile tornare a Visualizzatore metadati di accesso e la migrazione dei dati dal database di Access in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o i database di database SQL di Azure. Se necessario, è anche possibile collegare le tabelle di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tabelle di database SQL di Azure.  
  
Per ulteriori informazioni su queste attività e su come eseguire tali operazioni, vedere gli argomenti seguenti:  
  
-   [Preparazione dei database di Access per la migrazione](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
  
-   [Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
-   [Il collegamento alle applicazioni di accesso di SQL Server](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)  
  
Nelle sezioni seguenti vengono descritte le funzionalità dell'interfaccia utente SSMA.  
  
### <a name="metadata-explorers"></a>Finestre di esplorazione dei metadati  
SSMA contiene due strumenti di esplorazione dei metadati che è possibile utilizzare per esplorare e di eseguire azioni sull'accesso e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o i database di database SQL di Azure.  
  
#### <a name="access-metadata-explorer"></a>Accedere a Visualizzatore metadati  
Visualizzatore metadati accesso Mostra le informazioni sui database di Access che sono stati aggiunti al progetto. Quando si aggiunge un database di Access, SSMA recupera i metadati relativi a tale database, ovvero i metadati disponibili in Visualizzatore metadati di accesso.  
  
È possibile utilizzare Visualizzatore metadati di accesso per eseguire le attività seguenti:  
  
-   Selezionare le tabelle in ogni database di Access.  
  
-   Selezionare gli oggetti per la conversione e convertire gli oggetti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi. Per ulteriori informazioni, vedere [la conversione di oggetti di Database di Access](http://msdn.microsoft.com/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c).  
  
-   Selezionare gli oggetti per la migrazione dei dati e la migrazione dei dati da tali oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per ulteriori informazioni, vedere [la migrazione di accesso ai dati in SQL Server](http://msdn.microsoft.com/f3b18af7-1af0-499d-a00d-a0af94895625).  
  
-   Collegare e scollegare l'accesso e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tabelle.  
  
#### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQL Server o Visualizzatore metadati di database SQL di Azure  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]o Visualizzatore metadati di database SQL Azure Mostra le informazioni su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure. Quando ci si connette a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, SSMA recupera i metadati relativi a tale istanza e viene memorizzato nel file di progetto.  
  
È possibile utilizzare SQL Server o Visualizzatore metadati di database SQL Azure per selezionare oggetti di database di Access convertiti e caricare (sincronizzazione) gli oggetti nell'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure.  
  
Per ulteriori informazioni, vedere [il caricamento di convertire gli oggetti di Database in SQL Server](http://msdn.microsoft.com/4e854eee-b10c-4f0b-9d9e-d92416e6f2ba).  
  
### <a name="metadata"></a>Metadati  
A destra di ogni Visualizzatore metadati sono schede che descrivono l'oggetto selezionato. Ad esempio, se si seleziona una tabella in soluzioni di accesso ai metadati, quattro schede vengono visualizzate: **tabella**, **del mapping dei tipi**, **proprietà**, e **dati**. Se si seleziona una tabella in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, tre schede vengono visualizzate: **tabella**, **SQL**, e **dati**.  
  
La maggior parte delle impostazioni dei metadati sono di sola lettura. Tuttavia, è possibile modificare i metadati seguenti:  
  
-   In Visualizzatore metadati di accesso, è possibile modificare i mapping dei tipi. Assicurarsi di apportare queste modifiche prima di creare report o convertire gli schemi.  
  
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, è possibile modificare le proprietà di tabelle e indici di **tabella** scheda. Apportare queste modifiche prima di caricare gli schemi in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per ulteriori informazioni, vedere [la conversione di oggetti di Database di Access](http://msdn.microsoft.com/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c).  
  
### <a name="toolbars"></a>Barre degli strumenti  
SSMA è due barre degli strumenti: una barra degli strumenti del progetto e una barra degli strumenti di migrazione.  
  
#### <a name="the-project-toolbar"></a>La barra degli strumenti del progetto  
La barra degli strumenti del progetto contiene pulsanti per l'utilizzo di progetti, aggiunta di file di database di Access e connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure. Questi pulsanti sono simili a quelli nel **File** menu.  
  
#### <a name="the-migration-toolbar"></a>La barra degli strumenti di migrazione  
La barra degli strumenti di migrazione include i comandi seguenti:  
  
|Pulsante|Funzione|  
|----------|------------|  
|**Convertire, caricare ed eseguire la migrazione**|Converte i database di Access, carica oggetti convertiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, e viene eseguita la migrazione di dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, un'unica operazione.|  
|**Creazione di Report**|Converte lo schema di accesso selezionato per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi di database SQL di Azure e quindi crea un report che mostra come esito positivo della conversione.<br /><br />Questo comando è disponibile solo quando gli oggetti selezionati in Visualizzatore metadati di accesso.|  
|**Converti Schema**|Consente di convertire lo schema di accesso selezionato per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o degli schemi di database SQL di Azure.<br /><br />Questo comando è disponibile solo quando gli oggetti selezionati in Visualizzatore metadati di accesso.|  
|**La migrazione dei dati**|Esegue la migrazione di dati dal database di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure. Prima di eseguire questo comando, è necessario convertire gli schemi di accesso da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o schemi di database SQL di Azure, quindi caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure.<br /><br />Questo comando è disponibile solo quando gli oggetti selezionati in Visualizzatore metadati di accesso.|  
|**Arresta**|Arresta il processo corrente, ad esempio la conversione di oggetti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi di database SQL di Azure.|  
  
### <a name="menus"></a>Menu  
SSMA contiene i menu seguenti:  
  
|Menu|Description|  
|--------|---------------|  
|**File**|Contiene i comandi per la migrazione guidata, utilizzo di progetti, aggiunta e rimozione dei file di database di Access e la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure.|  
|**Modifica**|Contiene i comandi per la ricerca e l'utilizzo del testo nelle pagine di dettagli, ad esempio la copia [!INCLUDE[tsql](../../includes/tsql_md.md)] dal riquadro dei dettagli SQL. Per aprire la **gestire segnalibri** finestra di dialogo, dal menu Modifica, fare clic su Gestisci segnalibri. Nella finestra di dialogo verrà visualizzato un elenco di segnalibri. È possibile utilizzare i pulsanti sul lato destro della finestra di dialogo per gestire i segnalibri.|  
|**Visualizza**|Contiene il **sincronizzare i metadati Explorers** comando. Questo consente di sincronizzare gli oggetti tra Visualizzatore metadati di accesso e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di database SQL Azure. Contiene inoltre i comandi per visualizzare e nascondere il **Output** e **elenco errori** riquadri e un'opzione **layout** da gestire con il layout.|  
|**Strumenti**|Contiene i comandi per creare report, esportare i dati, eseguire la migrazione di oggetti e dati, collegare le tabelle e fornisce finestre di dialogo di accesso a globali e le impostazioni del progetto.|  
|**?**|Fornisce l'accesso di SSMA Guida in linea e di ottenere il **su** la finestra di dialogo.|  
  
### <a name="output-pane-and-error-list-pane"></a>Riquadro di output e il riquadro elenco errori  
Il **vista** menu sono disponibili comandi per attivare o disattivare la visibilità del riquadro di Output e il riquadro elenco errori:  
  
-   Il riquadro di Output Mostra i messaggi di stato da SSMA durante la conversione degli oggetti di sincronizzazione dell'oggetto e migrazione dei dati.  
  
-   Nel riquadro elenco errori Mostra messaggi di errore, avviso e informativi in un elenco che è possibile ordinare.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
