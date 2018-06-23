---
title: Utilizzo dell'istruzione DRILLTHROUGH per recuperare i dati di origine (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9869be182f398df326c0c81b7e00e869f0b3eae6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054390"
---
# <a name="using-drillthrough-to-retrieve-source-data-mdx"></a>Utilizzo dell'istruzione DRILLTHROUGH per il recupero di dati di origine (MDX)
  Nel linguaggio MDX (Multidimensional Expressions) è disponibile l'istruzione [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough), che consente di recuperare un set di righe dai dati di origine per una cella di un cubo.  
  
 Per eseguire un'istruzione `DRILLTHROUGH` su un cubo, è necessario definire un'azione drill-through per tale cubo. Per definire un'azione drill-through, in Progettazione cubi di [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]nel riquadro **Azioni** fare clic sul pulsante **Nuova azione drill-through**della barra degli strumenti. Nella nuova azione drill-through specificare il nome, la destinazione e la condizione dell'azione, nonché le colonne restituite dall'istruzione `DRILLTHROUGH`.  
  
## <a name="drillthrough-statement-syntax"></a>Sintassi dell'istruzione DRILLTHROUGH  
 Il `DRILLTHROUGH` istruzione utilizza la sintassi seguente:  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 Il `SELECT` clausola identifica la cella del cubo che contiene i dati di origine da recuperare. Questa clausola `SELECT` è identica a una normale istruzione `SELECT` MDX, con la differenza che in questo caso nella clausola `SELECT` è possibile specificare solo un membro per ogni asse. Se su un asse sono specificati più membri, verrà generato un errore.  
  
 La sintassi `<Max_Rows>` specifica il numero massimo di righe in ogni set di righe restituito. Se il provider OLE DB utilizzato per connettersi all'origine dei dati non supporta `DBPROP_MAXROWS`, l'impostazione `<Max_Rows>` verrà ignorata.  
  
 La sintassi `<First_Rowset>` identifica la partizione il cui set di righe viene restituito per primo.  
  
 La sintassi `<Return_Columns>` identifica le colonne del database sottostante da restituire.  
  
## <a name="drillthrough-statement-example"></a>Esempio di istruzione DRILLTHROUGH  
 Nell'esempio seguente illustra l'uso del `DRILLTHROUGH` istruzione. In questo esempio l'istruzione DRILLTHROUGH esegue una query sugli elementi foglia delle dimensioni Store, Product e Time, lungo la dimensione Stores (l'asse di sezionamento), e quindi restituisce il gruppo di misure del reparto, l'ID del reparto e il nome del dipendente.  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [La modifica dei dati &#40;MDX&#41;](mdx-data-manipulation-manipulating-data.md)  
  
  
