---
title: "Utilizzo dell&#39;istruzione DRILLTHROUGH per il recupero di dati di origine (MDX) | Microsoft Docs"
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
  - "istruzione DRILLTHROUGH"
  - "recupero di dati"
  - "query [MDX], istruzione DRILLTHROUGH"
  - "recupero di dati [MDX]"
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Utilizzo dell&#39;istruzione DRILLTHROUGH per il recupero di dati di origine (MDX)
  Nel linguaggio MDX (Multidimensional Expressions) è disponibile l'istruzione [DRILLTHROUGH](../Topic/DRILLTHROUGH%20Statement%20\(MDX\).md), che consente di recuperare un set di righe dai dati di origine per una cella di un cubo.  
  
 Per eseguire un'istruzione **DRILLTHROUGH** su un cubo, è necessario definire un'azione drill-through per tale cubo. Per definire un'azione drill-through, in Progettazione cubi di [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] nel riquadro **Azioni** fare clic sul pulsante **Nuova azione drill-through** della barra degli strumenti. Nella nuova azione drill-through specificare il nome, la destinazione e la condizione dell'azione, nonché le colonne restituite dall'istruzione **DRILLTHROUGH**.  
  
## Sintassi dell'istruzione DRILLTHROUGH  
 La sintassi dell'istruzione **DRILLTHROUGH** è la seguente:  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 La clausola **SELECT** identifica la cella del cubo che contiene i dati di origine da recuperare. Questa clausola **SELECT** è identica a una normale istruzione **SELECT** MDX, con la differenza che in questo caso nella clausola **SELECT** è possibile specificare solo un membro per ogni asse. Se su un asse sono specificati più membri, verrà generato un errore.  
  
 La sintassi `<Max_Rows>` specifica il numero massimo di righe in ogni set di righe restituito. Se il provider OLE DB uso per connettersi all'origine dati non supporta **DBPROP_MAXROWS**, l'impostazione `<Max_Rows>` verrà ignorata.  
  
 La sintassi `<First_Rowset>` identifica la partizione il cui set di righe viene restituito per primo.  
  
 La sintassi `<Return_Columns>` identifica le colonne del database sottostante da restituire.  
  
## Esempio di istruzione DRILLTHROUGH  
 Nell'esempio seguente viene illustrato l'uso dell'istruzione **DRILLTHROUGH**. In questo esempio l'istruzione DRILLTHROUGH esegue una query sugli elementi foglia delle dimensioni Store, Product e Time, lungo la dimensione Stores (l'asse di sezionamento), e quindi restituisce il gruppo di misure del reparto, l'ID del reparto e il nome del dipendente.  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## Vedere anche  
 [Manipolazione dei dati &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/manipulating-data-mdx.md)  
  
  