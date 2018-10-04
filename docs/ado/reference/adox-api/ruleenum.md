---
title: RuleEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RuleEnum
helpviewer_keywords:
- RuleEnum enumeration [ADOX]
ms.assetid: 738fd3ff-3daf-483d-a0b9-88bef1be54c1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 81c93601dbc47033618fdc72106d91e1b670fd8c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787049"
---
# <a name="ruleenum"></a>RuleEnum
Specifica la regola per seguire quando un [chiave](../../../ado/reference/adox-api/key-object-adox.md) viene eliminato.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adRICascade**|1|Consente di propagare le modifiche.|  
|**adRINone**|0|Valore predefinito. Non viene eseguita alcuna azione.|  
|**adRISetDefault**|3|Valore di chiave esterna è impostata sul valore predefinito.|  
|**adRISetNull**|2|Valore di chiave esterna è impostato su null.|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà DeleteRule (ADOX)](../../../ado/reference/adox-api/deleterule-property-adox.md)
