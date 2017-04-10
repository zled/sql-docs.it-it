---
title: "Funzione di aggregazione (Generatore report e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16ce643f-bbb3-40a5-ba78-7aed73156f3e
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Funzione di aggregazione (Generatore report e SSRS)
  Restituisce un'aggregazione personalizzata dell'espressione specificata, secondo quanto definito dal provider di dati.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Sintassi  
  
```  
  
Aggregate(expression, scope)  
```  
  
#### Parametri  
 *espressione*  
 Espressione su cui eseguire l'aggregazione. È necessario che l'espressione sia un riferimento di campo semplice.  
  
 *ambito*  
 (**Stringa**) Nome di un set di dati, gruppo o area dati che contiene gli elementi del report a cui applicare la funzione di aggregazione. *Ambito* deve essere una costante di tipo stringa e non può essere un'espressione. Se si omette *scope* , viene usato l'ambito corrente.  
  
## Tipo restituito  
 Il tipo restituito dipende dal provider di dati. Restituisce **Nothing** se il provider di dati non supporta questa funzione o se i dati non sono disponibili.  
  
## Osservazioni  
 La funzione **Aggregate** offre una modalità per usare aggregazioni calcolate sull'origine dati esterna. Il supporto per questa caratteristica è determinato dall'estensione dei dati. L'estensione dell'elaborazione dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ad esempio, consente di recuperare set di righe bidimensionali da una query MDX. Alcune righe del set di risultati possono contenere valori di aggregazione calcolati nel server dell'origine dati. Tali valori sono noti come *aggregazioni server*. Per visualizzare le aggregazioni server nella finestra Progettazione query con interfaccia grafica per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è possibile usare il pulsante **Mostra aggregazione** sulla barra degli strumenti. Per altre informazioni, vedere [Interfaccia utente di Progettazione query MDX di Analysis Services &#40;Generatore report &#41;](../Topic/Analysis%20Services%20MDX%20Query%20Designer%20User%20Interface%20\(Report%20Builder\).md).  
  
 Quando si visualizza la combinazione di valori di aggregazione e di set di dati di dettaglio nelle righe di dettaglio di un'area dati Tablix, le aggregazioni server non vengono solitamente incluse perché non corrispondono a dati di dettaglio. Tuttavia, è possibile visualizzare tutti i valori recuperati per il set di dati e personalizzare le modalità di calcolo e visualizzazione dei dati di aggregazione.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] rileva l'uso della funzione **Aggregate** nelle espressioni del report per determinare se visualizzare aggregazioni server nelle righe di dettaglio. Se si include **Aggregate** in un'espressione in un'area dati, le aggregazioni server possono essere visualizzate solo in righe di totali o totali complessivi di gruppo, non nelle righe di dettaglio. Se si desidera visualizzare le aggregazioni server nelle righe di dettaglio, non usare la funzione **Aggregate** .  
  
 È possibile cambiare questo comportamento predefinito modificando il valore dell'opzione **Interpretare i subtotali come righe di dettaglio** nella finestra di dialogo **Proprietà set di dati** . Quando questa opzione è impostata su **True**, tutti i dati, incluse le aggregazioni server, appaiono come dati di dettaglio. Quando è impostata su **False**, le aggregazioni server appaiono come totali. L'impostazione di questa proprietà influisce su tutte le aree dati collegate al set di dati.  
  
> [!NOTE]  
>  Tutti i gruppi di contenuto per l'elemento del report che fa riferimento ad **Aggregate** devono includere riferimenti di campo semplici per le relative espressioni di raggruppamento, ad esempio `[FieldName]`. Non è possibile usare **Aggregate** in un'area dati che usa espressioni di raggruppamento complesse. Per l'estensione di elaborazione dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] la query deve includere campi MDX di tipo **LevelProperty** (non **MemberProperty**) per supportare l'aggregazione con la funzione **Aggregate**.  
  
 *Expression* può contenere chiamate alle funzioni di aggregazione nidificate con le eccezioni e le condizioni seguenti:  
  
-   *Scope* per le aggregazioni nidificate deve corrispondere o essere contenuto nell'ambito dell'aggregazione esterna. Per tutti gli ambiti distinti nell'espressione, un ambito deve essere in una relazione figlio con tutti gli altri ambiti.  
  
-   *Scope* per le aggregazioni nidificate non può essere il nome di un set di dati.  
  
-   *Expression* non deve contenere funzioni **First**, **Last**, **Previous**o **RunningValue** .  
  
-   *Expression* non deve contenere aggregazioni nidificate che specificano *recursive*.  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md).  
  
 Per altre informazioni sulle aggregazioni ricorsive, vedere [Creazione di gruppi di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## Confronto tra le funzioni Aggregate e Sum  
 La funzione **Aggregate** è diversa dalle funzioni di aggregazioni numeriche come **Sum** in quanto la funzione **Aggregate** restituisce un valore calcolato dal provider di dati o dall'estensione per l'elaborazione dati. Le funzioni di aggregazione numeriche come **Sum** restituiscono invece un valore calcolato dal componente Elaborazione report in un set di dati determinato dal parametro *scope* . Per altre informazioni, vedere le funzioni di aggregazione elencate in [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md).  
  
## Esempio  
 Nell'esempio di codice seguente è illustrata un'espressione che recupera un'aggregazione server per il campo `LineTotal`. L'espressione viene aggiunta nella riga di una cella che appartiene al gruppo `GroupbyOrder`.  
  
```  
=Aggregate(Fields!LineTotal.Value, "GroupbyOrder")  
```  
  
## Vedere anche  
 [Utilizzo delle espressioni nei report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  