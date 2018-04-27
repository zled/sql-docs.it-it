---
title: Parole riservate (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
caps.latest.revision: 11
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 31d22299f286678c0380c4287792610cd0281f0f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="reserved-words-master-data-services"></a>Parole riservate (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], quando si creano oggetti modello o membri, alcune parole non possono essere utilizzate. È possibile che l'utilizzo di queste parole provochi errori.  
  
> [!NOTE]  
>  Inoltre, è necessario limitare l'utilizzo di caratteri speciali (simboli, sillabazione e così via).  
  
-   [Modelli](../master-data-services/reserved-words-master-data-services.md#models)  
  
-   [Entità](../master-data-services/reserved-words-master-data-services.md#entities)  
  
-   [Gerarchie esplicite](../master-data-services/reserved-words-master-data-services.md#exhierarchies)  
  
-   [Attributi](../master-data-services/reserved-words-master-data-services.md#attributes)  
  
-   [Membri](../master-data-services/reserved-words-master-data-services.md#members)  
  
##  <a name="models"></a> Modelli  
 Se si crea un modello con il nome impostato su **Name** o **Code**, non selezionare **Crea entità con lo stesso nome del modello** poiché non è possibile usare **Name** o **Code** per il nome di un'entità.  
  
##  <a name="entities"></a> Entità  
 Per i nomi dell'entità, non è possibile utilizzare **Name** o **Code**.  
  
##  <a name="exhierarchies"></a> Gerarchie esplicite  
 Per i nomi della gerarchia espliciti, non è possibile utilizzare **Name** o **Code**.  
  
##  <a name="attributes"></a> Attributi  
  
-   **ID**  
  
-   **Code**  
  
-   **EnterUserName**  
  
-   **LastChgUserName**  
  
-   **Nome**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a> Membri  
 Per i membri, non è possibile usare **MDMMemberStatus**, **MDMUnused**o **ROOT** per il valore di attributo **Code** .  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
  
