---
title: Tipo di dati ColumnBinding (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ColumnBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ColumnBinding
helpviewer_keywords:
- ColumnBinding data type
ms.assetid: 3ab1bac1-6716-4b17-a107-d5f9c744c5e6
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1ad7cea5041f8d65964b85e36a0b992f9f5afdae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156807"
---
# <a name="columnbinding-data-type-assl"></a>Tipo di dati ColumnBinding (ASSL)
  Definisce un tipo di dati derivato che rappresenta l'associazione di una colonna in una vista origine dati a un [DataItem](dataitem-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ColumnBinding>  
   <!-- The following elements extend Binding -->  
   <TableID>...</TableID>  
      <ColumnID>...</ColumnID>  
</ColumnBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[Associazione](binding-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[ColumnID](../properties/columnid-element-eventcolumn-assl.md), [TableID](../properties/id-element-assl.md)|  
|Elementi derivati|Vedere [associazione](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Per creare nomi di elemento XML validi, [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] `DataSet` oggetti codificano i nomi di tabella Analogamente alla serializzazione in XML Schema Definition (XSD); ad esempio, il nome "Order Details" diventa "Order_x0020_Details". Allo stesso modo, gli elementi `ColumnID` e `TableID` contenuti nell'elemento `ColumnBinding` e che fanno riferimento a oggetti nella vista origine dati devono codificare anch'essi i nomi durante la serializzazione, per garantire che tali nomi corrispondano direttamente al testo nella vista origine dati. L'istanza di Analysis Services decodificherà tali nomi operando analogamente al modello a oggetti `DataSet`.  
  
 Un elemento `TableDefinitions` contenuto in un elemento che utilizza il tipo di dati `TableBinding` e che fa riferimento a tabelle nella vista origine dati deve inoltre codificare i nomi in base alla serializzazione nella vista origine dati. I nomi di tabella nelle associazioni `Partition`, tuttavia, non devono essere codificati, in quanto tali nomi sono nomi di tabella presenti nel database e non devono essere inclusi nella vista origine dati. La mancata codifica dei nomi di tabella nelle associazioni `Partition` consente inoltre di ottenere i seguenti risultati:  
  
-   Mantiene più semplice la libreria di definizione dei dati (DDL) per le partizioni.  
  
-   Fornisce maggiore consistenza, in quanto le partizioni possono avere un nome di tabella o un'istruzione SELECT, e l'istruzione SELECT non deve essere codificata.  
  
 I nomi di tabella e di colonna non includono delimitatori, ad esempio " [" per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Per ulteriori informazioni sul `Binding` tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del `Binding` tipo e la gerarchia di ereditarietà dei `Binding` tipi, vedere [tipo di dati Binding &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni dati in ASSL, vedere [origini dati e le associazioni &#40;multidimensionali SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti AMO è <xref:Microsoft.AnalysisServices.ColumnBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  