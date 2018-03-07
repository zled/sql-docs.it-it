---
title: Escludere una regola di business (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules [Master Data Services], excluding
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 19178247823c4fb89b31cb832093dc39faec34df
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="exclude-a-business-rule-master-data-services"></a>Escludere una regola business (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]escludere una regola di business quando non si vuole eliminarla in modo permanente, ma non si vuole convalidare i dati rispetto a essa.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-exclude-a-business-rule"></a>Per escludere una regola business  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Dalla barra dei menu scegliere **Gestisci** e fare clic su **Regole business**.  
  
3.  Nella pagina **Regole business** selezionare un modello nell'elenco a discesa **Modello** .  
  
4.  Nell'elenco a discesa **Entità** selezionare un'entità.  
  
5.  Nell'elenco a discesa **Tipi di membri** selezionare un tipo di membro.  
  
6.  Nella griglia selezionare la riga per la regola di business che si vuole escludere e quindi fare clic su **Modifica**.  
  
7.  Selezionare la casella di controllo **Esclusa** .  
  
8.  Fare clic su **Salva**.  
  
9. Fare clic su **Pubblica tutto**.  
  
10. Nella finestra di dialogo di conferma fare clic su **OK**. Il valore nella colonna **Stato della regola di business** è **Esclusa** e la colonna **Esclusa** è impostata su **Sì**.  
  
## <a name="see-also"></a>Vedere anche  
 [Eliminare una regola business &#40;Master Data Services&#41;](../master-data-services/delete-a-business-rule-master-data-services.md)   
 [Creare e pubblicare una regola di business &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [Regole business &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  
