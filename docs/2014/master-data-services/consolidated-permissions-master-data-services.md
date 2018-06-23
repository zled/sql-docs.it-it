---
title: Consolidati autorizzazioni (Master Data Services) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a0436df9a9aa4f21d9a581172e2874ca2dad6aa6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156244"
---
# <a name="consolidated-permissions-master-data-services"></a>Autorizzazioni consolidate (Master Data Services)
  Le autorizzazioni consolidate si applicano ai valori di attributo per tutti i membri consolidati di un'entità.  
  
 Le autorizzazioni consolidate si applicano solo alle entità abilitate per gerarchie esplicite e raccolte.  
  
 **Note:**  
  
-   Le autorizzazioni foglia si applicano solo all'area funzionale **Visualizzatore** dell'interfaccia utente.  
  
-   Le autorizzazioni assegnate agli attributi **Name** e **Code** non sono applicate.  
  
|Autorizzazione|Description|  
|----------------|-----------------|  
|**Sola lettura**|I membri consolidati vengono visualizzati, ma l'utente non può aggiungerli, rimuoverli o modificarli.|  
|**Update**|I membri consolidati vengono visualizzati e l'utente può aggiungerli, rimuoverli e modificarli.|  
|**Nega**|I membri consolidati per l'entità non vengono visualizzati.|  
  
## <a name="attribute-permissions"></a>Autorizzazioni per attributi  
 Le autorizzazioni per gli attributi si applicano ai valori degli attributi per l'entità specifica. Gli utenti che dispongono solo delle autorizzazioni per gli attributi non possono aggiungere o rimuovere membri.  
  
|Autorizzazione|Description|  
|----------------|-----------------|  
|**Sola lettura**|L'attributo viene visualizzato, ma l'utente non può modificare i valori di attributo.|  
|**Update**|L'attributo viene visualizzato e l'utente può modificare i valori di attributo.|  
|**Nega**|L'attributo non viene visualizzato.<br /><br /> Nota: non è possibile negare in modo esplicito l'accesso agli attributi Name e Code.|  
  
## <a name="see-also"></a>Vedere anche  
 [Assegnare autorizzazioni per oggetti modello &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Le autorizzazioni foglia &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [Autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Membri &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Gli attributi &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  