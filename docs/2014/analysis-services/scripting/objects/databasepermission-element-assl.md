---
title: Elemento DatabasePermission (ASSL) | Microsoft Docs
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0fbfd9544e5305169e0d25b1b0157197d39cc002
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37259527"
---
# <a name="databasepermission-element-assl"></a>Elemento DatabasePermission (ASSL)
  Definisce le autorizzazioni predefinite in un [Database](database-element-assl.md) (elemento) per uno specifico [ruolo](role-element-assl.md) elemento.  
  
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
  
## <a name="remarks"></a>Note  
 Gli oggetti `DatabasePermission` possono essere presenti solo per i ruoli posseduti dal database e per ogni ruolo può essere presente un solo oggetto `DatabasePermission`.  
  
 Questo elemento dispone delle convalide seguenti in DeploymentMode, valore 2 (modelli tabulari).  
  
-   *Amministrare* valore predefinito dell'attributo è impostato su `False`, salvo quando l'utente dispone di privilegi amministrativi. Per utenti con privilegi amministrativi il valore dell'attributo è impostato su `True`.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Role &#40;ASSL&#41;](role-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
