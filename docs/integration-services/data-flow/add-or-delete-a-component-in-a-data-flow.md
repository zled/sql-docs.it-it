---
title: Aggiungere o eliminare un componente in un flusso di dati | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- adding components
- components [Integration Services], data flow
ms.assetid: d99124f9-0994-4f40-a48e-fdca6a4383e7
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a47b31037882b737992fd42d8b8660459279b06f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="add-or-delete-a-component-in-a-data-flow"></a>Aggiunta o eliminazione di un componente in un flusso di dati
  I componenti dei flussi di dati sono le origini, le destinazioni e le trasformazioni incluse in un flusso di dati. È possibile aggiungere componenti a un flusso di dati solo se il flusso di controllo del pacchetto include un'attività Flusso di dati.  
  
 Nelle procedure seguenti viene descritto come aggiungere o eliminare un componente nel flusso di dati di un pacchetto.  
  
### <a name="to-add-a-component-to-a-data-flow"></a>Per aggiungere un componente a un flusso di dati  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo** e quindi fare doppio clic sull'attività Flusso di dati che contiene il flusso di dati al quale si vuole aggiungere un componente.  
  
4.  Nella casella degli strumenti espandere **Origini flusso di dati**, **Trasformazioni flusso di dati**o **Destinazioni flusso di dati**e quindi trascinare un elemento flusso di dati nell'area di progettazione della scheda **Flusso di dati** .  
  
5.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
### <a name="to-delete-a-component-from-a-data-flow"></a>Per eliminare un componente da un flusso di dati  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo** e quindi fare doppio clic sull'attività Flusso di dati che contiene il flusso di dati dal quale si vuole eliminare un componente.  
  
4.  Fare clic con il pulsante destro del mouse sul componente flusso di dati e quindi scegliere **Elimina**.  
  
5.  Confermare l'eliminazione.  
  
6.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione di componenti in un flusso di dati](../../integration-services/data-flow/connect-components-in-a-data-flow.md)   
 [Debug di un flusso di dati](../../integration-services/troubleshooting/debugging-data-flow.md)   
 [Flusso di dati](../../integration-services/data-flow/data-flow.md)  
  
  
