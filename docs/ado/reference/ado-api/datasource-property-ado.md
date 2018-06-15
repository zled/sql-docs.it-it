---
title: Proprietà origine dati (ADO) | Documenti Microsoft
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
- Recordset20::DataSource
helpviewer_keywords:
- DataSource property [ADO]
ms.assetid: 300a702a-3544-48c5-b759-83b511fe97e0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5fa4df4252d9970d4ec8ec36500dc5782466c675
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277470"
---
# <a name="datasource-property-ado"></a>Proprietà origine dati (ADO)
Indica un oggetto che contiene i dati per essere rappresentato come un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
## <a name="remarks"></a>Remarks  
 Questa proprietà viene utilizzata per creare controlli associati a dati con l'ambiente di dati. L'ambiente di dati gestisce le raccolte di dati (origini dati) che contiene oggetti denominati (membri di dati) che saranno rappresentati come un **Recordset** oggetto *.*  
  
 Il [DataMember](../../../ado/reference/ado-api/datamember-property.md) e **DataSource** proprietà devono essere utilizzate insieme.  
  
 L'oggetto a cui fa riferimento deve implementare il **IDataSource** l'interfaccia e deve contenere un **IRowset** interfaccia.  
  
## <a name="usage"></a>Utilizzo  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to.  
Set rs.DataSource = myDE      'Name of the object containing an IRowset.  
```  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà DataMember](../../../ado/reference/ado-api/datamember-property.md)
