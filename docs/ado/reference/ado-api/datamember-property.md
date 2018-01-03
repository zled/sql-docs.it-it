---
title: "Proprietà DataMember | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Recordset20::DataMember
helpviewer_keywords: DataMember property
ms.assetid: 2c8fb09e-10ad-49b5-ab41-2603771780d9
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cdb6c6dbb5d7bb7c5c10a968cffe759edb9309f6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="datamember-property"></a>Proprietà DataMember
Indica il nome del membro dati che verrà recuperato dal [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) a cui fa riferimento il [DataSource](../../../ado/reference/ado-api/datasource-property-ado.md) proprietà.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **stringa** valore. Il nome non è tra maiuscole e minuscole.  
  
## <a name="remarks"></a>Osservazioni  
 Questa proprietà viene utilizzata per creare controlli associati a dati con l'ambiente di dati. L'ambiente di dati gestisce insiemi di dati (origini dati) contenenti oggetti denominati (membri di dati) che saranno rappresentati come un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
 Il **DataMember** e **DataSource** proprietà devono essere usate insieme.  
  
 Il **DataMember** proprietà determina quale oggetto specificato da di **DataSource** proprietà sarà rappresentata come un **Recordset** oggetto. Il **Recordset** oggetto deve essere chiusi prima di questa proprietà è impostata. Viene generato un errore se il **DataMember** non è impostata prima di **DataSource** proprietà, o se il **DataMember** nome non è riconosciuto dall'oggetto specificato nel **DataSource** proprietà.  
  
## <a name="usage"></a>Utilizzo  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to  
Set rs.DataSource = myDE      'Name of the object containing an IRowset  
```  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà DataSource (ADO)](../../../ado/reference/ado-api/datasource-property-ado.md)
