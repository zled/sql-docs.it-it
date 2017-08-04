---
title: Editor origine ODBC (pagina Output degli errori) | Documenti Microsoft
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
- sql13.ssis.designer.odbcsource.errorhandling.f1
ms.assetid: b2f6866c-db07-4cb3-9f38-889f8d2b03e6
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 86f1fa7d2408fe43f5f76a3d5470f9eb295145d6
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="odbc-source-editor-error-output-page"></a>Editor origine ODBC (pagina Output degli errori)
  Usare la pagina **Output degli errori** della finestra di dialogo **ODBC Source Editor** (Editor origine ODBC) per selezionare le opzioni di gestione degli errori.  
  
 Per sapere di più sull'origine ODBC, vedere [Origine CDC](../../integration-services/data-flow/cdc-source.md).  
  
## <a name="task-list"></a>Elenco attività  
 **Per aprire ODBC Source Editor (pagina Output degli errori)**  
  
-   In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], aprire il pacchetto [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] che contiene l'origine ODBC.  
  
-   Nella scheda **Flusso di dati** fare doppio clic sull'origine ODBC.  
  
-   In **ODBC Source Editor**(Editor origine ODBC) fare clic su **Output degli errori**.  
  
## <a name="options"></a>Opzioni  
  
### <a name="inputoutput"></a>Input/Output  
 Consente di visualizzare il nome dell'origine dei dati.  
  
### <a name="column"></a>Colonna  
 Non usato.  
  
### <a name="error"></a>Errore  
 Consente di selezionare il modo in cui l'origine ODBC deve gestire gli errori in un flusso: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
### <a name="truncation"></a>Troncamento  
 Consente di selezionare il modo in cui l'origine ODBC deve gestire il troncamento in un flusso: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
### <a name="description"></a>Description  
 Non usato.  
  
### <a name="set-this-value-to-selected-cells"></a>Imposta questo valore nelle celle selezionate  
 Consente di selezionare il modo in cui l'origine ODBC gestisce tutte le celle selezionate in caso di errore o troncamento: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
### <a name="apply"></a>Applica  
 Consente di applicare le opzioni di gestione degli errori alle celle selezionate.  
  
## <a name="error-handling-options"></a>Opzioni di gestione degli errori  
 Utilizzare le opzioni seguenti per configurare il modo in cui l'origine ODBC gestisce errori e troncamenti.  
  
### <a name="fail-component"></a>Interrompi componente  
 Quando si verifica un errore o un troncamento l'attività Flusso di dati viene interrotta. Questo è il comportamento predefinito.  
  
### <a name="ignore-failure"></a>Ignora errore  
 L'errore o il troncamento vengono ignorati.  
  
### <a name="redirect-flow"></a>Reindirizza flusso  
 La riga che determina l'errore o il troncamento viene inviata all'output degli errori dell'origine ODBC. Per altre informazioni, vedere [Origine ODBC](../../integration-services/data-flow/odbc-source.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Editor origine ODBC &#40; Pagina Gestione connessione &#41;](../../integration-services/data-flow/odbc-source-editor-connection-manager-page.md)   
 [Editor origine ODBC &#40; Pagina colonne &#41;](../../integration-services/data-flow/odbc-source-editor-columns-page.md)  
  
  
