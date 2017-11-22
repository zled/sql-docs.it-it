---
title: Aggiungere un gruppo (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups [Master Data Services], adding
- adding groups [Master Data Services]
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
caps.latest.revision: "7"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a7e0d8aab20d5d92bbc9b74c84d8159bcb560d3d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="add-a-group-master-data-services"></a>Aggiungere un gruppo (Master Data Services)
  Aggiungere un gruppo all'elenco **Gruppi** in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] per iniziare il processo di assegnazione dell'autorizzazione all'applicazione Web. Prima che un utente in un gruppo possa accedere a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], è necessario assegnare l'autorizzazione di gruppo a una o più aree funzionali e oggetti modello.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Autorizzazioni utenti e gruppi** .  
  
### <a name="to-add-a-group"></a>Per aggiungere un gruppo  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Autorizzazioni utenti e gruppi**.  
  
2.  Nella pagina **Utenti** scegliere **Gestisci gruppi**dalla barra dei menu.  
  
3.  Fare clic su **Aggiungi gruppi**.  
  
4.  Digitare il nome del gruppo preceduto dal nome di dominio di Active Directory o dal nome del computer server, come in *dominio\nome_gruppo* o *computer\nome_gruppo*.  
  
5.  Facoltativamente, fare clic su **Controlla nomi**.  
  
6.  Scegliere **OK**.  
  
    > [!NOTE]  
    >  Quando l'utente accede per la prima volta a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], il nome dell'utente viene aggiunto all'elenco di utenti di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   [Assegnare autorizzazioni per aree funzionali &#40;Master Data Services&#41;](../master-data-services/assign-functional-area-permissions-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza &#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md)  
  
  
