---
title: Elemento Statement (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Statement Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Statement
- microsoft.xml.analysis.statement
- urn:schemas-microsoft-com:xml-analysis#Statement
helpviewer_keywords:
- Statement command
ms.assetid: bfedc03c-d476-4d55-b5fd-36169f01351a
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 172e9961945bceca25e7826d5035f4b33ae797a5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="statement-element-xmla"></a>Elemento Statement (XMLA)
  Contiene una query o istruzione da inviare tramite il **Execute** metodo a un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Statement>...</Statement>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **istruzione** comando esegue una query o istruzione sul [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta i linguaggi riportati di seguito.  
  
-   Espressioni MDX (MDX)  
  
-   MDX (Estensioni Data Mining)  
  
-   Un subset di SQL (Structured Query Language)  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

