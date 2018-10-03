---
title: Metodo Execute (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Execute Method
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EXECUTE
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.execute
- urn:schemas-microsoft-com:xml-analysis#Execute
helpviewer_keywords:
- Execute method
ms.assetid: 0fff5221-7164-4bbc-ab58-49cf04c52664
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d1c3e842c8f859802be1193ca615933877faa1b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155682"
---
# <a name="execute-method-xmla"></a>Metodo Execute (XMLA)
  Invia il XML per i comandi Analysis (XMLA) a un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Include richieste che comportano il trasferimento dei dati, ad esempio recuperando o aggiornando dati nel server.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
 **Azione SOAP** "urn: schemas-microsoft-com: XML-analysis: Execute"  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Execute>  
   <Command>...</Command>  
   <Properties>...</Properties>  
   <Parameters>...</Parameters>  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che ricorre una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|None|  
|Elementi figlio|[Comando](xml-elements-properties/command-element-xmla.md), [parametri](xml-elements-properties/parameters-element-xmla.md), [proprietà](xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il `Execute` comandi XMLA forniti nell'esecuzione del metodo di `Command` elemento e restituisce tutti i dati risultanti utilizzando XMLA [set di righe](xml-data-types/rowset-data-type-xmla.md) tipo di dati (per set di risultati tabulari) o XMLA [MDDataSet](xml-data-types/mddataset-data-type-xmla.md) tipo di dati (per il set di risultati multidimensionali.)  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrata una chiamata al metodo `Execute` che contiene un'istruzione SELECT MDX (Multidimensional Expressions).  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Statement>  
         SELECT [Measures].MEMBERS ON COLUMNS FROM [Adventure Works]  
      </Statement>  
   </Command>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Multidimensional</Format>  
         <AxisFormat>ClusterFormat</AxisFormat>  
      </PropertyList>  
   </Properties>  
</Execute>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Metodo Discover &#40;XMLA&#41;](xml-elements-methods-discover.md)   
 [I metodi &#40;XMLA&#41;](xml-elements-methods.md)   
 [Elementi XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Set di righe dello schema di Analysis Services](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
