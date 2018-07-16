---
title: Convalidare membri specifici rispetto a regole business (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 9f3a3c6f4c812c5fc68479ef8ed3499a9e02b386
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37314061"
---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a>Convalidare membri specifici rispetto a regole business (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]è opportuno applicare selettivamente regole business quando si desidera aggiornare o convalidare subset di membri rispetto a regole business.  
  
> [!NOTE]  
>  Per applicare le regole di business a tutti i membri in una versione di un modello, vedere [Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
-   È necessario disporre almeno dell'autorizzazione **Update** per l'oggetto modello al quale vengono applicate le regole di business.  
  
### <a name="to-apply-business-rules-selectively"></a>Per applicare regole business selettivamente  
  
1.  Nella home page di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] selezionare un modello nell'elenco **Modello** .  
  
2.  Selezionare una versione dall'elenco **Versione** .  
  
3.  Fare clic su **Esplora**.  
  
4.  Scegliere **Entità** dalla barra dei menu, quindi fare clic sul nome dell'entità contenente i membri a cui applicare le regole.  
  
5.  Fare clic su **Applica regole business**. Le regole business sono applicate solo ai membri visualizzati nella griglia.  
  
## <a name="see-also"></a>Vedere anche  
 [Convalidare una versione rispetto alle regole Business &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md)   
 [Le regole di business &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
