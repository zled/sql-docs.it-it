---
title: Elemento ServerMode | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: c2f8cb39-dad7-433b-b7b7-fb1625f76a84
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 463af850c8af6e6db386f95be510b4eae23a5bbd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="servermode-element"></a>Elemento ServerMode
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
  
|Valore|Description|  
|-----------|-----------------|  
|*Multidimensionale*|Modalità multidimensionale e di data mining|  
|*Tabulare*|Modalità tabulare|  
|*SharePoint*|Modalità SharePoint|  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../../analysis-services/scripting/objects/server-element-assl.md)  
  
  
