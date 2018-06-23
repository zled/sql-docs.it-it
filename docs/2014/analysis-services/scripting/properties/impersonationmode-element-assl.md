---
title: Elemento ImpersonationMode (ASSL) | Documenti Microsoft
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
- ImpersonationMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ImpersonateMode
helpviewer_keywords:
- ImpersonateMode element
ms.assetid: 160fdcb2-ac9f-4c5a-a0eb-a5f7669166b9
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e41e5b5fef7759f6ad310a7f04dc012a7b7cb54f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157598"
---
# <a name="impersonationmode-element-assl"></a>Elemento ImpersonationMode (ASSL)
  Contiene un valore che indica il metodo di rappresentazione per gli elementi derivati dal [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ImpersonationInfo>  
   ...  
   <ImpersonationMode>...</ImpersonationMode>  
  
</ImpersonationInfo>...  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Valore predefinito*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Valore predefinito*|Il padre utilizza il metodo di rappresentazione più appropriato per il contesto in cui viene utilizzata la rappresentazione.|  
|*Account di rappresentazione*|Il padre utilizza le credenziali dell'account utente specificate nell'elemento padre.|  
|*ImpersonateAnonymous*|Il padre utilizza le credenziali di un utente anonimo.|  
|*ImpersonateCurrentUser*|Il padre utilizza le credenziali dell'utente corrente.|  
|*ImpersonateServiceAccount*|L'elemento padre utilizza le credenziali dell'account del servizio che viene associato all'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
 L'enumerazione che corrisponde ai valori consentiti di `ImpersonationMode` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.ImpersonationLevel>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  