---
title: Il tipo di dati TableBinding (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 80055d443f0a08b7cc957d5fa26d458178d3a1f6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="tablebinding-data-type-assl"></a>Tipo di dati TableBinding (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
 Per ulteriori informazioni sul **associazione** tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) di tipo **associazione** e la gerarchia di ereditarietà dei **associazione** sui tipi, vedere [associazione tipo di dati &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni dati in ASSL, vedere [origini dati e associazioni & #40; SSAS multidimensionale & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.TableBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
