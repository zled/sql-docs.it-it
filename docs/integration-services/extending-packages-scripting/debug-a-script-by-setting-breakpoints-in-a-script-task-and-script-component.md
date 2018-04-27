---
title: Eseguire il debug di uno script impostando punti di interruzione in un'attività e in un componente Script | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: extending-packages-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 31a023d2c2534e1137f51ef37c068e1d4e6e1bd8
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a>Eseguire il debug di uno script impostando punti di interruzione in un'attività e in un componente Script
  In questa procedura viene descritto come impostare i punti di interruzione negli script utilizzati nell'attività e nel componente Script.  
  
 Dopo aver impostato i punti di interruzione nello script, nella finestra di dialogo **Imposta punti di interruzione - \<nome oggetto>** vengono elencati i punti di interruzione insieme a quelli predefiniti.  
  
> [!IMPORTANT]  
>  In determinate circostanze, i punti di interruzione nell'attività Script e il componente Script vengono ignorati. Per altre informazioni, vedere la sezione **Debug dell'attività Script** in [Scrittura di codice e debug dell'attività Script](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md) e la sezione **Debug del componente script** in [Codifica e debug del componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="to-set-a-breakpoint-in-script"></a>Per impostare un punto di interruzione in uno script  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  Fare doppio clic sul pacchetto che include lo script in cui si desidera impostare i punti di interruzione.  
  
3.  Per aprire l'attività Script, fare clic sulla scheda **Flusso di controllo**, quindi fare doppio clic sull'attività.  
  
4.  Per aprire il componente Script, fare clic sulla scheda **Flusso di dati**, quindi fare doppio clic sul componente.  
  
5.  Fare clic su **Script**, quindi su **Modifica script**.  
  
6.  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) individuare la riga di script in cui si desidera impostare un punto di interruzione, fare clic con il pulsante destro del mouse sulla riga, scegliere **Punto di interruzione**, quindi fare clic su **Inserisci punto di interruzione**.  
  
     Nella riga di codice verrà visualizzata l'icona del punto di interruzione.  
  
7.  Scegliere **Esci** dal menu **File**.  
  
8.  Fare clic su **OK**.  
  
9. Per salvare il pacchetto, scegliere **Salva elementi selezionati** dal menu **File** .  
  
  
