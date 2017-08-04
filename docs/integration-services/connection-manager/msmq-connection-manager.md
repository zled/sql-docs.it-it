---
title: Gestione connessione MSMQ | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2a3eabde204f3629f903e66da5b4b0204a49ccd7
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

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
|Pubblico|\<nome computer >\\< nome della coda\>|  
|Privato|\<nome computer > \Private$\\< nome della coda\>|  
  
 Per rappresentare il computer locale è possibile utilizzare un punto (.).  
  
## <a name="configuration-of-the-msmq-connection-manager"></a>Configurazione della gestione connessione MSMQ  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vedere [Editor gestione connessione MSMQ](../../integration-services/connection-manager/msmq-connection-manager-editor.md).  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di programmazione, vedere <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [Aggiunta di connessioni a livello di programmazione](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività Message Queue](../../integration-services/control-flow/message-queue-task.md)   
 [Integration Services &#40; SSIS &#41; Connessioni](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
