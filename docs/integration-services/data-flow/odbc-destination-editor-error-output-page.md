---
title: "Editor destinazione ODBC (pagina Output errori) | Microsoft Docs"
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
  - "sql13.ssis.designer.odbcdest.errorhandling.f1"
ms.assetid: 0a743f8d-2a51-4296-9976-8104f5ca22d3
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Editor destinazione ODBC (pagina Output errori)
  Utilizzare la pagina **Output degli errori** della finestra di dialogo **ODBC Destination Editor** per selezionare le opzioni di gestione degli errori.  
  
 Per ulteriori informazioni sulla destinazione ODBC, vedere [ODBC Destination](../../integration-services/data-flow/odbc-destination.md).  
  
 **Per aprire ODBC Destination Editor (pagina Output degli errori)**  
  
## Elenco attività  
  
-   In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], aprire il pacchetto [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] con la destinazione ODBC.  
  
-   Nella scheda **Flusso di dati** fare doppio clic sulla destinazione ODBC.  
  
-   In **ODBC Destination Editor**, fare clic su **Output degli errori**.  
  
## Opzioni  
  
### Input/Output  
 Consente di visualizzare il nome dell'origine dei dati.  
  
### Colonna  
 Non usato.  
  
### Errore  
 Consente di selezionare il modo in cui la destinazione ODBC deve gestire gli errori in un flusso: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
### Troncamento  
 Consente di selezionare il modo in cui la destinazione ODBC deve gestire il troncamento in un flusso: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
### Description  
 Consente di visualizzare una descrizione dell'errore.  
  
### Imposta questo valore nelle celle selezionate  
 Consente di selezionare il modo in cui la destinazione ODBC gestisce tutte le celle selezionate in caso di errore o troncamento: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
### Applica  
 Consente di applicare le opzioni di gestione degli errori alle celle selezionate.  
  
## Opzioni di gestione degli errori  
 Utilizzare le opzioni seguenti per configurare il modo in cui la destinazione ODBC gestisce errori e troncamenti.  
  
### Interrompi componente  
 Quando si verifica un errore o un troncamento l'attività Flusso di dati viene interrotta. Questo è il comportamento predefinito.  
  
### Ignora errore  
 L'errore o il troncamento vengono ignorati.  
  
### Reindirizza flusso  
 La riga che determina l'errore o il troncamento viene inviata all'output degli errori della destinazione ODBC. Per ulteriori informazioni, vedere Destinazione ODBC.  
  
## Vedere anche  
 [Editor destinazione ODBC &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/odbc-destination-editor-connection-manager-page.md)   
 [Editor destinazione ODBC &#40;pagina Mapping&#41;](../../integration-services/data-flow/odbc-destination-editor-mappings-page.md)  
  
  