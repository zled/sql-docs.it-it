---
title: Metodo Discover (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Discover Method
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.discover
- urn:schemas-microsoft-com:xml-analysis#Discover
- Discover
helpviewer_keywords:
- Discover method
ms.assetid: 0eb52d88-c081-416e-a229-610e4373b0b3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 91ea30a495eb76c22075007f48e3ae721504ef49
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116321"
---
# <a name="discover-method-xmla"></a>Metodo Discover (XMLA)
  Recupera le informazioni, ad esempio l'elenco dei database disponibili o i dettagli su un oggetto specifico, da un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. I dati recuperati con il metodo `Discover` dipendono dai valori dei parametri passati al metodo stesso.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
 **Azione SOAP** "urn:schemas-microsoft-com:xml-analysis:Discover"  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Discover>  
   <RequestType>...</RequestType>  
   <Restrictions>...</Restrictions>  
   <Properties>...</Properties>  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|None|  
|Elementi figlio|[Le proprietà](xml-elements-properties/properties-element-xmla.md), [RequestType](xml-elements-properties/type-element-xmla.md), [restrizioni](xml-elements-properties/restrictions-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il metodo `Discover` richiede i metadati su istanze e oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. I metadati vengono restituiti utilizzando XMLA [set di righe](xml-data-types/rowset-data-type-xmla.md) tipo di dati.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente tramite il client viene inviata la chiamata `Discover` per richiedere un elenco di cubi dal database di esempio [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <RequestType>MDSCHEMA_CUBES</RequestType>  
   <Restrictions>  
      <RestrictionList>  
         <CATALOG_NAME>Adventure Works DW Multidimensional 2012</CATALOG_NAME>  
      </RestrictionList>  
   </Restrictions>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Tabular</Format>  
      </PropertyList>  
   </Properties>  
</Discover>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Eseguire il metodo &#40;XMLA&#41;](xml-elements-methods-execute.md)   
 [I metodi &#40;XMLA&#41;](xml-elements-methods.md)   
 [Elementi XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Set di righe dello schema di Analysis Services](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
