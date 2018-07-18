---
title: Elemento ImpersonationMode (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 786bc8e9ededa556d6d66d75e8e2cc52315cc62a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036332"
---
# <a name="impersonationmode-element-assl"></a>Elemento ImpersonationMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene un valore che indica il metodo di rappresentazione per gli elementi che derivano dal [ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md) tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ImpersonationInfo>  
   ...  
   <ImpersonationMode>...</ImpersonationMode>  
  
</ImpersonationInfo>...  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Valore predefinito*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Valore predefinito*|Il padre utilizza il metodo di rappresentazione più appropriato per il contesto in cui viene utilizzata la rappresentazione.|  
|*Account di rappresentazione*|Il padre utilizza le credenziali dell'account utente specificate nell'elemento padre.|  
|*ImpersonateAnonymous*|Il padre utilizza le credenziali di un utente anonimo.|  
|*ImpersonateCurrentUser*|Il padre utilizza le credenziali dell'utente corrente.|  
|*ImpersonateServiceAccount*|L'elemento padre utilizza le credenziali dell'account del servizio associata all'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
 L'enumerazione che corrisponde ai valori consentiti per **ImpersonationMode** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ImpersonationLevel>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
