---
title: Tipo di dati DataItem (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataItem Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataItem
helpviewer_keywords:
- DataItem data type
ms.assetid: f4f5155f-9c3d-49a1-a390-a9c734fafbce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f16c23941fc1048429ced974b88bba378bc72c2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153481"
---
# <a name="dataitem-data-type-assl"></a>Tipo di dati DataItem (ASSL)
  Definisce un tipo di dati primitivo che rappresenta le caratteristiche relative ai dati di un elemento di dati, ad esempio una colonna o un attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataItem>  
   <DataType>...</DataType>  
   <DataSize>...</DataSize>  
   <MimeType>...</MimeType>  
   <NullProcessing>...</NullProcessing>  
   <Trimming>...</Trimming>  
   <InvalidXmlCharacters>...</InvalidXmlCharacters>  
      <Collation>...</Collation>  
   <Format>...</Format>  
   <Source>...</Source>  
   <Annotations>...</Annotations>  
</DataItem>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Le annotazioni](../collections/annotations-element-assl.md), [regole di confronto](../properties/collation-element-assl.md), [DataSize](../properties/datasize-element-assl.md), [DataType](../properties/datatype-element-assl.md), [formato](../properties/format-element-assl.md), [InvalidXmlCharacters ](../properties/invalidxmlcharacters-element-assl.md), [MimeType](../properties/mimetype-element-assl.md), [NullProcessing](../properties/nullprocessing-element-assl.md), [origine](../properties/source-element-binding-assl.md), [Trimming](../properties/trimming-element-assl.md)|  
|Elementi derivati|Vedere la tabella nei Commenti.|  
  
## <a name="remarks"></a>Note  
 Il tipo di dati `DataItem` viene utilizzato per qualsiasi elemento dei dati che può essere associato; ad esempio, una misura, un chiave dell'attributo e un nome di attributo. I dettagli che sono attinenti e le impostazioni predefinite che si applicano, dipendono dall'utilizzo; ad esempio, i nomi di attributo devono essere stringhe.  
  
 Un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] accetta solo un determinato set di tipi di dati. L’utilizzo di altri tipi di dati comporta un errore, piuttosto che una conversione implicita in uno dei tipi validi.  
  
 Nella tabella seguente sono elencati elementi di tipo `DataItem`.  
  
|Elemento padre|Elemento di tipo `DataItem`|Commenti|  
|--------------------|----------------------------------|--------------|  
|[AttributeTranslation](../objects/column-element-assl.md)|`Source` elemento del `DataItem` deve essere di tipo [ColumnBinding](binding-data-type-assl.md) o [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/customrollupcolumn-element-assl.md)|`Source` elemento del `DataItem` deve essere di tipo [ColumnBinding](binding-data-type-assl.md) o [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/customrolluppropertiescolumn-element-assl.md)|`Source` elemento del `DataItem` deve essere di tipo [ColumnBinding](binding-data-type-assl.md) o [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/keycolumn-element-assl.md)|`Source` elemento del `DataItem` deve essere di tipo [ColumnBinding](binding-data-type-assl.md), [AttributeBinding](attributebinding-data-type-assl.md) o [TimeBinding](timebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/namecolumn-element-assl.md)|`Source` elemento del `DataItem` deve essere di tipo [ColumnBinding](binding-data-type-assl.md) o [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/skippedlevelscolumn-element-assl.md)|`Source` elemento del `DataItem` deve essere di tipo [ColumnBinding](binding-data-type-assl.md) o [AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/unaryoperatorcolumn-element-assl.md)|`Source` elemento del `DataItem` deve essere di tipo [ColumnBinding](binding-data-type-assl.md) o [AttributeBinding](attributebinding-data-type-assl.md)|  
|[Misura](../objects/measure-element-assl.md)|[Origine](../properties/source-element-binding-assl.md)|`Source` elemento del `DataItem` deve essere di tipo [RowBinding](rowbinding-data-type-assl.md), [ColumnBinding](binding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), o [CubeDimensionBinding](dimensionbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)|[KeyColumn](../objects/keycolumn-element-assl.md)|`Source` elemento del `DataItem` deve essere di tipo [ColumnBinding](binding-data-type-assl.md), [AttributeBinding](attributebinding-data-type-assl.md) o [InheritedBinding](inheritedbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[KeyColumn](../objects/keycolumn-element-assl.md)|`Source` elemento del `DataItem` deve essere di tipo [ColumnBinding](binding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[NameColumn](../objects/namecolumn-element-assl.md)|`Source` elemento del `DataItem` deve essere di tipo [ColumnBinding](binding-data-type-assl.md)|  
|[TableMiningStructureColumn](../objects/foreignkeycolumn-element-assl.md)|`Source` elemento del `DataItem` deve essere di tipo [ColumnBinding](binding-data-type-assl.md)|  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
