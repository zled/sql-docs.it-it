---
title: "Funzionalità disattivata per impostazione predefinita (Analysis Services) | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: instances
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: eb06cb663a0a94a0611d95532e80f15e5df2da7d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="features-off-by-default-analysis-services"></a>Funzionalità disabilitate per impostazione predefinita (Analysis Services)
  Un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è progettata per garantire sicurezza per impostazione predefinita. Le funzionalità che potrebbero mettere a repentaglio la sicurezza sono pertanto disabilitate per impostazione predefinita. Le funzionalità seguenti sono installate in stato disabilitato e devono essere abilitate specificamente se si desidera usarle.  
  
## <a name="feature-list"></a>Elenco di funzionalità  
 Per abilitare le funzionalità seguenti, connettersi a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Fare clic con il pulsante destro del mouse sul nome dell'istanza e scegliere **Facet**. In alternativa, è possibile abilitare queste funzionalità tramite le proprietà del server, come illustrato nella sezione seguente.  
  
-   Query di data mining ad hoc (OpenRowset)  
  
-   Oggetti collegati (a)  
  
-   Oggetti collegati (da)  
  
-   Ascolto solo su connessioni locali  
  
-   Funzioni definite dall'utente  
  
## <a name="server-properties"></a>Proprietà server  
 Le funzionalità aggiuntive disattivate per impostazione predefinita possono essere abilitate tramite le proprietà del server. Connettersi a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Fare clic con il pulsante destro del mouse sul nome dell'istanza e scegliere **Proprietà**. Fare clic su **Generale**, quindi su **Mostra avanzate** per visualizzare un elenco più ampio di proprietà.  
  
-   Query di data mining ad hoc (OpenRowset)  
  
-   Consenti modelli di data mining di sessione (Data Mining)  
  
-   Oggetti collegati (a)  
  
-   Oggetti collegati (da)  
  
-   Funzioni definite dall'utente basate su COM  
  
-   Definizioni di traccia Flight Recorder (modelli).  
  
-   Registrazione query  
  
-   Ascolto solo su connessioni locali  
  
-   XML binario  
  
-   Compressione  
  
-   Affinità gruppo. Per informazioni dettagliate, vedere [Thread Pool Properties](../../analysis-services/server-properties/thread-pool-properties.md) .  
  
  
