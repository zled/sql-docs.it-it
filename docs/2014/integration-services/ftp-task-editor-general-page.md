---
title: Editor attività FTP (pagina generale) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.ftptask.general.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 28b46fdd-b04a-4f97-a99f-883f5735a6d9
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 786f0d4371773f77045f0ef9cd6825057c12a937
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157778"
---
# <a name="ftp-task-editor-general-page"></a>Editor attività FTP (pagina Generale)
  Utilizzare la pagina **Generale** della finestra di dialogo **Editor attività FTP** per specificare la gestione connessione FTP tramite cui viene stabilita la connessione al server FTP con cui comunica l'attività. È inoltre possibile specificare un nome e una descrizione per l'attività FTP.  
  
 Per altre informazioni su questa attività, vedere [FTP Task](control-flow/ftp-task.md).  
  
## <a name="options"></a>Opzioni  
 **FtpConnection**  
 Consente di selezionare una gestione connessione FTP esistente o di creare una gestione connessione facendo clic su \<**Nuova connessione**>.  
  
> [!IMPORTANT]  
>  La gestione connessione FTP supporta solo l'autenticazione anonima e l'autenticazione di base. Non supporta l'autenticazione di Windows.  
  
 **Argomenti correlati**: [FTP Connection Manager](connection-manager/ftp-connection-manager.md), [FTP Connection Manager Editor](../../2014/integration-services/ftp-connection-manager-editor.md)  
  
 **StopOnFailure**  
 Consente di specificare il termine dell'attività FTP in caso di esito negativo di un'operazione FTP.  
  
 **Nome**  
 Consente di specificare un nome univoco per l'attività FTP. Tale nome viene utilizzato come etichetta nell'icona dell'attività.  
  
> [!NOTE]  
>  I nomi delle attività devono essere univoci all'interno di un pacchetto.  
  
 **Descrizione**  
 Consente di digitare una descrizione dell'attività FTP.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per i messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività FTP &#40;pagina trasferimento File&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md)   
 [Pagina Espressioni](expressions/expressions-page.md)  
  
  