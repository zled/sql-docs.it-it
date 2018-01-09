---
title: Utilizzo di drill-through per recuperare i dati di origine (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1749970e49904d8788c08f8be29cd20d189ebca3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-manipulation---retrieve-source-data-using-drillthrough"></a>Manipolazione dei dati MDX - recuperare i dati di origine utilizzando il drill-through
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]MDX (Multidimensional Expressions) utilizza il [drill-through](../../../mdx/mdx-data-manipulation-drillthrough.md)istruzione per recuperare un set di righe dall'origine dei dati per una cella del cubo.  
  
 Per eseguire un'istruzione **DRILLTHROUGH** su un cubo, è necessario definire un'azione drill-through per tale cubo. Per definire un'azione drill-through, in Progettazione cubi di [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]nel riquadro **Azioni** fare clic sul pulsante **Nuova azione drill-through**della barra degli strumenti. Nella nuova azione drill-through specificare il nome, la destinazione e la condizione dell'azione, nonché le colonne restituite dall'istruzione **DRILLTHROUGH** .  
  
## <a name="drillthrough-statement-syntax"></a>Sintassi dell'istruzione DRILLTHROUGH  
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
  
## <a name="drillthrough-statement-example"></a>Esempio di istruzione DRILLTHROUGH  
 Nell'esempio seguente viene illustrato l'uso dell'istruzione **DRILLTHROUGH** . In questo esempio l'istruzione DRILLTHROUGH esegue una query sugli elementi foglia delle dimensioni Store, Product e Time, lungo la dimensione Stores (l'asse di sezionamento), e quindi restituisce il gruppo di misure del reparto, l'ID del reparto e il nome del dipendente.  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manipolazione dei dati &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-manipulating-data.md)  
  
  
