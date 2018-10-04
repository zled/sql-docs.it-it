---
title: AllowNullsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- AllowNullsEnum
helpviewer_keywords:
- AllowNullsEnum enumeration [ADOX]
ms.assetid: 6acf3689-1a7f-4379-9d7f-df452ccbac27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d1f4f5ce302c6f9e3e28b037c838d452f771114
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692689"
---
# <a name="allownullsenum"></a>AllowNullsEnum
Specifica se i record con valori null vengono indicizzati.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|L'indice consente le voci in cui le colonne chiave sono null. Se viene immesso un valore null in una colonna chiave, la voce viene inserita nell'indice.|  
|**adIndexNullsDisallow**|1|Valore predefinito. L'indice non consente le voci in cui le colonne chiave sono null. Se viene immesso un valore null in una colonna chiave, si verificherà un errore.|  
|**adIndexNullsIgnore**|2|L'indice non inserisce le voci che contengono le chiavi null. Se viene immesso un valore null in una colonna chiave, la voce viene ignorata e verrà generato alcun errore.|  
|**adIndexNullsIgnoreAny**|4|L'indice non inserisce le voci in cui alcune colonne chiave ha un valore null. Per un indice con una a più colonne chiave, se si immette un valore null in una colonna, la voce viene ignorata e verrà generato alcun errore.|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà IndexNulls (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
