---
title: Il tipo di dati TableBinding (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
apiname: TableBinding Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TableBinding
helpviewer_keywords: TableBinding data type
ms.assetid: 3195dca4-82bf-46b7-a31f-5383586e3573
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0d3e255d968e95d71813d28d71d12fb7284eb4fb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="tablebinding-data-type-assl"></a>Tipo di dati TableBinding (ASSL)
  Definisce un tipo di dati derivato che rappresenta un'associazione a una tabella.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<TableBinding>  
   <!-- The following elements extend TabularBinding -->  
   <DataSourceID>...</DataSourceID>  
   <DbTableName>...</DbTableName>  
   <DbSchemaName>...</DbSchemaName>  
</TableBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|[TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[DataSourceID](../../../analysis-services/scripting/properties/datasourceid-element-assl.md), [DbSchemaName](../../../analysis-services/scripting/properties/dbschemaname-element-assl.md), [DbTableName](../../../analysis-services/scripting/properties/dbtablename-element-assl.md)|  
|Elementi derivati|Vedere [associazione](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Se si fa riferimento ad altre tabelle nell'espressione di filtro tramite una selezione secondaria, è possibile che le prestazioni in alcune origini dati risultino ridotte. La finestra di progettazione può tuttavia controllare completamente l'espressione SQL tramite la definizione di una query denominata nella vista origine dati da utilizzare come riferimento.  
  
 Il metodo di definizione delle associazioni per una partizione è indipendente dall'utilizzo di tabelle partizionate nella vista origine dati.  
  
 Si consideri, ad esempio, un gruppo di misure la cui tabella predefinita "Sales" contiene le colonne Date, Product ID, Qty, Price e Amount calcolate nella vista origine dati. In questo caso, la partizione "Sales97" può utilizzare la tabella "Sales97" con il filtro "Year(Sales.Date) = 97".  
  
 La query effettiva sarà la seguente:  
  
```  
SELECT Date, Product ID, Qty, Price, Qty * Price AS Amount   
   FROM Sales97 As Sales  
   WHERE Year(Sales.Date) = 97  
```  
  
 L'espressione calcolata si applica comunque, anche se l'espressione utilizza nomi di tabella qualificati, ad esempio Sales.Qty. Lo stesso vale se invece la tabella viene sostituita da una query "SELECT..." La clausola FROM precedente diventerà "da SELECT... As Sales".  
  
 Per ulteriori informazioni sul **associazione** tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) di tipo **associazione** e gerarchia di ereditarietà di **associazione** tipi, vedere [associazione tipo di dati &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni dati in ASSL, vedere [origini dati e associazioni &#40; SSAS multidimensionale &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.TableBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Origini dati e associazioni &#40; SSAS multidimensionale &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Analysis Services Scripting Language tipi di dati XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
