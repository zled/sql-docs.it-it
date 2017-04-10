---
title: "Editor destinazione ODBC (pagina Gestione connessione) | Microsoft Docs"
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
  - "sql13.ssis.designer.odbcdest.connection.f1"
ms.assetid: f6d9c6c2-e4c4-468b-9e0d-af7b9609614d
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Editor destinazione ODBC (pagina Gestione connessione)
  Utilizzare la pagina **Gestione connessione** della finestra di dialogo **ODBC Destination Editor** per selezionare la gestione connessione ODBC per la destinazione. Tramite questa pagina è inoltre possibile selezionare una tabella o una vista del database  
  
 Per ulteriori informazioni sulla destinazione ODBC, vedere [ODBC Destination](../../integration-services/data-flow/odbc-destination.md).  
  
 **Per aprire ODBC Destination Editor (pagina Gestione connessione)**  
  
## Elenco attività  
  
-   In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], aprire il pacchetto [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] con la destinazione ODBC.  
  
-   Nella scheda **Flusso di dati** fare doppio clic sulla destinazione ODBC.  
  
-   In **ODBC Destination Editor**, fare clic su **Gestione connessione**.  
  
## Opzioni  
  
### Gestione connessione  
 Consente di selezionare una gestione connessione ODBC esistente nell'elenco o di creare una nuova connessione facendo clic su Nuova. La connessione può essere a qualsiasi database supportato da ODBC.  
  
### Nuova  
 Fare clic su **Nuovo**. Viene visualizzata la finestra di dialogo **Configura gestione connessione ODBC** in cui è possibile creare una nuova gestione connessione.  
  
### Modalità di accesso ai dati  
 Consente di selezionare il metodo di caricamento dei dati nella destinazione. Le opzioni disponibili vengono visualizzate nella tabella seguente.  
  
|Opzione|Description|  
|------------|-----------------|  
|Nome tabella - Batch|Selezionare questa opzione per configurare la destinazione ODBC per l'utilizzo della modalità batch. Se si seleziona questa opzione, sono disponibili le opzioni seguenti.|  
||**Nome tabella o vista**: selezionare una tabella o vista disponibile nell'elenco.<br /><br /> Questo elenco contiene solo le prime 1000 tabelle. Se il database contiene più di 1000 tabelle, è possibile digitare l'inizio di un nome di tabella o usare il carattere jolly (\*) per immettere qualsiasi parte del nome e visualizzare la tabella o le tabelle che si vuole usare.<br /><br /> **Dimensioni batch**: digitare la dimensione del batch per il caricamento bulk. Si tratta del numero di righe caricato come un batch|  
|Nome tabella - Riga per riga|Selezionare questa opzione per configurare la destinazione ODBC per l'inserimento di una riga per volta nella tabella di destinazione. Se si seleziona questa opzione, è disponibile l'opzione seguente.|  
||**Nome tabella o vista**: selezionare una tabella o vista disponibile del database dall'elenco.<br /><br /> Questo elenco contiene solo le prime 1000 tabelle. Se il database contiene più di 1000 tabelle, è possibile digitare l'inizio di un nome di tabella o utilizzare il carattere jolly (*) per immettere qualsiasi parte del nome e visualizzare la tabella o le tabelle che si desidera utilizzare.|  
  
### Anteprima  
 Fare clic su **Anteprima** per visualizzare fino a 200 dati per la tabella selezionata.  
  
## Vedere anche  
 [Proprietà personalizzate della destinazione ODBC](../../integration-services/data-flow/odbc-destination-custom-properties.md)   
 [Editor destinazione ODBC &#40;pagina Mapping&#41;](../../integration-services/data-flow/odbc-destination-editor-mappings-page.md)   
 [Editor destinazione ODBC &#40;pagina Output degli errori&#41;](../../integration-services/data-flow/odbc-destination-editor-error-output-page.md)  
  
  