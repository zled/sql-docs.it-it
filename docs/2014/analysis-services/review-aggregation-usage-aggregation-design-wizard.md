---
title: Controlla utilizzo aggregazioni (Progettazione guidata aggregazioni) | Documenti Microsoft
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
- sql12.asvs.aggregationdesignwizard.reviewusage.f1
ms.assetid: 107ee872-3df2-4931-b56c-af11e38f6745
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5a26ea23dda5bba4813a9c5a99d797471124750d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158790"
---
# <a name="review-aggregation-usage-aggregation-design-wizard"></a>Controlla utilizzo aggregazioni (Progettazione guidata aggregazioni)
  Utilizzare la pagina **Controlla utilizzo aggregazioni** per configurare le impostazioni di utilizzo delle aggregazioni.  
  
## <a name="options"></a>Opzioni  
 **Default**  
 Selezionare per impostare l'impostazione di utilizzo delle aggregazioni per l'attributo su Predefinito. Con questa impostazione, la progettazione applica una regola predefinita in base al tipo di attributo e di dimensione.  
  
 `Full`  
 Selezionare questa opzione per impostare l'impostazione di utilizzo delle aggregazioni per l'attributo per `Full`. Con questa impostazione, ogni aggregazione per il cubo deve includere questo attributo o un attributo correlato che è a un livello inferiore nella catena dell'attributo. Il `Full` impostazione di utilizzo aggregazioni deve essere evitato quando un attributo contiene molti membri. Se specificata per più attributi o attributi che hanno molti membri, questa impostazione potrebbe impedire la progettazione delle aggregazioni a causa delle dimensioni eccessive.  
  
 **Nessuno**  
 Selezionare per impostare l'impostazione di utilizzo delle aggregazioni per l'attributo in Nessuna. Con questa impostazione nessuna aggregazione del cubo deve includere questo attributo.  
  
 `Unrestricted`  
 Selezionare questa opzione per impostare l'impostazione di utilizzo delle aggregazioni per l'attributo per `Unrestricted`. Con questa impostazione non sono inserite restrizioni nella progettazione delle aggregazioni. Tuttavia, l'attributo ancora deve essere valutato per stabilire se è idoneo.  
  
 **Impostare come predefinito per tutti**  
 Selezionare per impostare le impostazioni  di utilizzo delle aggregazioni per tutti gli attributi su Predefinito.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggregazione progettazione guidata F1 Help](aggregation-design-wizard-f1-help.md)   
 [Procedure guidate di Analysis Services &#40;dati multidimensionali&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  