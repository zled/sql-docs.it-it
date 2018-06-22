---
title: Seleziona metodo di creazione (Creazione guidata cubo) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubewizard.cubedefinition.f1
ms.assetid: 985d3b5b-7891-465b-862d-f7e75431b342
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b99ea0d73d9d24992af5fcac09d8df3f4d71fafd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064530"
---
# <a name="select-creation-method-cube-wizard"></a>Seleziona metodo di creazione (Creazione guidata cubo)
  Utilizzare la pagina **Seleziona metodo di creazione** per specificare la modalità di creazione del cubo.  
  
## <a name="options"></a>Opzioni  
 **Usa tabelle esistenti**  
 Selezionare per creare un cubo utilizzando le tabelle esistenti in un'origine dati. La procedura guidata descriverà dettagliatamente il processo di selezione e definizione dei gruppi di misure e delle dimensioni in base alle tabelle esistenti per compilare il cubo nuovo.  
  
 **Crea un cubo vuoto**  
 Selezionare per creare un cubo vuoto. Questa opzione è utile per creare tutto manualmente o quando tutti i gruppi di misure nel cubo sono gruppi di misure collegati.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo quando si lavora a un progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] e non quando si è connessi direttamente a un database [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 **Genera tabelle nell'origine dei dati**  
 Selezionare per creare prima un cubo e quindi generare tabelle nuove nell'origine dati in base alla definizione del cubo.  
  
> [!NOTE]  
>  Per utilizzare questa opzione, si deve disporre delle autorizzazioni per creare gli oggetti nell'origine dei dati sottostante.  
  
 La selezione di questa opzione renderà disponibile l'opzione **Modello** .  
  
 **Modello**  
 Selezionare il modello che si desidera utilizzare per creare il cubo. I modelli offrono un set completo di definizioni orientate ad applicazioni aziendali specifiche.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo quando l'opzione viene selezionata l'opzione **Genera tabelle nell'origine dati** .  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti cubo &#40;Analysis Services - dati multidimensionali&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)   
 [Cubi nei modelli multidimensionali](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Dimensioni nei modelli multidimensionali](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  