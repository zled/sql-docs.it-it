---
title: Elemento ServerMode | Documenti Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c2f8cb39-dad7-433b-b7b7-fb1625f76a84
caps.latest.revision: 6
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 8448e5ac3111f4c1683ae3dd62dcaef992f3f0e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054848"
---
# <a name="servermode-element"></a>Elemento ServerMode
  L'elemento server `ServerMode` consente di specificare la modalità di funzionamento del server.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Server>  
...  
   <ddl300:ServerMode>...</ddl300:ServerMode>  
...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|(nessuna)|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Server](../../scripting/objects/server-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il server funziona in una delle modalità seguenti:  
  
|valore|Description|  
|-----------|-----------------|  
|*Multidimensionale*|Modalità multidimensionale e di data mining|  
|*Tabulare*|Modalità tabulare|  
|*SharePoint*|Modalità SharePoint|  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../scripting/objects/server-element-assl.md)  
  
  