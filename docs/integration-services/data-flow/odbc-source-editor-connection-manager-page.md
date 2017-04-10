---
title: "Editor origine ODBC (pagina Gestione connessione) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.odbcsource.connection.f1"
ms.assetid: e2c8dc83-6394-4d6c-9232-97e94be72431
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Editor origine ODBC (pagina Gestione connessione)
  Utilizzare la pagina **Gestione connessione** della finestra di dialogo **ODBC Source Editor** per selezionare la gestione connessione ODBC per l'origine. Tramite questa pagina è inoltre possibile selezionare una tabella o una vista del database.  
  
 Per ulteriori informazioni sull'origine ODBC, vedere [ODBC Source](../../integration-services/data-flow/odbc-source.md).  
  
## Elenco attività  
 **Per aprire ODBC Source Editor (pagina Gestione connessione)**  
  
-   In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], aprire il pacchetto [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] che contiene l'origine ODBC.  
  
-   Nella scheda **Flusso di dati** fare doppio clic sull'origine ODBC.  
  
## Opzioni  
  
### Gestione connessione  
 Consente di selezionare una gestione connessione ODBC esistente nell'elenco o di creare una nuova connessione facendo clic su **Nuova** . La connessione può essere a qualsiasi database supportato da ODBC.  
  
### Nuova  
 Fare clic su **Nuovo**. Viene visualizzata la finestra di dialogo **Configura gestione connessione ODBC** in cui è possibile creare una nuova gestione connessione ODBC.  
  
### Modalità di accesso ai dati  
 Consente di selezionare il metodo per la selezione dei dati dall'origine. Le opzioni disponibili vengono visualizzate nella tabella seguente.  
  
|Opzione|Description|  
|------------|-----------------|  
|Nome tabella|Consente di recuperare dati da una tabella o da una vista nell'origine dati ODBC. Se si seleziona questa opzione, scegliere un valore nell'elenco per le opzioni seguenti:|  
||**Nome tabella o vista**: selezionare una tabella o vista disponibile nell'elenco o digitare un'espressione regolare per identificare la tabella.|  
||Questo elenco contiene solo le prime 1000 tabelle. Se il database contiene più di 1000 tabelle, è possibile digitare l'inizio di un nome di tabella o utilizzare il carattere jolly (*) per immettere qualsiasi parte del nome e visualizzare la tabella o le tabelle che si desidera utilizzare.|  
|Comando SQL|Consente di recuperare dati dall'origine dati ODBC utilizzando una query SQL. Scrivere la query nella sintassi del database di origine che si sta utilizzando. Se si seleziona questa opzione, immettere una query in uno dei modi seguenti:|  
||Immettere il testo della query SQL nel campo **Testo comando SQL** .|  
||Fare clic su **Sfoglia** per caricare la query SQL da un file di testo.|  
||Fare clic su **Analizza query** per verificare la sintassi del testo della query.|  
  
### Anteprima  
 Fare clic su **Anteprima** per visualizzare un massimo di 200 righe dei dati estratti dalla tabella o dalla vista selezionata.  
  
## Vedere anche  
 [Proprietà personalizzate dell'origine ODBC](../../integration-services/data-flow/odbc-source-custom-properties.md)   
 [Editor origine ODBC &#40;pagina Colonne&#41;](../../integration-services/data-flow/odbc-source-editor-columns-page.md)   
 [Editor origine ODBC &#40;pagina Output degli errori&#41;](../../integration-services/data-flow/odbc-source-editor-error-output-page.md)  
  
  