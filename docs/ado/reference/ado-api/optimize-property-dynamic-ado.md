---
title: "Ottimizzare la proprietà dinamica (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Optimize property [ADO]
ms.assetid: a491c4ce-2b04-4c84-be83-3846bde8d16b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4aeae41d865e585c4c8b93c86bd6f8e9753eaea1
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="optimize-property-dynamic-ado"></a>Ottimizzare la proprietà dinamica (ADO)
Specifica se è necessario creare un indice su una [campo](../../../ado/reference/ado-api/field-object.md).  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **booleano** valore che indica se è necessario creare un indice.  
  
## <a name="remarks"></a>Osservazioni  
 Un indice può migliorare le prestazioni delle operazioni di ricerca o ordinare i valori in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). L'indice è interno al ADO. in modo esplicito non è possibile accedere o utilizzarlo nell'applicazione.  
  
 Per creare un indice su un campo, impostare il **Ottimizza** proprietà **True**. Per eliminare l'indice, impostare questa proprietà su **False**.  
  
 **Ottimizzare** è una proprietà dinamica accodata la [campo](../../../ado/reference/ado-api/field-object.md) oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta quando il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà è impostata su **adUseClient**.  
  
## <a name="usage"></a>Utilizzo  
  
```  
Dim rs As New Recordset  
Dim fld As Field  
rs.CursorLocation = adUseClient      'Enable index creation  
rs.Fields.Append "Field1", adChar, 35, adFldIsNullable  
rs.Open  
Set fld = rs.Fields(0)  
fld.Properties("Optimize") = True    'Create an index  
fld.Properties("Optimize") = False   'Delete an index  
```  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Ottimizzare l'esempio di proprietà (Visual Basic)](../../../ado/reference/ado-api/optimize-property-example-vb.md)   
 [Ottimizzare l'esempio di proprietà (VC + +)](../../../ado/reference/ado-api/optimize-property-example-vc.md)   
 [Proprietà filtro](../../../ado/reference/ado-api/filter-property.md)   
 [Find (metodo) (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Proprietà di ordinamento](../../../ado/reference/ado-api/sort-property.md)

