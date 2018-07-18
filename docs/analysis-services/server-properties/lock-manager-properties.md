---
title: Proprietà di Gestione blocchi | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 146bfef500424b7a587c3fb28616a3727086f265
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033329"
---
# <a name="lock-manager-properties"></a>Proprietà di Gestione blocchi
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta le proprietà del server di Gestione blocchi elencate nella tabella seguente. Per altre informazioni sulle proprietà aggiuntive del server e sulla relativa impostazione, vedere [Proprietà server in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Si applica a:** modalità server multidimensionale e tabulare  
  
## <a name="properties"></a>Proprietà  
 **DefaultLockTimeoutMS**  
 Proprietà a valore integer a 32 bit con segno che definisce il timeout predefinito dei blocchi per le richieste di blocco interne.  
  
 Il valore predefinito di questa proprietà è -1, che indica l'assenza di timeout per le richieste di blocco interne.  
  
 **LockWaitGranularityMS**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **DeadlockDetectionGranularityMS**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà server in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Determinare la modalità server di un'istanza di Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
