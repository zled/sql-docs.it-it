---
title: Elemento Delete (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Delete Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.delete
- urn:schemas-microsoft-com:xml-analysis#Delete
- http://schemas.microsoft.com/analysisservices/2003/engine#Delete
helpviewer_keywords:
- Delete element
ms.assetid: 76201b18-11e9-4815-9287-27a068d8fbc5
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 880c869016a6f433e6593d17d0519eba58bc613e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="delete-element-xmla"></a>Elemento Delete (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Elimina un oggetto in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Delete IgnoreFailures="boolean">  
      <Object>...</Object>  
   </Delete>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|Attribute|Description|  
|---------------|-----------------|  
|IgnoreFailures|Attributo **Boolean** facoltativo. Se è impostato su True, il metodo **Execute** ignora gli errori di rete o gli errori relativi alle partizioni remote.|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
