---
title: Scheda gestori eventi | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.eventhandlerwindow.f1
ms.assetid: 94fc8916-8032-490c-b9d5-ded8b6217e49
caps.latest.revision: 21
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 83fb3a3e736e91b1c47fa3dffff5bbe9bfa4a940
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203891"
---
# <a name="event-handlers-tab"></a>Scheda Gestori eventi
  Utilizzare la scheda **Gestori eventi** dello strumento Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] per compilare un flusso di controllo in un pacchetto [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Un gestore di evento viene eseguito in risposta a un evento generato dal pacchetto oppure da un'attività o da un contenitore incluso nel pacchetto.  
  
## <a name="options"></a>Opzioni  
 **File eseguibile**  
 Consente di selezionare il file eseguibile per il quale si desidera compilare un gestore di evento. Il file eseguibile può essere il pacchetto oppure un'attività o un contenitore incluso nel pacchetto.  
  
 **Gestore dell'evento**  
 Consente di selezionare un gestore di evento. Creare il gestore di evento trascinando gli elementi dalla **casella degli strumenti**.  
  
 **Elimina**  
 Dopo aver selezionato un gestore di evento, fare clic su **Elimina** per rimuoverlo dal pacchetto.  
  
 **Fare clic qui per creare un \<nome del gestore eventi > per il file eseguibile \<nome eseguibile >**  
 Fare clic per creare il gestore di evento.  
  
 Creare il flusso di controllo trascinando gli oggetti grafici che rappresentano i contenitori e le attività di [!INCLUDE[ssIS](../includes/ssis-md.md)] dalla **casella degli strumenti** all'area di progettazione della scheda **Gestori eventi** e quindi trascinando il connettore per collegare gli oggetti.  
  
 È inoltre possibile fare clic con il pulsante destro del mouse sull'area di progettazione, quindi scegliere **Aggiungi annotazione**dal menu per aggiungere annotazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestori eventi di Integration Services &#40;SSIS&#41;](integration-services-ssis-event-handlers.md)   
 [Flusso di controllo](control-flow/control-flow.md)   
 [Progettazione SSIS](ssis-designer.md)   
 [Integration Services &#40;SSIS&#41; gestori eventi](integration-services-ssis-event-handlers.md)  
  
  
