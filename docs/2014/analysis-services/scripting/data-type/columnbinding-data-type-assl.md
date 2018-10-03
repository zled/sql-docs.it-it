---
title: Tipo di dati ColumnBinding (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 271b4ae8b305e554f94bd1b0da3bbed96a7dd476
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149341"
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
|Tipi di dati di base|[associazione](binding-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[ColumnID](../properties/columnid-element-eventcolumn-assl.md), [TableID](../properties/id-element-assl.md)|  
|Elementi derivati|Vedere [associazione](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Note  
 Per creare nomi di elemento XML validi, [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] `DataSet` oggetti codificano i nomi di tabella Analogamente alla serializzazione di XML Schema Definition (XSD); ad esempio, il nome "Order Details" diventa "Order_x0020_Details". Allo stesso modo, gli elementi `ColumnID` e `TableID` contenuti nell'elemento `ColumnBinding` e che fanno riferimento a oggetti nella vista origine dati devono codificare anch'essi i nomi durante la serializzazione, per garantire che tali nomi corrispondano direttamente al testo nella vista origine dati. L'istanza di Analysis Services decodificherà tali nomi operando analogamente al modello a oggetti `DataSet`.  
  
 Un elemento `TableDefinitions` contenuto in un elemento che utilizza il tipo di dati `TableBinding` e che fa riferimento a tabelle nella vista origine dati deve inoltre codificare i nomi in base alla serializzazione nella vista origine dati. I nomi di tabella nelle associazioni `Partition`, tuttavia, non devono essere codificati, in quanto tali nomi sono nomi di tabella presenti nel database e non devono essere inclusi nella vista origine dati. La mancata codifica dei nomi di tabella nelle associazioni `Partition` consente inoltre di ottenere i seguenti risultati:  
  
-   Mantiene più semplice la libreria di definizione dei dati (DDL) per le partizioni.  
  
-   Fornisce maggiore consistenza, in quanto le partizioni possono avere un nome di tabella o un'istruzione SELECT, e l'istruzione SELECT non deve essere codificata.  
  
 I nomi di tabella e di colonna non includono delimitatori, ad esempio " [" per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Per altre informazioni sul `Binding` tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del `Binding` tipo e la gerarchia di ereditarietà dei `Binding` tipi, vedere [associazione tipo di dati &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni di dati in ASSL, vedere [origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti AMO è <xref:Microsoft.AnalysisServices.ColumnBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
