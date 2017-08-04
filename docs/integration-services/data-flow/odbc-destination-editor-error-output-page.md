---
title: ODBC Destination Editor (pagina Output degli errori) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.designer.odbcdest.errorhandling.f1
ms.assetid: 0a743f8d-2a51-4296-9976-8104f5ca22d3
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e0fa59290399f3c3f7fc42b1f74b6a42c573f7d2
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="odbc-destination-editor-error-output-page"></a>Editor destinazione ODBC (pagina Output errori)
  Utilizzare la pagina **Output degli errori** della finestra di dialogo **ODBC Destination Editor** per selezionare le opzioni di gestione degli errori.  
  
 Per ulteriori informazioni sulla destinazione ODBC, vedere [ODBC Destination](../../integration-services/data-flow/odbc-destination.md).  
  
 **Per aprire ODBC Destination Editor (pagina Output degli errori)**  
  
## <a name="task-list"></a>Elenco attività  
  
-   In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], aprire il pacchetto [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] con la destinazione ODBC.  
  
-   Nella scheda **Flusso di dati** fare doppio clic sulla destinazione ODBC.  
  
-   In **ODBC Destination Editor**, fare clic su **Output degli errori**.  
  
## <a name="options"></a>Opzioni  
  
### <a name="inputoutput"></a>Input/Output  
 Consente di visualizzare il nome dell'origine dei dati.  
  
### <a name="column"></a>Colonna  
 Non usato.  
  
### <a name="error"></a>Errore  
 Consente di selezionare il modo in cui la destinazione ODBC deve gestire gli errori in un flusso: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
### <a name="truncation"></a>Troncamento  
 Consente di selezionare il modo in cui la destinazione ODBC deve gestire il troncamento in un flusso: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
### <a name="description"></a>Description  
 Consente di visualizzare una descrizione dell'errore.  
  
### <a name="set-this-value-to-selected-cells"></a>Imposta questo valore nelle celle selezionate  
 Consente di selezionare il modo in cui la destinazione ODBC gestisce tutte le celle selezionate in caso di errore o troncamento: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
### <a name="apply"></a>Applica  
 Consente di applicare le opzioni di gestione degli errori alle celle selezionate.  
  
## <a name="error-handling-options"></a>Opzioni di gestione degli errori  
 Utilizzare le opzioni seguenti per configurare il modo in cui la destinazione ODBC gestisce errori e troncamenti.  
  
### <a name="fail-component"></a>Interrompi componente  
 Quando si verifica un errore o un troncamento l'attività Flusso di dati viene interrotta. Questo è il comportamento predefinito.  
  
### <a name="ignore-failure"></a>Ignora errore  
 L'errore o il troncamento vengono ignorati.  
  
### <a name="redirect-flow"></a>Reindirizza flusso  
 La riga che determina l'errore o il troncamento viene inviata all'output degli errori della destinazione ODBC. Per ulteriori informazioni, vedere Destinazione ODBC.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor destinazione ODBC &#40; Pagina Gestione connessione &#41;](../../integration-services/data-flow/odbc-destination-editor-connection-manager-page.md)   
 [Editor destinazione ODBC &#40; Pagina mapping &#41;](../../integration-services/data-flow/odbc-destination-editor-mappings-page.md)  
  
  
