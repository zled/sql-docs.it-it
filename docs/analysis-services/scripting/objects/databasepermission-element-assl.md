---
title: Elemento DatabasePermission (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 855c632b78beb3a5ba75ff7acf31b72fff229e95
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34035172"
---
# <a name="databasepermission-element-assl"></a>Elemento DatabasePermission (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Elemento Role & #40; ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
