---
title: "Proprietà ActiveCommand (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset20::ActiveCommand
helpviewer_keywords:
- ActiveCommand property [ADO]
ms.assetid: fb4088d5-5968-42d6-aeaa-3955046bb4da
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eee93cce3f7868ff9c71a83a462e5073d3e2d722
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="activecommand-property-ado"></a>Proprietà ActiveCommand (ADO)
Indica il [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto che ha creato l'oggetto associato [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **Variant** che contiene un **comando** oggetto. Valore predefinito è un riferimento di oggetto null.  
  
## <a name="remarks"></a>Osservazioni  
 Il **ActiveCommand** proprietà è di sola lettura.  
  
 Se un **comando** oggetto non è stato utilizzato per creare l'oggetto corrente **Recordset**, quindi un **Null** riferimento a un oggetto viene restituito.  
  
 Utilizzare questa proprietà per trovare l'oggetto associato **comando** oggetto quando è disponibile solo il valore risultante **Recordset** oggetto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà ActiveCommand (VB)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [Esempio di proprietà ActiveCommand (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [Esempio di proprietà ActiveCommand (VC + +)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
