---
title: Editor attività servizio Web (pagina generale) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.general.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 32da4424359a7b27ebef6f48c988f9e20c6f4d71
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090231"
---
# <a name="web-service-task-editor-general-page"></a>Editor attività Servizio Web (pagina Generale)
  Usare la pagina **Generale** della finestra di dialogo **Editor attività Servizio Web** per specificare una gestione connessione HTTP e il percorso del file WSDL (Web Services Description Language) usato dall'attività Servizio Web, descrivere l'attività Servizio Web e scaricare il file WSDL.  
  
 Per altre informazioni su questa attività, vedere [Attività Servizio Web](control-flow/web-service-task.md).  
  
## <a name="options"></a>Opzioni  
 **HTTPConnection**  
 Selezionare una gestione connessione nell'elenco o creare una nuova gestione connessione facendo clic su \<**Nuova connessione**>.  
  
> [!IMPORTANT]  
>  La gestione connessione HTTP supporta solo l'autenticazione anonima e l'autenticazione di base. Non supporta l'autenticazione di Windows.  
  
 **Argomenti correlati**: [Gestione connessione HTTP](connection-manager/http-connection-manager.md), [Editor gestione connessione HTTP &#40;pagina Server&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)  
  
 **WSDLFile**  
 Consente di digitare il percorso completo di un file WSDL presente localmente nel computer o di trovare il file usando il pulsante Sfoglia **(…)** .  
  
 Sezionare il file WSDL presente nel computer, se è già stato scaricato manualmente. Se invece il file WSDL non è stato ancora scaricato, attenersi alla seguente procedura:  
  
-   Creare un file vuoto con l'estensione di file "wsdl".  
  
-   Selezionare questo file vuoto per l'opzione **WSDLFile** .  
  
-   Impostare il valore della **OverwriteWSDLFile** a `True` per consentire al file vuoto di essere sovrascritto con il file WSDL effettivo.  
  
-   Fare clic su **Scarica WSDL** per scaricare il file WSDL effettivo e sovrascrivere il file vuoto.  
  
    > [!NOTE]  
    >  L'opzione **Scarica WSDL** non è abilitato fino a quando non si fornisce il nome di un file locale esistente nella casella **WSDLFile** .  
  
 **OverwriteWSDLFile**  
 Consente di specificare se il file WSDL per l'attività Servizio Web può essere sovrascritto.  
  
 Se si intende scaricare il file WSDL tramite il **Scarica WSDL** pulsante, impostare questo valore su `True`.  
  
 **Nome**  
 Consente di specificare un nome univoco per l'attività Servizio Web. Tale nome viene utilizzato come etichetta nell'icona dell'attività.  
  
> [!NOTE]  
>  I nomi delle attività devono essere univoci all'interno di un pacchetto.  
  
 **Descrizione**  
 Consente di digitare una descrizione dell'attività Servizio Web.  
  
 **Scarica WSDL**  
 Consente di scaricare il file WSDL.  
  
 Questo pulsante non è attivato fino a quando non si fornisce il nome di un file locale esistente nella casella **WSDLFile** .  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività servizio Web &#40;pagina di Input&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Editor attività servizio Web &#40;pagina di Output&#41;](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [Pagina Espressioni](expressions/expressions-page.md)  
  
  
