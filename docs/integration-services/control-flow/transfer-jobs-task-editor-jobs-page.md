---
title: "Editor attività Trasferisci processi (pagina processi) | Documenti Microsoft"
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
- sql13.dts.designer.transferjobstask.jobs.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5efb3b22c8cb6849b5a70423cfd4b51b45c21686
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="transfer-jobs-task-editor-jobs-page"></a>Editor attività Trasferisci processi (pagina Processi)
  Utilizzare la pagina **Processi** della finestra di dialogo **Editor attività Trasferisci processi** per specificare le proprietà relative alla copia di uno o più processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent tra due istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per ulteriori informazioni sull'attività Trasferisci processi, vedere [Transfer Jobs Task](../../integration-services/control-flow/transfer-jobs-task.md).  
  
> [!NOTE]  
>  Per accedere ai processi nel server di origine, l'utente deve essere un membro almeno del ruolo predefinito del database **SQLAgentUserRole** nel server. Per creare processi nel server di destinazione, l'utente deve essere un membro del ruolo predefinito del server **sysadmin** o di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Per altre informazioni sui ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e sulle relative autorizzazioni, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
## <a name="options"></a>Opzioni  
 **SourceConnection**  
 Selezionare una gestione connessione SMO nell'elenco oppure fare clic su  **\<nuova connessione >** per creare una nuova connessione al server di origine.  
  
 **DestinationConnection**  
 Selezionare una gestione connessione SMO nell'elenco oppure fare clic su  **\<nuova connessione >** per creare una nuova connessione al server di destinazione.  
  
 **TransferAllJobs**  
 Indicare se l'attività deve copiare dal server di origine nel server di destinazione tutti i processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent o solo quelli specificati.  
  
 Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente:  
  
|Valore|Description|  
|-----------|-----------------|  
|**True**|Copia tutti i processi.|  
|**False**|Copia solo i processi specificati.|  
  
 **JobsList**  
 Fare clic sul pulsante con i puntini di sospensione **(…)** per selezionare i processi da copiare. È necessario selezionare almeno un processo.  
  
> [!NOTE]  
>  Prima di selezionare i processi da copiare, specificare la proprietà **SourceConnection** .  
  
 Quando la proprietà **TransferAllJobs** è impostata su **True** , l'opzione **JobsList**non è disponibile.  
  
 **IfObjectExists**  
 Indicare la modalità con cui l'attività deve gestire i processi che hanno lo stesso nome di processi già esistenti nel server di destinazione.  
  
 Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente:  
  
|Valore|Description|  
|-----------|-----------------|  
|**FailTask**|L'attività viene interrotta se nel server di destinazione esistono processi con lo stesso nome.|  
|**Overwrite**|L'attività sovrascrive i processi con lo stesso nome che si trovano nel server di destinazione.|  
|**Skip**|L'attività ignora i processi con lo stesso nome che si trovano nel server di destinazione.|  
  
 **EnableJobsAtDestination**  
 Specificare se i processi copiati nel server di destinazione devono essere attivati.  
  
 Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente:  
  
|Valore|Description|  
|-----------|-----------------|  
|**True**|Attiva i processi nel server di destinazione.|  
|**False**|Disabilita i processi nel server di destinazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../integration-services/integration-services-error-and-message-reference.md)   
 [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Editor attività processi di trasferimento &#40; Pagina generale &#41;](../../integration-services/control-flow/transfer-jobs-task-editor-general-page.md)   
 [Pagina espressioni](../../integration-services/expressions/expressions-page.md)   
 [Gestione connessione SMO](../../integration-services/connection-manager/smo-connection-manager.md)  
  
  
