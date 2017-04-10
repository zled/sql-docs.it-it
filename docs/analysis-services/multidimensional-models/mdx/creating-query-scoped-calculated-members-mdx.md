---
title: "Creazione di membri calcolati con ambito query (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WITH, parola chiave"
  - "membri calcolati con ambito query [MDX]"
ms.assetid: c4507149-e67b-4e5d-9192-cc911acd9adc
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Creazione di membri calcolati con ambito query (MDX)
  Se un membro calcolato è necessario solo per un'unica query MDX (Multidimensional Expression), è possibile definire tale membro calcolato mediante la parola chiave WITH. Un membro calcolato creato utilizzando la parola chiave WITH non esisterà più al termine dell'esecuzione della query.  
  
 Come illustrato in questo argomento, la sintassi della parola chiave WITH è molto flessibile e consente addirittura di basare un membro calcolato su un altro membro calcolato.  
  
> [!NOTE]  
>  Per altre informazioni sui membri calcolati, vedere [Compilazione di membri calcolati in MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/building-calculated-members-in-mdx-mdx.md).  
  
## Sintassi della parola chiave WITH  
 Utilizzare la sintassi seguente per aggiungere la parola chiave WITH a un'istruzione SELECT MDX:  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ] SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]FROM <SELECT subcube clause> [ <SELECT slicer axis clause> ][ <SELECT cell property list clause> ]  
<SELECT WITH clause> ::=  
   ( [ CALCULATED ] MEMBER <CREATE MEMBER body clause>) | <CREATE MEMBER body clause> ::= Member_Identifier AS 'MDX_Expression'  
   [ <CREATE MEMBER property clause> [ , <CREATE MEMBER property clause> ... ] ]  
<CREATE MEMBER property clause> ::=  
   ( MemberProperty_Identifier = Scalar_Expression )  
  
```  
  
 Nella sintassi della parola chiave WITH il valore `Member_Identifier` rappresenta il nome completo del membro calcolato. Il nome completo include la dimensione o il livello a cui è associato il membro calcolato. Il valore `MDX_Expression` restituisce il valore del membro calcolato dopo la valutazione del valore dell'espressione. È possibile specificare i valori delle proprietà della cella intrinseche per un membro calcolato, se si desidera, indicando il nome della proprietà della cella nel valore `MemberProperty_Identifier` e il valore della proprietà della cella nel valore `Scalar_Expression` .  
  
## Esempi di parola chiave WITH  
 La query MDX seguente definisce un membro calcolato, `[Measures].[Special Discount]`, che esegue il calcolo di uno sconto speciale in base all'importo dello sconto originale.  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 È inoltre possibile creare membri calcolati in un punto qualsiasi di una gerarchia. La query MDX seguente, ad esempio, definisce il membro calcolato `[BigSeller]` per un cubo Sales ipotetico. Questo membro calcolato determina se un particolare punto vendita ha registrato almeno 100,00 nelle vendite unitarie di birra e vino. La query, tuttavia, crea il membro calcolato `[BigSeller]` non come membro figlio della dimensione `[Product]` ma come membro figlio del membro `[Beer and Wine]` .  
  
```  
WITH   
   MEMBER [Product].[Beer and Wine].[BigSeller] AS  
  IIf([Product].[Beer and Wine] > 100, "Yes","No")  
SELECT  
   {[Product].[BigSeller]} ON COLUMNS,  
   Store.[Store Name].Members ON ROWS  
FROM Sales  
  
```  
  
 I membri calcolati non devono necessariamente dipendere solo dai membri esistenti in un cubo. Un membro calcolato può inoltre basarsi su altri membri calcolati definiti nella stessa espressione MDX. La query MDX seguente, ad esempio, utilizza il valore creato nel primo membro calcolato, `[Measures].[Special Discount]`, per generare il valore del secondo membro calcolato, `[Measures].[Special Discounted Amount]`.  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Percentage] * 1.5,   
   FORMAT_STRING = 'Percent'  
  
   MEMBER [Measures].[Special Discounted Amount] AS  
   [Measures].[Reseller Average Unit Price] * [Measures].[Special Discount],   
   FORMAT_STRING = 'Currency'  
  
SELECT   
   {[Measures].[Special Discount], [Measures].[Special Discounted Amount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
  
```  
  
## Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)   
 [Istruzione SELECT &#40;MDX&#41;](../Topic/SELECT%20Statement%20\(MDX\).md)   
 [Creazione di membri calcolati con ambito sessione &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-session-scoped-calculated-members-mdx.md)  
  
  