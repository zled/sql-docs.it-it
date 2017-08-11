---
title: Esempi di equazioni (Generatore Report e SSRS) filtrare | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filtering data [Reporting Services], filter equation examples
ms.assetid: 66bec93d-7c3b-4d4a-8cb6-7a7bb2f34ec6
caps.latest.revision: 18
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e6bbd95ac20afbeb00b331efa13492a0036fff20
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="filter-equation-examples-report-builder-and-ssrs"></a>Esempi di equazioni di filtro (Generatore report e SSRS)
  Per creare un filtro è necessario specificare una o più equazioni di filtro. Un'equazione di filtro include un'espressione, un tipo di dati, un operatore e un valore. In questo argomento vengono forniti esempi di filtri di uso comune.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a>Esempi di filtri  
 Nella tabella seguente sono riportati esempi di equazioni di filtro che utilizzano tipi di dati e operatori differenti. L'ambito per il confronto è determinato dall'elemento del report per il quale è definito il filtro. Per un filtro definito in un set di dati, ad esempio, **TOP% 10** si riferisce al primo 10 percento di valori nel set di dati. Per un filtro definito in un gruppo, **TOP% 10** rappresenta il primo 10 percento di valori nel gruppo.  
  
|Espressione semplice|Tipo di dati|Operatore|Value|Description|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|**Integer**|**>**|`7`|Sono inclusi valori di dati maggiori di 7.|  
|`[SUM(Quantity)]`|**Integer**|**TOP N**|`10`|Include i primi 10 valori di dati.|  
|`[SUM(Quantity)]`|**Integer**|**TOP %**|`20`|Include il primo 20% di valori di dati.|  
|`[Sales]`|**Text**|**>**|`=CDec(100)`|Include tutti i valori di tipo System.Decimal (tipi di dati "money" in SQL) maggiori di 100 dollari.|  
|`[OrderDate]`|**DateTime**|**>**|`2008-01-01`|Include tutte le date dal 1 gennaio 2008 alla data corrente.|  
|`[OrderDate]`|**DateTime**|**BETWEEN**|`2008-01-01`<br /><br /> `2008-02-01`|Include le date dal 1 gennaio 2008 al 1 febbraio 2008 compreso.|  
|`[Territory]`|**Text**|**LIKE**|`*east`|Tutti i nomi di territorio che terminano in "east".|  
|`[Territory]`|**Text**|**LIKE**|`%o%th*`|Tutti i nomi di territorio che iniziano con North e South.|  
|`=LEFT(Fields!Subcat.Value,1)`|**Text**|**IN**|`B, C, T`|Tutti i valori di sottocategoria che iniziano con la lettera B, C o T.|  
  
## <a name="see-also"></a>Vedere anche  
 [I parametri di report &#40; Generatore report e progettazione Report &#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Aggiungere i filtri di set di dati, i filtri di area dati e i filtri di gruppo &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Tipi di dati in espressioni &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Utilizzo delle espressioni nei report &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)  
  
  
