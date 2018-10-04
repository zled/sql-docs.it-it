---
title: IDBProperties (OLE DB) | Documenti di Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b6dada26e15fc83d890b270ad553eb051bb08fa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135871"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  La specifica dello standard OLE DB consente ai provider di specificare VT_EMPTY per `DBPROPINFO::vValues`. Tuttavia [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB Native Client restituisce sempre VT_EMPTY quando si chiama `IDBProperties::GetPropertyInfo` con `DBPROPSET_ROWSETALL` per recuperare le proprietà del set di righe.  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
