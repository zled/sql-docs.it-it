---
title: Gestione connessione MSMQ | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: connection-manager
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5a5dee5322e197d46cbdab5911f2e93bf34df4af
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="msmq-connection-manager"></a>gestione connessione MSMQ
  Una gestione connessione MSMQ consente la connessione di un pacchetto a una coda di messaggi che utilizza MSMQ (Message Queuing, Accodamento messaggi). Questa gestione connessione è usata dall'attività Message Queue inclusa in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Quando si aggiunge una gestione connessione MSMQ a un pacchetto, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una gestione connessione che in fase di esecuzione verrà risolta in una connessione MSMQ, imposta le proprietà di tale gestione connessione, quindi la aggiunge alla raccolta **Connections** del pacchetto. La proprietà **ConnectionManagerType** della gestione connessione viene impostata su **MSMQ**.  
  
 Per configurare la gestione connessione MSMQ, procedere nel modo seguente:  
  
-   Specificare una stringa di connessione.  
  
-   Specificare il percorso della coda di messaggi a cui connettersi.  
  
 Il formato del percorso dipende dal tipo di coda, come illustrato nella tabella seguente.  
  
|Tipo di coda|Percorso di esempio|  
|----------------|-----------------|  
|Pubblico|\<nome computer>\\<nome della coda\>|  
|Privato|\<nome computer>\Private$\\\<nome della coda\>|  
  
 Per rappresentare il computer locale è possibile utilizzare un punto (.).  
  
## <a name="configuration-of-the-msmq-connection-manager"></a>Configurazione della gestione connessione MSMQ  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vedere [Editor gestione connessione MSMQ](../../integration-services/connection-manager/msmq-connection-manager-editor.md).  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di programmazione, vedere l'articolo relativo a <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [Aggiunta di connessioni a livello di programmazione](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="msmq-connection-manager-editor"></a>Editor gestione connessione MSMQ
  Usare la finestra di dialogo **Gestione connessione MSMQ** per specificare il percorso di una coda di messaggi di Microsoft Message Queuing (noto anche come MSMQ).  
  
 Per ulteriori informazioni sulla gestione connessione MSMQ, vedere [MSMQ Connection Manager](../../integration-services/connection-manager/msmq-connection-manager.md).  
  
> [!NOTE]  
>  Gestione connessione MSMQ supporta le code pubbliche e private locali, nonché le code pubbliche remote. Non supporta le code private remote. Per una soluzione alternativa che utilizza l'attività Script, vedere [Sending to a Remote Private Message Queue with the Script Task](../../integration-services/extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md).  
  
### <a name="options"></a>Opzioni  
 **Nome**  
 Consente di specificare un nome univoco per la gestione della connessione MSMQ nel flusso di lavoro. Il nome specificato verrà visualizzato in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 **Descrizione**  
 Consente di aggiungere una descrizione per la gestione connessione. È consigliabile includere nella descrizione informazioni sugli scopi della gestione connessione, in modo da ottenere pacchetti autodocumentati e semplificarne quindi la gestione.  
  
 **Percorso**  
 Digitare il percorso completo della coda di messaggi. Il formato del percorso dipende dal tipo di coda.  
  
|Tipo di coda|Percorso di esempio|  
|----------------|-----------------|  
|Pubblico|\<nome computer>\\<nome della coda\>|  
|Privato|\<nome computer>\Private$\\\<nome della coda\>|  
  
 Per rappresentare il computer locale è possibile utilizzare ".".  
  
 **Test**  
 Dopo aver configurato la gestione connessione MSMQ, verificare che la connessione può essere stabilita facendo clic su **Test**.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività Message Queue](../../integration-services/control-flow/message-queue-task.md)   
 [Connessioni in Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
