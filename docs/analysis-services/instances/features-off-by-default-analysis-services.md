---
title: "Funzionalità disattivata per impostazione predefinita (Analysis Services) | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4b9d92a7620ed165d661fe4c48726a8049d33500
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

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
  
  

