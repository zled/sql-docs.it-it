---
title: Il tipo di dati ProactiveCachingObjectNotificationBinding (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 82c176201804e555f4e844ea38541fcbf20d9446
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34031382"
---
# <a name="proactivecachingobjectnotificationbinding-data-type-assl"></a>Tipo di dati ProactiveCachingObjectNotificationBinding (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati derivato astratto che rappresenta le informazioni per il [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) elemento relative alle modifiche di origine dati in tabelle e viste specificate o in tabelle e viste identificate tramite i dati esistenti associazioni che richiedono la ricompilazione della cache.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProactiveCachingObjectNotificationBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <NotificationTechnique>...</NotificationTechnique>  
</ProactiveCachingObjectNotificationBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|[ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)|  
|Tipi di dati derivati|[ProactiveCachingInheritedBinding](../../../analysis-services/scripting/data-type/proactivecachinginheritedbinding-data-type-assl.md), [ProactiveCachingTablesBinding](../../../analysis-services/scripting/data-type/proactivecachingtablesbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[NotificationTechnique](../../../analysis-services/scripting/properties/notificationtechnique-element-assl.md)|  
|Elementi derivati|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sul **ProactiveCachingBinding** tipo, inclusa una tabella della gerarchia di ereditarietà del **ProactiveCachingBinding** tipi, vedere [dati ProactiveCachingBinding Tipo &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md).  
  
 Per ulteriori informazioni sul **associazione** tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del **associazione** tipo e la gerarchia di ereditarietà dei **associazione**  sui tipi, vedere [associazione tipo di dati &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni dati in ASSL, vedere [origini dati e associazioni & #40; SSAS multidimensionale & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ProactiveCachingObjectNotificationBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
