---
title: Account (ImpersonationInfo) (ASSL) elemento | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Account Element (ImpersonationInfo)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Account element
ms.assetid: aa3a1281-e42a-4926-875b-e6b81f4599c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f454e39a7c4ec4911f38ff070f94fcbe50a34c74
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190371"
---
# <a name="account-element-impersonationinfo-assl"></a>Elemento Account (ImpersonationInfo) (ASSL)
  Contiene il nome dell'account utente per il [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ImpersonationInfo  
   ...  
  <Account>...</Account>  
   ...  
</Action>  
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
|Elementi padre|[ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore del `Account` elemento, nonché il valore della [Password](password-element-assl.md) elemento, viene usato per gli scopi della rappresentazione se il valore del [ImpersonationMode](impersonationmode-element-assl.md) (elemento) per qualsiasi elemento derivato dal `ImpersonationInfo` tipo di dati è impostato su *ImpersonateAccount*.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento DataSourceImpersonationInfo &#40;ASSL&#41;](impersonationinfo-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
