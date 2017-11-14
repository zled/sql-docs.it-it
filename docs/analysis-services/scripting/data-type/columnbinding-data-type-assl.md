---
title: Il tipo di dati ColumnBinding (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ColumnBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ColumnBinding
helpviewer_keywords:
- ColumnBinding data type
ms.assetid: 3ab1bac1-6716-4b17-a107-d5f9c744c5e6
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e93d9587957409df5678eac7f0d31df71d201532
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="columnbinding-data-type-assl"></a>Tipo di dati ColumnBinding (ASSL)
  Definisce un tipo di dati derivato che rappresenta l'associazione di una colonna in una vista origine dati per un [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ColumnBinding>  
   <!-- The following elements extend Binding -->  
   <TableID>...</TableID>  
      <ColumnID>...</ColumnID>  
</ColumnBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|[Associazione](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[ColumnID](../../../analysis-services/scripting/properties/columnid-element-eventcolumn-assl.md), [TableID](../../../analysis-services/scripting/properties/tableid-element-assl.md)|  
|Elementi derivati|Vedere [associazione](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Per creare nomi di elemento XML validi, [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] **DataSet** oggetti codificano i nomi di tabella Analogamente alla serializzazione in XML Schema Definition (XSD); ad esempio, il nome "Order Details" diventa "Order_x0020_Details". Analogamente, il **ColumnID** e **TableID** gli elementi contenuti dal **ColumnBinding** elemento e gli oggetti di riferimento nella vista origine dati (DSV) devono inoltre codificare nomi durante la serializzazione, per assicurarsi che i nomi corrispondano direttamente il testo della vista origine dati. Istanza di Analysis Services decodificherà tali nomi, come il **DataSet** modello a oggetti.  
  
 Oggetto **TableDefinitions** elemento contenuto in un elemento utilizzando il **TableBinding** tipo di dati e che fa riferimento a tabelle nella vista origine dati deve inoltre codificare i nomi di serializzazione in XSD. Tuttavia, i nomi di tabella nel **partizione** associazioni non devono essere codificate perché questi nomi sono semplicemente i nomi delle tabelle presenti nel database e non deve essere nella vista origine dati. Non codifica della tabella di nomi nel **partizione** associazioni si ottengono anche le operazioni seguenti:  
  
-   Mantiene più semplice la libreria di definizione dei dati (DDL) per le partizioni.  
  
-   Fornisce maggiore consistenza, in quanto le partizioni possono avere un nome di tabella o un'istruzione SELECT, e l'istruzione SELECT non deve essere codificata.  
  
 I nomi di tabella e di colonna non includono delimitatori, ad esempio " [" per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Per ulteriori informazioni sul **associazione** tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del **associazione** tipo e la gerarchia di ereditarietà dei  **Associazione** tipi, vedere [associazione tipo di dati &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni dati in ASSL, vedere [origini dati e associazioni &#40; SSAS multidimensionale &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti AMO è <xref:Microsoft.AnalysisServices.ColumnBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

