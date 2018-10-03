---
title: Errore di Editor attività Trasferisci messaggi (pagina messaggi) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 590cb6da26f0857c62b87542b7890732416aa486
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103991"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a>Editor attività Trasferisci messaggi di errore (pagina Messaggi)
  Usare la pagina **Messaggi** della finestra di dialogo **Editor attività Trasferisci messaggi di errore** per specificare le proprietà relative alla copia di uno o più messaggi di errore definiti dall'utente di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tra due istanze di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Per ulteriori informazioni su questa attività, vedere [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md).  
  
## <a name="options"></a>Opzioni  
 **SourceConnection**  
 Selezionare una gestione connessione SMO nell'elenco o fare clic su **\<Nuova connessione...>** per creare una nuova connessione al server di origine.  
  
 **DestinationConnection**  
 Selezionare una gestione connessione SMO nell'elenco o fare clic su **Nuova connessione...>\<** per creare una nuova connessione al server di destinazione.  
  
 **IfObjectExists**  
 Indicare se l'attività deve sovrascrivere i messaggi di errore definiti dall'utente esistenti, ignorare i messaggi esistenti oppure interrompersi in caso nel server di destinazione esistano già messaggi di errore con lo stesso nome.  
  
 **TransferAllErrorMessages**  
 Indicare se l'attività deve copiare dal server di origine al server di destinazione tutti i messaggi di errore definiti dall'utente o solo quelli specificati.  
  
 Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente:  
  
|valore|Description|  
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
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Attività di Integration Services](control-flow/integration-services-tasks.md)   
 [Errore di Editor attività Trasferisci messaggi &#40;pagina Generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Gestione connessione SMO](connection-manager/smo-connection-manager.md)   
 [Errore di Editor attività Trasferisci messaggi &#40;pagina Generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Gestione connessione SMO](connection-manager/smo-connection-manager.md)  
  
  
