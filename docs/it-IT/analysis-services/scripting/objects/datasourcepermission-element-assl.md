---
title: Elemento DataSourcePermission (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DataSourcePermission Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DataSourcePermission element
ms.assetid: 6dc6fb13-034e-479a-902e-27f3fb78c33f
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2736e5f3f2c075e79af0f5522cdfc01bc03c735f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="datasourcepermission-element-assl"></a>Elemento DataSourcePermission (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce le autorizzazioni predefinite in un [DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md) per uno specifico tipo di dati [ruolo](../../../analysis-services/scripting/objects/role-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataSourcePermissions>  
   <DataSourcePermission xsi:type="Permission">  
      <!-- No child elements other than those from Permission are defined -->  
...</DataSourcePermission>  
</DataSourcePermissions>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[Autorizzazione](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DataSourcePermissions](../../../analysis-services/scripting/collections/datasourcepermissions-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Gli oggetti**DataSourcePermission** possono essere presenti solo per i ruoli posseduti dal database e per ogni ruolo può essere presente un solo oggetto **DataSourcePermission** .  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Role & #40; ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
