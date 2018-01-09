---
title: Elemento password (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Password Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Password
- urn:schemas-microsoft-com:xml-analysis#Password
- microsoft.xml.analysis.password
helpviewer_keywords: Password element
ms.assetid: 8a0603bd-f6a1-4b86-84f1-c83d0b03951b
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 64bd2da0a5e2ef508feaa00279f57b4604066d1e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="password-element-xmla"></a>Elemento Password (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Determina la password da utilizzare dall'elemento padre [Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) o [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) comando per la crittografia o decrittografia di un file di backup.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Password>...</Password>  
   ...  
</Backup>  
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
|Elementi padre|[Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [ripristino](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Per **Backup** comandi, se il **Password** elemento non è incluso o contiene una stringa vuota, il file di backup non è crittografato.  
  
 Per **ripristinare** comandi, se il **Password** elemento non è incluso o contiene una stringa vuota durante il tentativo di ripristinare un file di backup crittografato, si verifica un errore.  
  
 Se **percorso** sono inclusi elementi in uno un **Backup** o **ripristinare** comando, lo stesso **Password** elemento viene usato per il backup di entrambi e file di backup remoti. Per ulteriori informazioni sui file di backup remoti, vedere [backup, ripristino e sincronizzazione di database &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento location &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
