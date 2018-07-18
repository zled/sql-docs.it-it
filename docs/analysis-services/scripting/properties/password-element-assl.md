---
title: Elemento password (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cc5464e4530e00a0d12807cb0cef2c2e1aa22afa
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050669"
---
# <a name="password-element-assl"></a>Elemento Password (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la password dell'account utente per il [ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ImpersonationInfo  
   ...  
  <Password>...</Password>  
   ...  
</ImpersonationInfo>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore dei **Password** elemento, nonché il valore della [Account](../../../analysis-services/scripting/properties/account-element-impersonationinfo-assl.md) elemento, viene usato per gli scopi della rappresentazione se il valore del [ImpersonationMode](../../../analysis-services/scripting/properties/impersonationmode-element-assl.md) (elemento) per qualsiasi elemento derivato dal **ImpersonationInfo** tipo di dati è impostato su *ImpersonateAccount*.  
  
 Solo i membri del ruolo di amministratore del server per il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza può fornire un valore vuoto per il **Password** elemento  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento DataSourceImpersonationInfo &#40;ASSL&#41;](../../../analysis-services/scripting/properties/datasourceimpersonationinfo-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
