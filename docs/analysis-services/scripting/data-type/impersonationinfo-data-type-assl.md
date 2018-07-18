---
title: Il tipo di dati ImpersonationInfo (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e1dcf87a713337b91cd07c9d52ac76498ffca679
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037565"
---
# <a name="impersonationinfo-data-type-assl"></a>Tipo di dati ImpersonationInfo (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati primitivo che rappresenta le informazioni utilizzate per rappresentare un utente.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ImpersonationInfo>  
   <ImpersonationMode>...</ImpersonationMode>  
   <Account>...</Account>  
   <Password>   </Password>  
   <ImpersonationInfoSecurity>...</ImpersonationInfoSecurity>  
</ImpersonationInfo>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati di base|Nessuno|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[Account](../../../analysis-services/scripting/properties/account-element-impersonationinfo-assl.md), [ImpersonationInfoSecurity](../../../analysis-services/scripting/properties/impersonationinfosecurity-element-assl.md), [ImpersonationMode](../../../analysis-services/scripting/properties/impersonationmode-element-assl.md), [Password](../../../analysis-services/scripting/properties/password-element-assl.md)|  
|Elementi derivati|[DataSourceImpersonationInfo](../../../analysis-services/scripting/properties/datasourceimpersonationinfo-element-assl.md), [ImpersonationInfo](../../../analysis-services/scripting/properties/impersonationinfo-element-assl.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
