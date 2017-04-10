---
title: "Funzione Level (Generatore report e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Funzione Level (Generatore report e SSRS)
  Restituisce il livello di nidificazione corrente in una gerarchia ricorsiva.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Sintassi  
  
```  
  
Level(scope)  
```  
  
#### Parametri  
 *ambito*  
 (**String**) Facoltativo. Nome di un set di dati, gruppo o area dati che contiene gli elementi del report a cui applicare la funzione di aggregazione. Se si omette *scope* , viene usato l'ambito corrente.  
  
## Tipo restituito  
 Restituisce un valore **Integer**. Se il parametro *scope* specifica un set di dati o un'area dati oppure un raggruppamento non ricorsivo, ovvero un raggruppamento privo dell'elemento **Parent**, **Level** restituirà 0. Se *scope* viene omesso, restituisce il livello dell'ambito corrente.  
  
## Osservazioni  
 Il valore restituito dalla funzione **Level** è a base zero, ovvero il primo livello di una gerarchia viene indicato con 0.  
  
 È possibile utilizzare la funzione **Level** per consentire l'applicazione dei rientri in una gerarchia ricorsiva, ad esempio un elenco di dipendenti.  
  
 Per altre informazioni sulle gerarchie ricorsive, vedere [Creazione di gruppi di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## Esempio  
 L'esempio di codice seguente consente di ottenere il livello di riga nel gruppo Employees:  
  
```  
=Level("Employees")  
```  
  
## Vedere anche  
 [Utilizzo delle espressioni nei report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  