---
title: "Editor attività Invia messaggi (pagina messaggio) | Documenti Microsoft"
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
- sql13.dts.designer.sendmailtask.mail.f1
helpviewer_keywords:
- Send Mail Task Editor
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0c630d4044cf083e80b25ea2aac60b74a5bc9d7e
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="send-mail-task-editor-mail-page"></a>Editor attività Invia messaggi (pagina Messaggio)
  Usare la pagina **Messaggio** della finestra di dialogo **Editor attività Invia messaggi** per specificare i destinatari, il tipo di messaggio e la priorità relativi a un messaggio. È inoltre possibile allegare file al messaggio. Il testo del messaggio può essere una stringa specificata, una connessione a un file che contiene il testo o il nome di una variabile che contiene il testo.  
  
 Per ulteriori informazioni su questa attività, vedere [Send Mail Task](../../integration-services/control-flow/send-mail-task.md).  
  
## <a name="options"></a>Opzioni  
 **SMTPConnection**  
 Selezionare una gestione connessione SMTP nell'elenco oppure fare clic su  **\<nuova connessione >** per creare una nuova gestione connessione.  
  
> [!IMPORTANT]  
>  La gestione connessione SMTP supporta solo l'autenticazione anonima e l'autenticazione di Windows. Non supporta l'autenticazione di base.  
  
 **Argomenti correlati:** [Gestione connessione SMTP](../../integration-services/connection-manager/smtp-connection-manager.md)  
  
 **From**  
 Consente di specificare l'indirizzo di posta elettronica del mittente.  
  
 **Per**  
 Consente di specificare gli indirizzi di posta elettronica dei destinatari, separati da punti e virgola.  
  
 **Cc**  
 Consente di specificare gli indirizzi di posta elettronica, separati da punti e virgola, di altri destinatari che riceveranno copie del messaggio.  
  
 **Bcc**  
 Consente di specificare gli indirizzi di posta elettronica, separati da punti e virgola, di destinatari in copia nascosta che riceveranno copie del messaggio.  
  
 **Oggetto**  
 Consente di specificare l'oggetto del messaggio di posta elettronica.  
  
 **MessageSourceType**  
 Consente di selezionare il tipo di origine del messaggio. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Input diretto**|Consente di impostare l'origine sul testo del messaggio. Selezionando questo valore, verrà visualizzata l'opzione dinamica **MessageSource**.|  
|**Connessione file**|Consente di impostare l'origine sul file contenente il testo del messaggio. Selezionando questo valore, verrà visualizzata l'opzione dinamica **MessageSource**.|  
|**Variabile**|Consente di impostare l'origine su una variabile contenente il testo del messaggio. Selezionando questo valore, verrà visualizzata l'opzione dinamica **MessageSource**.|  
  
 **Priorità**  
 Consente di impostare il livello di priorità del messaggio.  
  
 **Allegati**  
 Consente di specificare i nomi file degli allegati del messaggio di posta elettronica, separati dal carattere di barra verticale (|).  
  
> [!NOTE]  
>  Le righe A, Cc e Ccn sono limitate a 256 caratteri, in conformità con gli standard Internet.  
  
## <a name="messagesourcetype-dynamic-options"></a>Opzioni dinamiche MessageSourceType  
  
### <a name="messagesourcetype--direct-input"></a>MessageSourceType = Input diretto  
 **MessageSource**  
 Digitare il testo del messaggio oppure fare clic sul pulsante Sfoglia (…), quindi digitare il messaggio nella finestra di dialogo **Origine messaggio** .  
  
### <a name="messagesourcetype--file-connection"></a>MessageSourceType = Connessione file  
 **MessageSource**  
 Selezionare una gestione connessione File nell'elenco oppure fare clic su \< **nuova connessione...** > per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### <a name="messagesourcetype--variable"></a>MessageSourceType = Variabile  
 **MessageSource**  
 Selezionare una variabile nell'elenco oppure fare clic su \< **nuova variabile...** > per creare una nuova variabile.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Aggiungi variabile](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../integration-services/integration-services-error-and-message-reference.md)   
 [Invio di posta elettronica attività Editor &#40; Pagina generale &#41;](../../integration-services/control-flow/send-mail-task-editor-general-page.md)   
 [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
  
