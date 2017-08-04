---
title: Autorizzazioni (Master Data Services) per oggetti modello | Documenti Microsoft
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
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ee6ede91067d2b358a403458e07af37b2f895ac3
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="model-object-permissions-master-data-services"></a>Autorizzazioni per oggetti modello (Master Data Services)
  Le autorizzazioni per oggetti modello sono obbligatorie. Esse determinano a quali attributi può accedere un utente nell'area funzionale **Visualizzatore** dell'interfaccia utente.  
  
 Ad esempio, se si assegna all'utente un'autorizzazione **Update** per l'entità Product, l'utente può aggiornare tutti gli attributi dell'entità Product. Se si assegna l'autorizzazione **Update** per un singolo attributo, l'utente potrà aggiornare solo quell'attributo.  
  
 Per determinare la sicurezza assegnata su ogni singolo valore di attributo, le autorizzazioni degli oggetti modello vengono combinate alle autorizzazioni dei membri della gerarchia che determinano i membri ai quali un utente può accedere.  
  
 Per concedere a un utente l'accesso a un'area funzionale diversa da **Visualizzatore**, è necessario che l'utente sia un amministratore del modello, il che implica anche l'assegnazione delle autorizzazioni per gli oggetti modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
 Le autorizzazioni degli oggetti modello vengono assegnate nell'area funzionale **Autorizzazioni utenti e gruppi** della scheda **Modelli** nell'interfaccia utente di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . In questa scheda il modello viene rappresentato come struttura ad albero. Quando si assegna un'autorizzazione a un oggetto dell'albero, tutti gli oggetti sottostanti ereditano tale autorizzazione. Per eseguire l'override dell'ereditarietà, è possibile assegnare autorizzazioni ai singoli oggetti.  
  
 È possibile assegnare una combinazione di autorizzazioni di lettura, creazione, aggiornamento ed eliminazione o negare le autorizzazioni per gli oggetti modello. La mancata assegnazione di autorizzazioni nella scheda **Modelli** determina l'impossibilità da parte dell'utente di visualizzare modelli o dati in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="best-practice"></a>Procedura consigliata  
 In generale, è consigliabile assegnare l'autorizzazione **ALL** all'oggetto modello e quindi assegnare in modo esplicito l'autorizzazione agli oggetti sottostanti.  
  
## <a name="external-resources"></a>Risorse esterne  
 Post del blog sui [miglioramenti della sicurezza](http://go.microsoft.com/fwlink/p/?LinkId=615376)su msdn.com.  
  
## <a name="see-also"></a>Vedere anche  
 [Assegnare autorizzazioni per oggetti modello &#40; Master Data Services &#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Modello autorizzazioni &#40; Master Data Services &#41;](../master-data-services/model-permissions-master-data-services.md)   
 [Area funzionale autorizzazioni &#40; Master Data Services &#41;](../master-data-services/functional-area-permissions-master-data-services.md)   
 [Le autorizzazioni membri gerarchia &#40; Master Data Services &#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Determinazione delle autorizzazioni &#40; Master Data Services &#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
