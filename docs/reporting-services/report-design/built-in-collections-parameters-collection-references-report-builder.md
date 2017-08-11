---
title: Riferimenti alla raccolta di parametri (Generatore Report e SSRS) | Documenti Microsoft
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
ms.assetid: c4b47e15-0484-4c13-9182-898db825f01f
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 17698a3c268e824d2f638042b71b3ec21f994e86
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="built-in-collections---parameters-collection-references-report-builder"></a>Raccolte predefinite - riferimenti alla raccolta di parametri (Generatore Report)
  I parametri di un report sono una delle raccolte predefinite a cui è possibile fare riferimento da un'espressione. Includendo parametri in un'espressione, è possibile personalizzare i dati e l'aspetto dei report in base alle opzioni scelte da un utente. Le espressioni possono essere utilizzate per qualsiasi proprietà di elemento di report o una proprietà casella di testo che fornisce il (*Fx*) o \< **espressione**> opzione. Le espressioni vengono anche utilizzate per controllare il contenuto e l'aspetto dei report in altri modi. Per altre informazioni, vedere [Esempi di espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md).  
  
 Quando si confrontano i valori dei parametri con i valori dei campi di set di dati in fase di esecuzione, i tipi di dati per i due elementi confrontati devono essere identici. I parametri dei report possono essere dei tipi seguenti: Boolean, DateTime, Integer, Float o Text, che rappresenta il tipo di dati stringa sottostante. Può essere necessario convertire il tipo di dati del valore del parametro in base al valore del set di dati. Per altre informazioni, vedere [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md).  
  
 Per includere un riferimento a un parametro in un'espressione, è necessario essere in grado di specificare la sintassi corretta per tale riferimento, che varia a seconda che il parametro sia a valore singolo o multivalore.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="Single"></a> Utilizzo di un parametro a valore singolo in un'espressione  
 Nella tabella seguente sono riportati esempi della sintassi da utilizzare quando si include in un'espressione un riferimento a un parametro a valore singolo di un tipo di dati qualsiasi.  
  
|Esempio|Description|  
|-------------|-----------------|  
|`=Parameters!` *\<Nomeparametro >*`.IsMultiValue`|Restituisce **False**.<br /><br /> Verifica se un parametro è multivalore. Se è **True**, il parametro è multivalore ed è costituito da una raccolta di oggetti. Se è **False**, il parametro è a valore singolo ed è costituito da un solo oggetto.|  
|`=Parameters!` *\<Nomeparametro >*`.Count`|Restituisce il valore intero 1. Per un parametro a valore singolo, il conteggio è sempre 1.|  
|`=Parameters!` *\<Nomeparametro >*`.Label`|Restituisce l'etichetta del parametro, utilizzata di frequente come nome visualizzato in un elenco a discesa di valori disponibili.|  
|`=Parameters!` *\<Nomeparametro >*`.Value`|Restituisce il valore del parametro. Se la proprietà Etichetta non è stata impostata, questo valore verrà visualizzato nell'elenco a discesa dei valori disponibili.|  
|`=CStr(Parameters!`  *\<Nomeparametro >*`.Value)`|Restituisce il valore del parametro sotto forma di stringa.|  
|`=Fields(Parameters!` *\<Nomeparametro >*`.Value).Value`|Restituisce il valore del campo il cui nome è uguale a quello del parametro.|  
  
 Per altre informazioni sull'uso dei parametri in un filtro, vedere [Aggiungere filtri per set di dati, aree dati e gruppi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md).  
  
##  <a name="Multi"></a> Utilizzo di un parametro multivalore in un'espressione  
 Nella tabella seguente sono riportati esempi della sintassi da utilizzare quando si include in un'espressione un riferimento a un parametro multivalore di un tipo di dati qualsiasi.  
  
|Esempio|Description|  
|-------------|-----------------|  
|`=Parameters!` *\<MultivalueParameterName >*`.IsMultiValue`|Restituisce **True** o **False**.<br /><br /> Verifica se un parametro è multivalore. Se è **True**, il parametro è multivalore ed è costituito da una raccolta di oggetti. Se è **False**, il parametro è a valore singolo ed è costituito da un solo oggetto.|  
|`=Parameters!` *\<MultivalueParameterName >*`.Count`|Restituisce un valore intero.<br /><br /> Fa riferimento al numero di valori. Per un parametro a valore singolo, il conteggio è sempre 1. Per un parametro multivalore, il conteggio è 0 o maggiore di zero.|  
|`=Parameters!` *\<MultivalueParameterName >*`.Value(0)`|Restituisce il primo valore di un parametro multivalore.|  
|`=Parameters!` *\<MultivalueParameterName >* `.Value(Parameters!`  *\<MultivalueParameterName >*`.Count-1)`|Restituisce l'ultimo valore di un parametro multivalore.|  
|`=Split("Value1,Value2,Value3",",")`|Restituisce una matrice di valori.<br /><br /> Creare una matrice di valori per un parametro multivalore di tipo **Stringa** . È possibile utilizzare qualsiasi delimitatore nel secondo parametro per dividere. È possibile utilizzare questa espressione per impostare i valori predefiniti di un parametro multivalore oppure creare un parametro multivalore da inviare a un sottoreport o a un report drill-through.|  
|`=Join(Parameters!` *\<MultivalueParameterName >*`.Value,", ")`|Restituisce un oggetto **Stringa** costituito da un elenco di valori delimitati da virgole in un parametro multivalore. È possibile utilizzare qualsiasi delimitatore nel secondo parametro per unire.|  
  
 Per ulteriori informazioni sull'utilizzo di parametri in un filtro, vedere [i parametri di Report &#40; Generatore report e progettazione Report &#41; ](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Filtri di uso comune &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/commonly-used-filters-report-builder-and-ssrs.md)   
 [Aggiungere, modificare o eliminare un parametro di Report &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)   
 [Esercitazione: Aggiungere un parametro di Report &#40; Generatore report &#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Esercitazioni di Generatore report](../../reporting-services/report-builder-tutorials.md)   
 [Raccolte predefinite nelle espressioni &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md)  
  
  
