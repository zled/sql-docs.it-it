---
title: Elemento OlapInfo (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: OlapInfo Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#OlapInfo
- microsoft.xml.analysis.olapinfo
- urn:schemas-microsoft-com:xml-analysis#OlapInfo
- OLAPInfo
helpviewer_keywords: OlapInfo element
ms.assetid: 8828fdd7-c0f7-48ce-a0d0-ab4bc1a995cf
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b3e93be0db8c57ad2fa27724b5b6d8afbf5d77c2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="olapinfo-element-xmla"></a>Elemento OlapInfo (XMLA)
  Contiene i metadati di asse e cella contenuti un [radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elemento che utilizza il [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <OlapInfo>  
      <CubeInfo>...</CubeInfo>  
      <AxesInfo>...</AxesInfo>  
      <CellInfo>...</CellInfo>  
   </OlapInfo>  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Elementi figlio|[AxesInfo](../../../analysis-services/xmla/xml-elements-properties/axesinfo-element-xmla.md), [CellInfo](../../../analysis-services/xmla/xml-elements-properties/cellinfo-element-xmla.md), [CubeInfo](../../../analysis-services/xmla/xml-elements-properties/cubeinfo-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **OLAPInfo** sezione di un **radice** elemento utilizzando il **MDDataSet** tipo di dati fornisce i metadati relativi al cubo, gli assi del risultato multidimensionale e le proprietà le celle incluso il risultato.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
