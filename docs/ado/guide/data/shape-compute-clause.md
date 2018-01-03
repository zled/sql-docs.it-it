---
title: Forma clausola COMPUTE | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shape commands [ADO]
- compute clause [ADO]
- data shaping [ADO], COMPUTE clause
ms.assetid: 3fdfead2-b5ab-4163-9b1d-3d2143a5db8c
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0c20aec7585c33a7165fac4e93b446e4ce3aaf4e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="shape-compute-clause"></a>Clausola COMPUTE forma
Una clausola COMPUTE forma genera un elemento padre **Recordset**, le cui colonne sono costituiti da un riferimento al figlio **Recordset**; facoltativo colonne il cui contenuto è capitolo, nuovo, o le colonne calcolate, o risultato dell'esecuzione di funzioni di aggregazione sull'elemento figlio **Recordset** o una forma precedentemente **Recordset**; e tutte le colonne dal figlio **Recordset** elencate parametro facoltativo nella clausola.  
  
## <a name="syntax"></a>Sintassi  
  
```  
SHAPE child-command [AS] child-alias  
   COMPUTE child-alias [[AS] name], [appended-column-list]  
   [BY grp-field-list]  
```  
  
## <a name="description"></a>Description  
 Le parti di questa clausola sono come segue:  
  
 *comando figlio*  
 È costituita da uno dei seguenti:  
  
-   Un comando di query all'interno delle parentesi graffe ("{") che restituisce un elemento figlio **Recordset** oggetto. Il comando viene immesso al provider di dati sottostante e la relativa sintassi dipende dai requisiti del provider. Ciò corrisponderà in genere il linguaggio SQL, anche se ADO non richieda qualsiasi linguaggio di query specifico.  
  
-   Il nome di un oggetto esistente a forma di **Recordset**.  
  
-   Un altro comando shape.  
  
-   La parola chiave nella tabella, seguita dal nome di una tabella nel provider di dati.  
  
 *alias di figlio*  
 Un alias utilizzato per fare riferimento al **Recordset** restituito dal *comando figlio.* Il *figlio alias* è obbligatoria nell'elenco di colonne nella clausola COMPUTE e definisce la relazione tra padre e figlio **Recordset** oggetti.  
  
 *elenco di colonne aggiunte*  
 Un elenco in cui ogni elemento definisce una colonna nell'elemento padre generato. Ogni elemento contiene una colonna a capitoli, una nuova colonna, una colonna calcolata o un valore risultante da una funzione di aggregazione sull'elemento figlio **Recordset**.  
  
 *elenco di campi di gruppo*  
 Un elenco di colonne padre e figlio **Recordset** gli oggetti che specifica la modalità di raggruppamento delle righe nell'elemento figlio.  
  
 Per ogni colonna di *gruppo-field-list,* è una colonna corrispondente nel padre e figlio **Recordset** oggetti. Per ogni riga dell'elemento padre **Recordset**, *elenco di campi di gruppo* le colonne hanno valori univoci e il figlio **Recordset** a cui fa riferimento l'elemento padre riga è costituito esclusivamente da figlio le righe il cui *elenco di campi gruppo* le colonne hanno gli stessi valori di riga padre.  
  
 Se la clausola BY viene inclusa, l'elemento figlio **Recordset**di righe verranno raggruppate in base alle colonne nella clausola COMPUTE. L'elemento padre **Recordset** conterrà una riga per ogni gruppo di righe nell'elemento figlio **Recordset**.  
  
 Se la clausola BY viene omessa, l'intero figlio **Recordset** viene considerato come un singolo gruppo e l'elemento padre **Recordset** conterrà esattamente una riga. Tale riga farà riferimento intero figlio **Recordset**. Omettere la clausola BY consente di calcolare le aggregazioni di "totale complessivo" sull'intero figlio **Recordset**.  
  
 Ad esempio  
  
```  
SHAPE {select * from Orders} AS orders             COMPUTE orders, SUM(orders.OrderAmount) as TotalSales         
```  
  
 Indipendentemente dalla modalità padre **Recordset** è del formato (utilizzando COMPUTE o APPEND), contiene una colonna capitolo che viene utilizzata per essere correlata a un elemento figlio **Recordset**. Se si desidera, l'elemento padre **Recordset** può inoltre includere le colonne che contengono funzioni di aggregazione (SUM, MIN, MAX e così via) sulle righe figlio. Sia l'elemento padre e figlio **Recordset** possono contenere colonne che contengono un'espressione sulla riga di **Recordset**, nonché le colonne che sono nuovi e inizialmente vuota.  
  
## <a name="operation"></a>Operazione  
 Il *comando figlio* viene rilasciato al provider, che restituisce un elemento figlio **Recordset**.  
  
 La clausola COMPUTE specifica le colonne dell'elemento padre **Recordset**, che può essere un riferimento al figlio **Recordset**, una o più aggregazioni, un'espressione calcolata o nuove colonne. Se è presente una clausola BY, le colonne definisce inoltre vengono aggiunti all'elemento padre **Recordset**. Specifica la clausola BY come le righe dell'elemento figlio **Recordset** sono raggruppati.  
  
 Si supponga, ad esempio, che si dispone di una tabella, denominata dati demografici, che include i campi di stato, città e popolamento. (Le cifre di popolamento della tabella vengono fornite esclusivamente come esempio).  
  
|State|Città|Popolazione|  
|-----------|----------|----------------|  
|WA|Seattle|700,000|  
|o|Medford|200,000|  
|o|Portland|400,000|  
|CA|Los Angeles|800,000|  
|CA|San Diego|600,000|  
|WA|Tacoma|500,000|  
|o|Corvallis|300,000|  
  
 A questo punto, eseguire questo comando forma:  
  
```  
rst.Open  "SHAPE {select * from demographics} AS rs "  & _  
          "COMPUTE rs, SUM(rs.population) BY state", _  
           objConnection  
```  
  
 Questo comando apre una forma **Recordset** con due livelli. Il livello padre è un oggetto generato **Recordset** con una colonna aggregata (`SUM(rs.population)`), una colonna che fa riferimento il figlio **Recordset** (`rs`) e una colonna per il raggruppamento figlio **Recordset** (`state`). Il livello figlio è il **Recordset** restituito dal comando di query (`select * from demographics`).  
  
 L'elemento figlio **Recordset** righe di dettaglio saranno raggruppati per stato, ma in caso contrario, in nessun ordine particolare. I gruppi, ovvero non saranno in ordine alfabetico o numerico. Se si desidera che l'elemento padre **Recordset** per essere ordinati, è possibile utilizzare il **ordinamento Recordset** metodo per ordinare l'elemento padre **Recordset**.  
  
 È ora possibile passare l'elemento padre di aperto **Recordset** e accedere ai dettagli figlio **Recordset** oggetti. Per ulteriori informazioni, vedere [accesso alle righe in un Recordset gerarchico](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
## <a name="resultant-parent-and-child-detail-recordsets"></a>Risultante padre e figlio dettaglio Recordset  
  
### <a name="parent"></a>Parent  
  
|SUM (Reporting Services. Popolamento)|rs|State|  
|---------------------------|--------|-----------|  
|1,300,000|Riferimento a child1|CA|  
|1,200,000|Riferimento a child2|WA|  
|1,100,000|Riferimento a child3|o|  
  
## <a name="child1"></a>Child1  
  
|State|Città|Popolazione|  
|-----------|----------|----------------|  
|CA|Los Angeles|800,000|  
|CA|San Diego|600,000|  
  
## <a name="child2"></a>Child2  
  
|State|Città|Popolazione|  
|-----------|----------|----------------|  
|WA|Seattle|700,000|  
|WA|Tacoma|500,000|  
  
## <a name="child3"></a>Child3  
  
|State|Città|Popolazione|  
|-----------|----------|----------------|  
|o|Medford|200,000|  
|o|Portland|400,000|  
|o|Corvallis|300,000|  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso alle righe in un Recordset gerarchico](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Data Shaping Panoramica](../../../ado/guide/data/data-shaping-overview.md)   
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)   
 [Grammatica formale forma](../../../ado/guide/data/formal-shape-grammar.md)   
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Provider desiderati per il Data Shaping](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Clausola APPEND forma](../../../ado/guide/data/shape-append-clause.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)   
 [Valore proprietà (ADO)](../../../ado/reference/ado-api/value-property-ado.md)   
 [Funzioni di Visual Basic, Applications Edition](../../../ado/guide/data/visual-basic-for-applications-functions.md)
