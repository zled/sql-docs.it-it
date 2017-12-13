---
title: Elemento PermissionSet (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PermissionSet Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: PermissionSet
helpviewer_keywords: PermissionSet element
ms.assetid: da5a9175-48e4-4b5e-a780-3e0077939974
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0b8415d83fbb76b2c280d8d59595f52983b04fc9
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="permissionset-element-assl"></a>Elemento PermissionSet (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Identifica il set di autorizzazioni associato a un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] assembly .NET Framework.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ClrAssembly>  
   ...  
   <PermissionSet>...</PermissionSet>  
  
</ClrAssembly>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Safe*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Safe*|È consentito solo il calcolo interno e l'accesso locale ai dati. *Safe* è il set di autorizzazioni più restrittivo. Il codice eseguito da un assembly con autorizzazioni *Safe* non può accedere alle risorse di sistema esterne, ad esempio i file, la rete, le variabili di ambiente o il registro di sistema.|  
|*ExternalAccess*|*Safe*, con la possibilità aggiuntiva di accedere a risorse di sistema esterne, ad esempio i file, la rete, le variabili di ambiente e il registro di sistema.|  
|*Senza restrizioni*|Senza restrizioni consente agli assembly libero accesso alle risorse, interne ed esterne [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il codice eseguito all'interno di un assembly *Unrestricted* può chiamare il codice non gestito.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **PermissionSet** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.PermissionSet>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati ComAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Elemento Assemblies &#40; ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Elemento database &#40; ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Elemento server &#40; ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
