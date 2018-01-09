---
title: Prospettive nei modelli multidimensionali | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default members
- hiding objects from perspective
- renaming perspectives
- attributes [Analysis Services], default members
- removing perspectives
- perspectives [Analysis Services]
- names [Analysis Services], perspectives
- cubes [Analysis Services], perspectives
- deleting perspectives
ms.assetid: 5a3d6577-6833-4c24-820c-b65bb856157b
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 94508cf2bb7347d3b8cef15ce5c743f33c04a018
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="perspectives-in-multidimensional-models"></a>Prospettive nei modelli multidimensionali
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Una prospettiva è un subset di un cubo creato per una particolare applicazione o un gruppo di utenti. La prospettiva predefinita è costituita dal cubo. Una prospettiva viene esposta a un client come un cubo. Quando viene visualizzata da un utente, una prospettiva si presenta come un altro cubo. Qualsiasi modifica apportata ai dati del cubo tramite writeback nella prospettiva viene apportata al cubo originale. Per altre informazioni sulle viste in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [Prospettive](../../analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives.md).  
  
 Usare la scheda **Prospettive** di Progettazione cubi per creare o modificare prospettive in un cubo. Nella prima colonna **Oggetti cubo** della scheda **Prospettive** sono elencati tutti gli oggetti del cubo. Corrisponde alla prospettiva predefinita per il cubo, costituita dal cubo stesso.  
  
## <a name="creating-or-deleting-perspectives"></a>Creazione o eliminazione di prospettive  
 È possibile aggiungere una prospettiva alla scheda **Prospettive** scegliendo **Nuova prospettiva** dal menu **Cubo** . È anche possibile fare clic sul pulsante **Nuova prospettiva** sulla barra degli strumenti oppure fare clic con il pulsante destro del mouse in un punto qualsiasi del riquadro e quindi scegliere **Nuova prospettiva** dal menu di scelta rapida. A un cubo può essere aggiunto qualsiasi numero di prospettive.  
  
 Per rimuovere una prospettiva, fare innanzitutto clic su qualsiasi cella della colonna per la prospettiva che si desidera eliminare. Scegliere quindi **Elimina prospettiva** dal menu **Cubo**. È anche possibile fare clic sul pulsante **Elimina prospettiva** sulla barra degli strumenti oppure fare clic con il pulsante destro del mouse su qualsiasi cella della prospettiva che si desidera eliminare e quindi scegliere **Elimina prospettiva** dal menu di scelta rapida.  
  
## <a name="renaming-perspectives"></a>ridenominazione di prospettive  
 Nella prima riga di ogni prospettiva ne viene visualizzato il nome. Quando si crea una prospettiva, il nome corrisponde inizialmente a "Prospettiva", seguito da un numero ordinale a partire da 1 se è già presente una prospettiva denominata "Prospettiva". È possibile fare clic sul nome per modificarlo.  
  
## <a name="hiding-objects-from-a-perspective"></a>Come nascondere oggetti in una prospettiva  
 Per nascondere un oggetto in una prospettiva, deselezionare la casella di controllo nella riga corrispondente all'oggetto della colonna per la prospettiva. In una prospettiva possono essere nascosti gli oggetti del cubo seguenti:  
  
-   Gruppi di misure  
  
-   Misure  
  
-   Dimensioni  
  
-   Gerarchie  
  
-   Set denominati  
  
-   KPI  
  
-   Azioni  
  
-   Membri calcolati  
  
 Per visualizzare qualsiasi oggetto, espandere la categoria (**Gruppi di misure**, **Dimensioni**, **KPI**, **Calcoli**o **Azioni**) per qualsiasi tipo di oggetto in **Oggetti cubo**. Per visualizzare le gerarchie o gli attributi di una dimensione, espandere innanzitutto una dimensione e quindi la riga **Gerarchie** o **Attributi** . Per visualizzare le misure in un gruppo di misure, espandere il gruppo di misure.  
  
## <a name="see-also"></a>Vedere anche  
 [Cubi nei modelli multidimensionali](../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)  
  
  
