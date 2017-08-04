---
title: Modello di autorizzazioni (Master Data Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8e54b1bd5e60c600e2447f37bdcf77e6f811e869
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="model-permissions-master-data-services"></a>Autorizzazioni per i modelli (Master Data Services)
  Le autorizzazioni per i modelli si applicano a tutte le entità, alle gerarchie derivate, alle gerarchie esplicite e alle raccolte esistenti all'interno del modello. È possibile eseguire l'override delle autorizzazioni assegnate al modello per qualsiasi singolo oggetto.  
  
> [!NOTE]  
>  Se un utente è un amministratore di modelli, il modello viene visualizzato in tutte le aree funzionali dell'interfaccia utente. In caso contrario, il modello viene visualizzato solo nell'area funzionale **Visualizzatore**. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
|Autorizzazione|Description|  
|----------------|-----------------|  
|**Lettura**|L'utente può leggere i membri, gli attributi, le appartenenze a gerarchie o le appartenenze a raccolte.|  
|**Create**|L'utente può creare i membri e assegnare i valori di attributo durante la creazione.|  
|**Update**|L'utente può aggiornare i membri, gli attributi, le appartenenze a gerarchie o le appartenenze a raccolte.|  
|**Elimina**|L'utente può eliminare i membri|  
|**Nega**|Negare l'accesso al modello|  
|**Amministrativi**|Autorizzazione dell'amministratore per il modello. L'autorizzazione di amministratore è disponibile solo al livello del modello.|  
  
 Le autorizzazioni di lettura, creazione, aggiornamento ed eliminazione possono essere combinate. Quando vengono assegnate le autorizzazioni di creazione, aggiornamento ed eliminazione, l'autorizzazione di lettura viene assegnata automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Assegnare autorizzazioni per oggetti modello &#40; Master Data Services &#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Autorizzazioni per oggetti modello &#40; Master Data Services &#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Autorizzazioni per entità &#40; Master Data Services &#41;](../master-data-services/entity-permissions-master-data-services.md)   
 [Le autorizzazioni della raccolta &#40; Master Data Services &#41;](../master-data-services/collection-permissions-master-data-services.md)  
  
  
