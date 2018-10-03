---
title: Autorizzazioni per raccolte (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], permissions
- permissions [Master Data Services], collections
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: aa360d47553f539438843ab1872fedc270ac1e99
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47749692"
---
# <a name="collection-permissions-master-data-services"></a>Autorizzazioni per raccolte (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Le autorizzazioni per le raccolte si applicano a tutte le raccolte relative a un'entità. Non è possibile assegnare autorizzazioni a una raccolta specifica. Le autorizzazioni si applicano a tutte le raccolte.  
  
> [!NOTE]  
>  Queste autorizzazioni si applicano solo all'area funzionale **Visualizzatore** dell'interfaccia utente.  
  
|Autorizzazione|Descrizione|  
|----------------|-----------------|  
|**Lettura**|L'utente può leggere i membri della raccolta e gli attributi dei membri.|  
|**Creare**|L'utente può creare i membri della raccolta e assegnare i valori di attributo.|  
|**Update**|L'utente può aggiornare i membri della raccolta, gli attributi e le relazioni.|  
|**Elimina**|L'utente può eliminare membri della raccolta.|  
|**Nega**|L'accesso ai membri della raccolta è negato.|  
  
 Le autorizzazioni di lettura, creazione, aggiornamento ed eliminazione possono essere combinate. Quando vengono assegnate le autorizzazioni di creazione, aggiornamento ed eliminazione, l'autorizzazione di lettura viene assegnata automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Assegnare autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Raccolte &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)   
 [Autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
