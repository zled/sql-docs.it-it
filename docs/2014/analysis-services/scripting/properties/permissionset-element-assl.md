---
title: Elemento PermissionSet (ASSL) | Documenti Microsoft
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
- PermissionSet Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PermissionSet
helpviewer_keywords:
- PermissionSet element
ms.assetid: da5a9175-48e4-4b5e-a780-3e0077939974
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a6246058af826a73b589f1854b0236de946a4d65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157826"
---
# <a name="permissionset-element-assl"></a>Elemento PermissionSet (ASSL)
  Identifica il set di autorizzazioni associato un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] assembly .NET Framework.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ClrAssembly>  
   ...  
   <PermissionSet>...</PermissionSet>  
  
</ClrAssembly>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Safe*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ClrAssembly](../data-type/assembly-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Safe*|È consentito solo il calcolo interno e l'accesso locale ai dati. *Safe* è il set di autorizzazioni più restrittivo. Il codice eseguito da un assembly con autorizzazioni *Safe* non può accedere alle risorse di sistema esterne, ad esempio i file, la rete, le variabili di ambiente o il registro di sistema.|  
|*ExternalAccess*|*Safe*, con la possibilità aggiuntiva di accedere a risorse di sistema esterne, ad esempio i file, la rete, le variabili di ambiente e il registro di sistema.|  
|*Senza restrizioni*|Senza restrizioni concede agli assembly libero accesso alle risorse interne ed esterne [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il codice eseguito all'interno di un assembly *Unrestricted* può chiamare il codice non gestito.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `PermissionSet` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.PermissionSet>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati ComAssembly &#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Elemento Assemblies &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Elemento database &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Elemento server &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  