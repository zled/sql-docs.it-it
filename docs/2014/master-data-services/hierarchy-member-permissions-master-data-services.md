---
title: Autorizzazioni dei membri della gerarchia (Master Data Services) | Microsoft Docs
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
- members [Master Data Services], permissions
- permissions [Master Data Services], members
ms.assetid: b3880eed-1bf6-4f65-ab23-b08c194cc858
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e5ac17b8e72209a25c1e8e213d775012e800ca35
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067621"
---
# <a name="hierarchy-member-permissions-master-data-services"></a>Autorizzazioni membri gerarchie (Master Data Services)
  Le autorizzazioni membri gerarchia sono facoltative e devono essere utilizzate solo quando si desidera che un utente abbia accesso limitato a membri specifici. Se non si assegnano autorizzazioni nella scheda **Membri gerarchia** , le autorizzazioni dell'utente sono basate esclusivamente su quelle assegnate nella scheda **Modelli** .  
  
 Le autorizzazioni dei membri della gerarchia vengono assegnate nell'area funzionale [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Autorizzazioni utenti e gruppi **della scheda** Membri gerarchia **nell'interfaccia utente di** . Queste autorizzazioni determinano a quali membri può accedere un utente nell'area funzionale **Esplora** dell'interfaccia utente.  
  
 Nella scheda **Membri gerarchia** ogni gerarchia è rappresentata come albero. Quando si assegna un'autorizzazione a un nodo dell'albero, tutti i figli la ereditano, a meno che non sia stato assegnata in modo esplicito a un livello inferiore.  
  
> [!NOTE]  
>  Quando si assegna un'autorizzazione a un nodo di una gerarchia, a tutti i membri inclusi negli altri nodi dello stesso livello o di un livello superiore l'autorizzazione viene negata.  
  
 In **Esplora**le autorizzazioni per i membri vengono applicate in tutte le posizioni in cui il membro viene visualizzato. Ad esempio, un membro con **readonly** l'autorizzazione è di sola lettura a qualsiasi entità, gerarchie e raccolte a cui appartiene.  
  
 Le autorizzazioni membri gerarchia si applicano alla versione del modello cui sono assegnate e a eventuali copie future della versione. Non si applicano a versioni precedenti a quella a cui sono assegnate.  
  
|Autorizzazione|Description|  
|----------------|-----------------|  
|**Sola lettura**|I membri vengono visualizzati, ma l'utente non può modificarli. L'utente non può inoltre spostare i membri in qualsiasi gerarchia o raccolta esplicita cui essi appartengono.<br /><br /> Nota: Se si assegna **Read-only** delle autorizzazioni necessarie per **radice**, i membri in **radice** sono di sola lettura; tuttavia, nelle gerarchie esplicite e raccolte, l'utente può spostare membri da **radice** e aggiungere nuovi membri a **radice**.|  
|**Update**|I membri vengono visualizzati e l'utente può modificarli. L'utente può inoltre spostare i membri in qualsiasi gerarchia o raccolta esplicita cui essi appartengono.|  
|**Nega**|I membri non vengono visualizzati.|  
  
 Nella scheda **Membri gerarchia** le autorizzazioni assegnate non vengono applicate immediatamente. La frequenza con cui le autorizzazioni vengono applicate dipende dall'**impostazione relativa all'intervallo di elaborazione della sicurezza dei membri** nella tabella Impostazioni sistema del database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . È possibile applicare immediatamente autorizzazioni di membri seguendo i passaggi descritti in [Immediately Apply Member Permissions &#40;Master Data Services&#41;](immediately-apply-member-permissions-master-data-services.md).  
  
> [!NOTE]  
>  Non è possibile assegnare autorizzazioni membri gerarchie a gerarchie ricorsive, gerarchie derivate con estremità esplicite e a gerarchie derivate con livelli nascosti.  
  
## <a name="possible-overlapping-permissions"></a>Possibili autorizzazioni sovrapposte  
 Quando si assegnano autorizzazioni ai membri, è possibile che sia necessario risolvere eventuali autorizzazioni sovrapposte.  
  
### <a name="when-a-member-belongs-to-multiple-hierarchies"></a>Quando un membro appartiene a più gerarchie  
 Due o più gerarchie possono contenere lo stesso membro.  
  
-   Se un nodo della gerarchia viene assegnato **aggiornamento** autorizzazione e un altro viene assegnata **Read-only**, i membri nel nodo **Read-only**.  
  
-   Se un nodo della gerarchia viene assegnato **aggiornamento** o **Read-only** autorizzazione e un altro nodo vengono assegnate **Deny**, quindi non vengono visualizzati i membri del nodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Assegnare autorizzazioni membri gerarchia &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Modo in cui vengono determinate le autorizzazioni &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Membri &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Gerarchie &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchies-master-data-services.md)   
 [Applicare immediatamente autorizzazioni membri &#40;Master Data Services&#41;](immediately-apply-member-permissions-master-data-services.md)  
  
  