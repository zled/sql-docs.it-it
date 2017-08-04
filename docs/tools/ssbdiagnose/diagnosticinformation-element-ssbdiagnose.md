---
title: Elemento DiagnosticInformation (ssbdiagnose) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML output file format [ssbdiagnose], diagnosticinformation element
- diagnosticinformation element
- ssbdiagnose
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9d5a21ac18d6b4982c7c93bf11e3bf16051dc0c7
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

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
  
|Attribute|Descrizione|  
|---------------|-----------------|  
|**Nessuno**|N/D|  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuno|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|Una volta per file di output XML **ssbdiagnose** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|Nessuno|  
|**Elementi figlio**|[Elemento banner &#40; ssbdiagnose &#41;](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)<br /><br /> [Elemento Issue &#40; ssbdiagnose &#41;](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sugli spazi dei nomi XML, vedere [Spazi dei nomi in un documento XML](http://go.microsoft.com/fwlink/?LinkId=7341) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità ssbdiagnose &#40; Service Broker &#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
