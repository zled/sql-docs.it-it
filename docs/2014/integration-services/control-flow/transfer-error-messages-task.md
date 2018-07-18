---
title: Attività Trasferisci messaggi di errore | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.f1
helpviewer_keywords:
- Transfer Error Messages task [Integration Services]
ms.assetid: da702289-035a-4d14-bd74-04461fbfee1b
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2d7a40c86c0dba2a4b2db08305f7fea379a97b1f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201851"
---
# <a name="transfer-error-messages-task"></a>Attività Trasferisci messaggi di errore
  L'attività Trasferisci messaggi di errore trasferisce uno o più messaggi di errore definiti dall'utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tra istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I messaggi definiti dall'utente sono messaggi con un identificatore che è uguale o maggiore di 50000. I messaggi con identificatore minore di 50000 sono messaggi di errore di sistema e non possono essere trasferiti utilizzando l'attività Trasferisci messaggi di errore.  
  
 È possibile configurare l'attività Trasferisci messaggi di errore per il trasferimento di tutti i messaggi di errore o dei soli messaggi di errore specificati. I messaggi di errore definiti dall'utente possono essere disponibili in lingue diverse. È possibile configurare l'attività per il trasferimento dei soli messaggi nelle lingue selezionate. È necessario che nel server di destinazione sia inclusa la versione del messaggio che utilizza la tabella codici 1033, corrispondente all'inglese americano, per poter trasferire su tale server versioni del messaggio in altre lingue.  
  
 La tabella sysmessages del database master contiene tutti i messaggi di errore, sia di sistema che definiti dall'utente, utilizzati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 I messaggi definiti dall'utente da trasferire potrebbero essere già presenti nella destinazione. Un messaggio di errore è considerato duplicato se l'identificatore e la lingua corrispondono a quelli di un messaggio di errore esistente. È possibile configurare l'attività Trasferisci messaggi di errore per la gestione dei messaggi di errore duplicati nei modi seguenti:  
  
-   I messaggi di errore duplicati vengono sovrascritti.  
  
-   In presenza di messaggi di errore duplicati l'attività ha esito negativo.  
  
-   I messaggi di errore duplicati vengono ignorati.  
  
 In fase di esecuzione l'attività Trasferisci messaggi di errore si connette al server di origine e al server di destinazione utilizzando una o più gestioni connessioni SMO. Le gestioni connessioni SMO vengono configurate separatamente dall'attività Trasferisci messaggi di errore, che tuttavia vi fa riferimento. Le gestioni connessioni SMO specificano il server e la modalità di autenticazione da adottare per l'accesso al server. Per altre informazioni, vedere [Gestione connessione SMO](../connection-manager/smo-connection-manager.md).  
  
 L'attività Trasferisci messaggi di errore supporta un'origine e una destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Non esiste alcuna limitazione relativamente alla versione da utilizzare come origine o destinazione.  
  
## <a name="events"></a>Eventi  
 L'attività Trasferisci messaggi di errore genera un evento informativo in cui è indicato il numero di messaggi di errore trasferiti.  
  
 Non viene riportato lo stato incrementale del trasferimento, ma solo il completamento 0% e 100%.  
  
## <a name="execution-value"></a>Valore di esecuzione  
 Il valore di esecuzione, definito nella proprietà `ExecutionValue` dell'attività, restituisce il numero di messaggi di errore trasferiti. Tramite l'assegnazione di una variabile definita dall'utente per il `ExecValueVariable` proprietà del messaggio di errore di trasferimento attività, informazioni sul trasferimento di messaggio di errore possono essere rese disponibili ad altri oggetti nel pacchetto. Per altre informazioni, vedere [Variabili di Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md) e [Utilizzo di variabili nei pacchetti](../use-variables-in-packages.md).  
  
## <a name="log-entries"></a>Voci di log  
 L'attività Trasferisci messaggi di errore include le voci di log personalizzate seguenti:  
  
-   TransferErrorMessagesTaskStartTransferringObjects    Indica che il trasferimento è iniziato. La voce di log include l'ora di inizio.  
  
-   TransferErrorMessagesTaskFinishedTransferringObjects    Indica che il trasferimento è stato completato. La voce di log include l'ora di fine.  
  
 Inoltre, una voce di log per il `OnInformation` indica il numero di messaggi di errore che sono stati trasferiti e una voce di log per il `OnWarning event` è stata scritta per ogni messaggio di errore nella destinazione viene sovrascritto.  
  
## <a name="security-and-permissions"></a>Sicurezza e autorizzazioni  
 Per poter creare messaggi di errore, l'utente che esegue il pacchetto deve essere un membro del ruolo del server sysadmin o serveradmin nel server di destinazione.  
  
## <a name="configuration-of-the-transfer-error-messages-task"></a>Configurazione dell'attività Trasferisci messaggi di errore  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic su uno degli argomenti seguenti:  
  
-   [Errore di Editor attività Trasferisci messaggi &#40;pagina Generale&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Errore di Editor attività Trasferisci messaggi &#40;pagina di messaggi&#41;](../transfer-error-messages-task-editor-messages-page.md)  
  
-   [Pagina Espressioni](../expressions/expressions-page.md)  
  
 Per informazioni sull'impostazione di queste proprietà a livello di codice, fare clic sull'argomento seguente:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferErrorMessagesTask.TransferErrorMessagesTask>  
  
## <a name="related-tasks"></a>Related Tasks  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostare le proprietà di un'attività o di un contenitore](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di Integration Services](integration-services-tasks.md)   
 [Flusso di controllo](control-flow.md)  
  
  
