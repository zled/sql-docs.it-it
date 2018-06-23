---
title: Editor gestione connessione MSMQ | Documenti Microsoft
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
- sql12.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- MSMQ Connection Manager Editor
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 43db2e4e5da787c5c0e17b788c6c3bb818f1a1d9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156971"
---
# <a name="msmq-connection-manager-editor"></a>Editor gestione connessione MSMQ
  Usare la finestra di dialogo **Gestione connessione MSMQ** per specificare il percorso di una coda di messaggi di Microsoft Message Queuing (noto anche come MSMQ).  
  
 Per ulteriori informazioni sulla gestione connessione MSMQ, vedere [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md).  
  
> [!NOTE]  
>  Gestione connessione MSMQ supporta le code pubbliche e private locali, nonché le code pubbliche remote. Non supporta le code private remote. Per una soluzione alternativa che utilizza l'attività Script, vedere [Sending to a Remote Private Message Queue with the Script Task](control-flow/script-task.md).  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Consente di specificare un nome univoco per la gestione della connessione MSMQ nel flusso di lavoro. Il nome specificato verrà visualizzato in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
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
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  