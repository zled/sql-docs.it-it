---
title: Elemento ReadDefinition (ASSL) | Microsoft Docs
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
- ReadDefinition Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReadDefinition
helpviewer_keywords:
- ReadDefinition element
ms.assetid: 1f250129-13b2-41b9-b083-b5aacddf0060
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fed91c75bd717e67dd624fc16f7091be24fb030c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297231"
---
# <a name="readdefinition-element-assl"></a>Elemento ReadDefinition (ASSL)
  Determina se i membri possono leggere la definizione del database o la definizione di oggetti nel database.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Permission> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <ReadDefinition>...</ReadDefinition>  
   ...  
</Permission>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Nessuno*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[CubePermission](../objects/cubepermission-element-assl.md), [DatabasePermission](../objects/databasepermission-element-assl.md), [DimensionPermission](../objects/dimensionpermission-element-assl.md), [MiningModelPermission](../objects/miningmodelpermission-element-assl.md), [MiningStructurePermission ](../objects/miningstructurepermission-element-assl.md), [Autorizzazione](../data-type/permission-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Nessuno*|L'accesso alla definizione dell'oggetto non è consentito.|  
|*Base*|È consentito l'accesso di base alla definizione dell'oggetto. **Nota:** questa autorizzazione è necessaria per la creazione di cubi locali, collegare i gruppi di misure e dimensioni di collegamento.|  
|*È consentito*|È consentito l'accesso completo alla definizione dell'oggetto. **Nota:** questa autorizzazione è necessaria per l'esecuzione di un [Discover](../../xmla/xml-elements-methods-discover.md) XML per la chiamata Analysis (XMLA) utilizzando il parametro DISCOVER_XML_METADATA.|  
  
 Gli elementi che corrispondono ai padri di `ReadDefinition` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CubePermission>, <xref:Microsoft.AnalysisServices.DatabasePermission>, <xref:Microsoft.AnalysisServices.DimensionPermission>, <xref:Microsoft.AnalysisServices.MiningModelPermission>, <xref:Microsoft.AnalysisServices.MiningStructurePermission> e <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Role &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
