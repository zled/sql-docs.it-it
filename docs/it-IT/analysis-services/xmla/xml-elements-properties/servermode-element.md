---
title: Elemento ServerMode | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: c2f8cb39-dad7-433b-b7b7-fb1625f76a84
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: af2c8d12e2861993474a093b2385f393924f2f67
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="servermode-element"></a>Elemento ServerMode
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Il **ServerMode** elemento server specifica la modalità in cui opera il server.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Server>  
...  
   <ddl300:ServerMode>...</ddl300:ServerMode>  
...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|(nessuna)|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il server funziona in una delle modalità seguenti:  
  
|Value|Description|  
|-----------|-----------------|  
|*Multidimensionale*|Modalità multidimensionale e di data mining|  
|*Tabulare*|Modalità tabulare|  
|*SharePoint*|Modalità SharePoint|  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../../analysis-services/scripting/objects/server-element-assl.md)  
  
  
