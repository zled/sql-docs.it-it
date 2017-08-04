---
title: "Editor attività tramite servizio Web (pagina generale) | Documenti Microsoft"
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
- sql13.dts.designer.webservicestask.general.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2c65419846e21225c6b5fe41bc07cfbae6dffe01
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="web-service-task-editor-general-page"></a>Editor attività Servizio Web (pagina Generale)
  Usare la pagina **Generale** della finestra di dialogo **Editor attività Servizio Web** per specificare una gestione connessione HTTP e il percorso del file WSDL (Web Services Description Language) usato dall'attività Servizio Web, descrivere l'attività Servizio Web e scaricare il file WSDL.  
  
 Per altre informazioni su questa attività, vedere [Attività Servizio Web](../../integration-services/control-flow/web-service-task.md).  
  
## <a name="options"></a>Opzioni  
 **HTTPConnection**  
 Selezionare una gestione connessione nell'elenco oppure fare clic su \< **nuova connessione...** > per creare una nuova gestione connessione.  
  
> [!IMPORTANT]  
>  La gestione connessione HTTP supporta solo l'autenticazione anonima e l'autenticazione di base. Non supporta l'autenticazione di Windows.  
  
 **Argomenti correlati**: [Gestione connessione HTTP](../../integration-services/connection-manager/http-connection-manager.md), [Editor gestione connessione HTTP &#40;pagina Server&#41;](../../integration-services/connection-manager/http-connection-manager-editor-server-page.md)  
  
 **WSDLFile**  
 Consente di digitare il percorso completo di un file WSDL presente localmente nel computer o di trovare il file usando il pulsante Sfoglia **(…)** .  
  
 Sezionare il file WSDL presente nel computer, se è già stato scaricato manualmente. Se invece il file WSDL non è stato ancora scaricato, attenersi alla seguente procedura:  
  
-   Creare un file vuoto con l'estensione di file "wsdl".  
  
-   Selezionare questo file vuoto per l'opzione **WSDLFile** .  
  
-   Impostare il valore di **OverwriteWSDLFile** su **True** per consentire al file vuoto di essere sovrascritto con il file WSDL effettivo.  
  
-   Fare clic su **Scarica WSDL** per scaricare il file WSDL effettivo e sovrascrivere il file vuoto.  
  
    > [!NOTE]  
    >  L'opzione **Scarica WSDL** non è abilitato fino a quando non si fornisce il nome di un file locale esistente nella casella **WSDLFile** .  
  
 **OverwriteWSDLFile**  
 Consente di specificare se il file WSDL per l'attività Servizio Web può essere sovrascritto.  
  
 Se si intende scaricare il file WSDL tramite il pulsante **Scarica WSDL** , impostare questo valore su **True**.  
  
 **Nome**  
 Consente di specificare un nome univoco per l'attività Servizio Web. Tale nome viene utilizzato come etichetta nell'icona dell'attività.  
  
> [!NOTE]  
>  I nomi delle attività devono essere univoci all'interno di un pacchetto.  
  
 **Description**  
 Consente di digitare una descrizione dell'attività Servizio Web.  
  
 **Scarica WSDL**  
 Consente di scaricare il file WSDL.  
  
 Questo pulsante non è attivato fino a quando non si fornisce il nome di un file locale esistente nella casella **WSDLFile** .  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../integration-services/integration-services-error-and-message-reference.md)   
 [Web Editor attività servizio &#40; Input pagina &#41;](../../integration-services/control-flow/web-service-task-editor-input-page.md)   
 [Editor attività servizio Web &#40; pagina Output &#41;](../../integration-services/control-flow/web-service-task-editor-output-page.md)   
 [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
  
