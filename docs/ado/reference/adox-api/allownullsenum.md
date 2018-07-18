---
title: AllowNullsEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- AllowNullsEnum
helpviewer_keywords:
- AllowNullsEnum enumeration [ADOX]
ms.assetid: 6acf3689-1a7f-4379-9d7f-df452ccbac27
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49d0ef3d6de71281d403fafe71bf0df835c8985d
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284840"
---
# <a name="allownullsenum"></a>AllowNullsEnum
Specifica se i record con valori null vengono indicizzati.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|L'indice consente le voci in cui le colonne chiave sono null. Se viene immesso un valore null in una colonna chiave, la voce viene inserita in corrispondenza dell'indice.|  
|**adIndexNullsDisallow**|1|Valore predefinito. L'indice non consente le voci in cui le colonne chiave sono null. Se viene immesso un valore null in una colonna chiave, si verificherà un errore.|  
|**adIndexNullsIgnore**|2|L'indice non include le voci che contengono le chiavi null. Se viene immesso un valore null in una colonna chiave, la voce verrà ignorata e verrà generato alcun errore.|  
|**adIndexNullsIgnoreAny**|4|L'indice non include voci in cui alcune colonne chiave ha un valore null. Per un indice con una più colonne chiave, se viene immesso un valore null in una colonna, la voce verrà ignorata e verrà generato alcun errore.|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà IndexNulls (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
