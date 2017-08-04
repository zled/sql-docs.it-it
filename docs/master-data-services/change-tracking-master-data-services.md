---
title: Rilevamento modifiche (Master Data Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6851da978ab681f0236bc9737e7f628c0089abe0
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="change-tracking-master-data-services"></a>Rilevamento modifiche (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]è possibile utilizzare gruppi rilevamento delle modifiche per eseguire un'azione quando cambia un valore di attributo. Utilizzare il rilevamento modifiche quando non si conosce il nuovo valore, ma si desidera sapere se sono state apportate modifiche.  
  
## <a name="configuring-change-tracking"></a>Configurazione del rilevamento modifiche  
 Per configurare il rilevamento modifiche, aggiungere un attributo a un gruppo rilevamento modifiche. Il gruppo può contenere uno o molti attributi. Creare quindi una regola business per definire l'azione da eseguire quando uno degli attributi del gruppo vengono modificati.  
  
> [!NOTE]  
>  Le regole business del rilevamento modifiche considerano i dati in gestione temporanea (importati) come modificati.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Aggiungere attributi a un gruppo rilevamento modifiche.|[Aggiungere attributi a un gruppo rilevamento modifiche &#40; Master Data Services &#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Creare una regola business per avviare azioni in base alle modifiche apportate agli attributi.|[Inizializzare azioni basate su Cambia valore di attributo &#40; Master Data Services &#41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Convalida &#40; Master Data Services &#41;](../master-data-services/validation-master-data-services.md)  
  
-   [Le regole di business &#40; Master Data Services &#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [Attributi &#40; Master Data Services &#41;](../master-data-services/attributes-master-data-services.md)  
  
  
