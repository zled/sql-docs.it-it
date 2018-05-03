---
title: Elemento DiscoverResponse (XMLA) | Documenti Microsoft
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
- DiscoverResponse Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DiscoverResponse
- microsoft.xml.analysis.discoverresponse
- urn:schemas-microsoft-com:xml-analysis#DiscoverResponse
helpviewer_keywords:
- DiscoverResponse element
ms.assetid: 20e10a82-dbd1-4ead-b92d-f84b4b2f10c6
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6a2ebf97cf355ad906f0f90f35924fa1767ed666
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="xml-elements---objects---discoverresponse"></a>DiscoverResponse - oggetti - elementi XML
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene le informazioni restituite da un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in risposta a un [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) chiamata al metodo.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DiscoverResponse>  
   <return>  
</DiscoverResponse>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[restituire](../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **DiscoverResponse** è l'elemento in primo piano all'interno del corpo di una risposta SOAP per il **Discover** metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ExecuteResponse &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-objects-executeresponse.md)   
 [Gli oggetti &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-objects.md)  
  
  
