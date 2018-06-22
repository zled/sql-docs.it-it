---
title: Elemento DatabasePermission (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DatabasePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DatabasePermission
helpviewer_keywords:
- DatabasePermission element
ms.assetid: 6dcb9136-a40d-42e3-ad3b-b8ce8c7ca78c
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e47203616cc76fa09c0fd0658e7dad8a89c90a9b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077871"
---
# <a name="databasepermission-element-assl"></a>Elemento DatabasePermission (ASSL)
  Definisce le autorizzazioni predefinite in un [Database](database-element-assl.md) elemento per uno specifico [ruolo](role-element-assl.md) elemento.  
  
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[Autorizzazione](../data-type/permission-data-type-assl.md)|  
|Valore predefinito|False|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DatabasePermissions](../collections/databasepermissions-element-assl.md)|  
|Elementi figlio|[Amministrare](../properties/administer-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Gli oggetti `DatabasePermission` possono essere presenti solo per i ruoli posseduti dal database e per ogni ruolo può essere presente un solo oggetto `DatabasePermission`.  
  
 Questo elemento dispone delle convalide seguenti in DeploymentMode, valore 2 (modelli tabulari).  
  
-   *Amministrare* valore predefinito dell'attributo è impostata su `False`, salvo quando l'utente dispone di privilegi amministrativi. Per utenti con privilegi amministrativi il valore dell'attributo è impostato su `True`.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Role &#40;ASSL&#41;](role-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  