---
title: "Errore Editor attività Trasferisci messaggi (pagina messaggi) | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8051e89dc6c319d13f51d086d702145548ea7e48
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="transfer-error-messages-task-editor-messages-page"></a>Editor attività Trasferisci messaggi di errore (pagina Messaggi)
  Usare la pagina **Messaggi** della finestra di dialogo **Editor attività Trasferisci messaggi di errore** per specificare le proprietà relative alla copia di uno o più messaggi di errore definiti dall'utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tra due istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni su questa attività, vedere [Transfer Error Messages Task](../../integration-services/control-flow/transfer-error-messages-task.md).  
  
## <a name="options"></a>Opzioni  
 **SourceConnection**  
 Selezionare una gestione connessione SMO nell'elenco oppure fare clic su  **\<nuova connessione >** per creare una nuova connessione al server di origine.  
  
 **DestinationConnection**  
 Selezionare una gestione connessione SMO nell'elenco oppure fare clic su  **\<nuova connessione >** per creare una nuova connessione al server di destinazione.  
  
 **IfObjectExists**  
 Indicare se l'attività deve sovrascrivere i messaggi di errore definiti dall'utente esistenti, ignorare i messaggi esistenti oppure interrompersi in caso nel server di destinazione esistano già messaggi di errore con lo stesso nome.  
  
 **TransferAllErrorMessages**  
 Indicare se l'attività deve copiare dal server di origine al server di destinazione tutti i messaggi di errore definiti dall'utente o solo quelli specificati.  
  
 Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente:  
  
|Valore|Description|  
|-----------|-----------------|  
|**True**|Copia tutti i messaggi definiti dall'utente.|  
|**False**|Copia solo i messaggi definiti dall'utente specificati.|  
  
 **ErrorMessagesList**  
 Fare clic sui puntini di sospensione **(…)** per selezionare i messaggi di errore da copiare.  
  
> [!NOTE]  
>  È necessario specificare la proprietà **SourceConnection** prima di poter selezionare i messaggi di errore di cui eseguire la copia.  
  
 **ErrorMessageLanguagesList**  
 Fare clic sui puntini di sospensione **(…)** per selezionare le lingue per cui copiare i messaggi di errore definiti dall'utente nel server di destinazione. Per poter trasferire versioni del messaggio in altre lingue nel server di destinazione, è necessario che in tale server esista una versione us_english (tabella codici 1033) del messaggio.  
  
> [!NOTE]  
>  È necessario specificare la proprietà **SourceConnection** prima di poter selezionare i messaggi di errore di cui eseguire la copia.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../integration-services/integration-services-error-and-message-reference.md)   
 [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Editor attività i messaggi di errore di trasferimento &#40; Pagina generale &#41;](../../integration-services/control-flow/transfer-error-messages-task-editor-general-page.md)   
 [Gestione connessione SMO](../../integration-services/connection-manager/smo-connection-manager.md)   
 [Editor attività i messaggi di errore di trasferimento &#40; Pagina generale &#41;](../../integration-services/control-flow/transfer-error-messages-task-editor-general-page.md)   
 [Gestione connessione SMO](../../integration-services/connection-manager/smo-connection-manager.md)  
  
  
