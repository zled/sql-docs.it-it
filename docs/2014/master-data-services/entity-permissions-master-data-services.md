---
title: Autorizzazioni per le entità (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 7add4e6562bdfff222bca289af6d7486efe4e8a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193781"
---
# <a name="entity-permissions-master-data-services"></a>Autorizzazioni per le entità (Master Data Services)
  Le autorizzazioni per le entità si applicano a:  
  
-   Tutti gli attributi dell'entità, inclusi **Name** e **Code**, per i membri foglia e i membri consolidati.  
  
-   Tutte le raccolte dell'entità.  
  
-   Appartenenze e relazioni della gerarchia esplicita.  
  
 Quando si dispone delle autorizzazioni per un'entità, è possibile aggiungere e rimuovere membri dall'entità, dalle gerarchie esplicite e dalle raccolte corrispondenti.  
  
> [!NOTE]  
>  Queste autorizzazioni si applicano solo all'area funzionale **Visualizzatore** dell'interfaccia utente.  
  
|Autorizzazione|Description|  
|----------------|-----------------|  
|**Sola lettura**|L'entità viene visualizzata, ma l'utente non può aggiungere, rimuovere o modificare i membri.|  
|**Update**|L'entità viene visualizzata e l'utente può aggiungere, rimuovere e modificare i membri.|  
|**Nega**|L'entità non viene visualizzata.|  
  
## <a name="see-also"></a>Vedere anche  
 [Assegnare autorizzazioni per oggetti modello &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Entità &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)  
  
  
