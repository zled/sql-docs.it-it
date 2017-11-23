---
title: "Proprietà FilterAxis (ADO MD) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Cellset::FilterAxis
- FilterAxis
helpviewer_keywords: FilterAxis property [ADO MD]
ms.assetid: 9c656963-531e-4cd1-b698-d5f42a9b7ba3
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6271e96db5edc22b7d8c7d92ff82a043167a912f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="filteraxis-property-ado-md"></a>Proprietà FilterAxis (ADO MD)
Indica informazioni di filtro corrente [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un [asse](../../../ado/reference/ado-md-api/axis-object-ado-md.md) dell'oggetto ed è di sola lettura.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **FilterAxis** proprietà per restituire informazioni sulle dimensioni che sono stati utilizzati per suddividere i dati. Il [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md) proprietà del **asse** restituisce il numero di dimensioni di sezionamento. Questo asse è in genere ha una sola riga.  
  
 Il **asse** restituito da **FilterAxis** non è inclusa nel [assi](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) raccolta per un [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) oggetto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Cellset (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto asse (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Oggetto dimensione (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Proprietà DimensionCount (ADO MD)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
