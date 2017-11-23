---
title: Elemento DatabasePermission (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DatabasePermission Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DatabasePermission
helpviewer_keywords: DatabasePermission element
ms.assetid: 6dcb9136-a40d-42e3-ad3b-b8ce8c7ca78c
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c17db1238e4ceba510024ea64acdbc856ffdcb9b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="databasepermission-element-assl"></a>Elemento DatabasePermission (ASSL)
  Definisce le autorizzazioni predefinite in un [Database](../../../analysis-services/scripting/objects/database-element-assl.md) elemento per uno specifico [ruolo](../../../analysis-services/scripting/objects/role-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DatabasePermissions>  
      <DatabasePermission xsi:type="Permission">  
      <!-- The following elements extend Permission -->  
      <Administer>...</Administer>  
...</DatabasePermission>  
</DatabasePermissions>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[Autorizzazione](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Valore predefinito|False|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DatabasePermissions](../../../analysis-services/scripting/collections/databasepermissions-element-assl.md)|  
|Elementi figlio|[Amministrare](../../../analysis-services/scripting/properties/administer-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Gli oggetti**DatabasePermission** possono essere presenti solo per i ruoli posseduti dal database e per ogni ruolo può essere presente un solo oggetto **DatabasePermission** .  
  
 Questo elemento dispone delle convalide seguenti in DeploymentMode, valore 2 (modelli tabulari).  
  
-   Il valore predefinito dell'attributo*Administer* è impostato su **False**, salvo quando l'utente dispone di privilegi amministrativi. Per utenti con privilegi amministrativi il valore dell'attributo è impostato su **True**.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Role &#40; ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
