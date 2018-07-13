---
title: Elemento password (ASSL) | Microsoft Docs
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
- Password Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Password element
ms.assetid: ee756b01-fb08-4a9a-8c2a-7c04af0f8658
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 99d7eabdd66e6c7f036389b4825c5926873367b2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197741"
---
# <a name="password-element-assl"></a>Elemento Password (ASSL)
  Contiene la password dell'account utente per il [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) elemento.  
  
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
|Elemento padre|[ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore del `Password` elemento, nonché il valore della [Account](account-element-impersonationinfo-assl.md) elemento, viene usato per gli scopi della rappresentazione se il valore del [ImpersonationMode](impersonationmode-element-assl.md) (elemento) per qualsiasi elemento derivato dal `ImpersonationInfo` tipo di dati è impostato su *ImpersonateAccount*.  
  
 Solo membri del ruolo di amministratore del server per l'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] possono fornire un valore vuoto per l'elemento `Password`  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento DataSourceImpersonationInfo &#40;ASSL&#41;](impersonationinfo-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
