---
title: Elemento DiagnosticInformation (ssbdiagnose) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose], diagnosticinformation element
- diagnosticinformation element
- ssbdiagnose
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a6dfc3946f0087b65699968448bdb1c014750572
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194883"
---
# <a name="diagnosticinformation-element-ssbdiagnose"></a>Elemento DiagnosticInformation (ssbdiagnose)
  L'elemento **DiagnosticInformation** contiene tutti gli elementi che segnalano le informazioni di diagnostica rilevate dall'utilità. **DiagnosticInformation** è l'elemento radice di un file di output XML **ssbdiagnostic** .  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DiagnosticInformation>   
    ...   
</DiagnosticInformation>  
```  
  
## <a name="element-attributes"></a>Attributi elemento  
  
|attribute|Description|  
|---------------|-----------------|  
|`None`|N/D|  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Una volta per file di output XML **ssbdiagnose** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|Nessuna.|  
|**Elementi figlio**|[Elemento banner &#40;ssbdiagnose&#41;](banner-element-ssbdiagnose.md)<br /><br /> [Elemento Issue &#40;ssbdiagnose&#41;](issue-element-ssbdiagnose.md)|  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sugli spazi dei nomi XML, vedere [Spazi dei nomi in un documento XML](http://go.microsoft.com/fwlink/?LinkId=7341) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità ssbdiagnose &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  
