---
title: Approvazione necessaria (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b475a53d-269d-49f3-bb42-965c555f80be
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 4a17efe43d5690ab7afc89c13371a3c79064ae86
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35411373"
---
# <a name="approval-required-master-data-services"></a>Approvazione necessaria (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]l'amministratore può impostare un'entità su Approvazione necessaria. Tutte le modifiche all'entità richiedono l'esame e l'approvazione delle modifiche da parte di uno degli amministratori dell'entità.  
  
> [!NOTE]  
>  Le modifiche apportate ai membri foglia richiedono l'approvazione. Le modifiche apportate alle raccolte e alle gerarchie esplicite deprecate non richiedono l'approvazione.  
>   
>  Le modifiche apportate al processo della tabella di staging non richiedono l'approvazione.  
>   
>  Le modifiche apportate da una regola business non richiedono l'approvazione.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessaria l'autorizzazione per accedere all'area funzionale Amministrazione sistema  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)  
  
-   Deve essere presente un'entità. Per altre informazioni, vedere [Creare un'entità &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)  
  
## <a name="to-enable-approval-required-for-an-entity"></a>Per abilitare Approvazione necessaria per un'entità  
  
1.  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modelli** selezionare un modello dalla griglia e quindi fare clic su **Entità**.  
  
3.  Dalla griglia della pagina **Gestisci entità** selezionare la riga per l'entità per cui si vuole abilitare  **Approvazione necessaria** .  
  
4.  Fare clic su **Modifica**, selezionare **Approvazione necessaria**, quindi scegliere **Salva**.  
  
## <a name="see-also"></a>Vedere anche  
 [Insiemi di modifiche &#40;Master Data Services&#41;](../master-data-services/changesets-master-data-services.md)  
  
  
