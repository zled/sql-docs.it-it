---
title: Elemento DataSourcePermissions (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b16a00c43f896cafaeda3549d32b953d3be3adf4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028502"
---
# <a name="datasourcepermissions-element-assl"></a>Elemento DataSourcePermissions (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la raccolta di [DataSourcePermission](../../../analysis-services/scripting/objects/datasourcepermission-element-assl.md) gli elementi associati a un [DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md) tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataSource>  
   ...  
   <DataSourcePermissions>  
      <DataSourcePermission>...</DataSourcePermission>  
   </DataSourcePermissions>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Origine dati](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)|  
|Elementi figlio|[DataSourcePermission](../../../analysis-services/scripting/objects/datasourcepermission-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati Permission & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [Raccolte & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
