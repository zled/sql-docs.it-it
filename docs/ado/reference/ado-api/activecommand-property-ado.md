---
title: Proprietà ActiveCommand (ADO) | Documenti Microsoft
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
- Recordset20::ActiveCommand
helpviewer_keywords:
- ActiveCommand property [ADO]
ms.assetid: fb4088d5-5968-42d6-aeaa-3955046bb4da
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e85286a885ab8edcfb08b029f7a1fd77c8d3f4a0
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274962"
---
# <a name="activecommand-property-ado"></a>Proprietà ActiveCommand (ADO)
Indica il [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto che ha creato l'oggetto associato [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **Variant** che contiene un **comando** oggetto. Valore predefinito è un riferimento di oggetto null.  
  
## <a name="remarks"></a>Remarks  
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
