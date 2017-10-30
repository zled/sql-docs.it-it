---
title: Istruzione CREATE MEMBER (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_MEMBER
- CREATE MEMBER
- Member
- CREATE
dev_langs:
- kbMDX
helpviewer_keywords:
- CREATE MEMBER statement
- calculated members [MDX]
ms.assetid: 49379217-be2c-4139-a206-1168078b9b76
caps.latest.revision: 55
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6f3a183648dca9be0962559d15e2e5619480d930
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition---create-member"></a>Definizione dei dati MDX - creare membro
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un membro calcolato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE [ SESSION ] [HIDDDEN] [ CALCULATED ] MEMBER CURRENTCUBE | Cube_Name.Member_Name   
   AS MDX_Expression  
      [,Property_Name = Property_Value, ...n]  
......[,SCOPE_ISOLATION = CUBE]  
```  
  
## <a name="arguments"></a>Argomenti  
 *Cube_Name*  
 Espressione stringa valida che fornisce il nome del cubo in cui il membro verrà creato.  
  
 *Member_Name*  
 Espressione stringa valida che specifica il nome di un membro. Specificare un nome completo per creare un membro all'interno di una dimensione diversa da Measures. Se non si specifica un nome completo, il membro verrà creato nella dimensione Measures.  
  
 *MDX_Expression*  
 Espressione MDX (Multidimensional Expression) valida.  
  
 *Property_name*  
 Stringa valida che specifica il nome per la proprietà di un membro calcolato.  
  
 *Property_Value*  
 Espressione scalare valida che definisce il valore della proprietà di un membro calcolato.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione CREATE MEMBER definisce membri calcolati che rimangono disponibili per tutta la sessione e possono essere pertanto utilizzati in più query durante la sessione. Per ulteriori informazioni, vedere [membri calcolati Creating Session-Scoped &#40; MDX &#41; ](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md).  
  
 È inoltre possibile definire un membro calcolato da usare in un'unica query. Per definire un membro calcolato limitato a una singola query, è possibile usare la clausola WITH nell'istruzione SELECT. Per ulteriori informazioni, vedere [membri calcolati Creating Query-Scoped &#40; MDX &#41; ](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md).  
  
 *Property_name* può fare riferimento a una proprietà standard o facoltative membro calcolato. Le proprietà standard dei membri sono elencate di seguito in questo argomento. I membri calcolati creati con CREATE MEMBER senza un **sessione** valore hanno ambito sessione. Le stringhe contenute nelle definizioni dei membri calcolati sono delimitate da virgolette doppie, a differenza di quanto avviene con il metodo definito da OLE DB, che specifica che le stringhe devono essere delimitate da virgolette singole.  
  
 Specificando un cubo diverso dal cubo connesso viene generato un errore. Pertanto, per identificare il cubo corrente è consigliabile usare CURRENTCUBE anziché il nome di un cubo.  
  
 Per altre informazioni sulle proprietà dei membri definite da OLE DB, vedere la documentazione di OLE DB.  
  
## <a name="scope"></a>Ambito  
 I possibili ambiti di un membro calcolato sono elencati nella tabella seguente.  
  
 Ambito query  
 La visibilità e la durata del membro calcolato sono limitate alla query. Il membro calcolato è definito in una singola query. L'ambito query prevale sull'ambito sessione. Per ulteriori informazioni, vedere [membri calcolati Creating Query-Scoped &#40; MDX &#41; ](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md).  
  
 Ambito sessione  
 La visibilità e la durata del membro calcolato sono limitate alla sessione in cui è stato creato. Se sul membro calcolato viene utilizzata l'istruzione DROP MEMBER, la durata sarà inferiore alla durata della sessione. L'istruzione CREATE MEMBER crea un membro calcolato con ambito sessione.  
  
### <a name="scope-isolation"></a>Isolamento dell'ambito  
 Quando uno script MDX (Multidimensional Expressions) di un cubo contiene membri calcolati, per impostazione predefinita tali membri calcolati vengono risolti prima di tutti i calcoli con ambito di sessione e di tutti i calcoli definiti nelle query.  
  
> [!NOTE]  
>  In alcuni scenari, il [Aggregate (MDX)](../mdx/aggregate-mdx.md) funzione e [VisualTotals (MDX)](../mdx/visualtotals-mdx.md) funzione non esibiscono questo comportamento.  
  
 Il comportamento consente alle applicazioni client generiche di usare cubi contenenti calcoli complessi senza dover considerare l'implementazione specifica dei calcoli. Tuttavia, in alcuni scenari, è consigliabile eseguire sessione o i membri calcolati con ambito query prima di determinati calcoli nel cubo e né la **aggregazione** funzione né la **VisualTotals** funzione sono applicabili. A tale scopo, usare la proprietà di calcolo SCOPE_ISOLATION.  
  
#### <a name="example"></a>Esempio  
 Nello script seguente è illustrato un esempio di scenario in cui per ottenere il risultato corretto è necessaria la proprietà di calcolo SCOPE_ISOLATION.  
  
 **Script MDX del cubo:**  
  
```  
CREATE MEMBER CURRENTCUBE.Measures.ProfitRatio AS 'Measures.[Store Sales]/Measures.[Store Cost]', SOLVE_ORDER = 10  
```  
  
 **Query MDX:**  
  
```  
WITH MEMBER [Customer].[Customers].[USA]. USAWithoutWA AS  
[Customer].[Customers].[Country].&[USA] - [Customer].[Customers].[State Province.&[WA], SOLVE_ORDER=5  
SELECT {USAWithoutWA} ON 0 FROM SALES  
WHERE ProfitRatio  
```  
  
 Il risultato desiderato della query precedente è il rapporto delle vendite per gli Stati uniti escluso lo stato di Washington (WA), per archiviare i costi per tutti gli Stati Uniti tranne Washington. La query precedente non restituisce il risultato desiderato. Il risultato dato è il rapporto di USA meno il rapporto di WA, ovvero un risultato non significativo. Per ottenere il risultato desiderato, è possibile usare la proprietà di calcolo SCOPE_ISOLATION.  
  
 **Query MDX utilizzando la proprietà di calcolo SCOPE_ISOLATION:**  
  
```  
WITH MEMBER [Customer].[Customers].[USA]. USAWithoutWA AS  
[Customer].[Customers].[Country].&[USA] - [Customer].[Customers].[State Province.&[WA], SOLVE_ORDER=5  
,SCOPE_ISOLATION=CUBE  
SELECT {USAWithoutWA} ON 0 FROM SALES  
WHERE ProfitRatio  
```  
  
## <a name="standard-properties"></a>Proprietà standard  
 Ogni membro calcolato dispone di un set di proprietà predefinite. Quando un'applicazione client è connesso ad [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], le proprietà predefinite sono supportate o disponibili per essere supportate, come l'amministratore sceglie.  
  
 Possono essere disponibili ulteriori proprietà dei membri, a seconda della definizione del cubo. Le proprietà seguenti rappresentano informazioni riguardanti il livello delle dimensioni del cubo.  
  
|Identificatore proprietà|Significato|  
|-------------------------|-------------|  
|SOLVE_ORDER|L'ordine con cui deve essere risolto il membro calcolato nel caso in cui un membro calcolato faccia riferimento a un altro membro calcolato, ovvero, quando i membri calcolati si intersecano.|  
|FORMAT_STRING|Una stringa di formato in stile [!INCLUDE[msCoName](../includes/msconame-md.md)] Office che può essere utilizzata dall'applicazione client per la visualizzazione dei valori delle celle.|  
|VISIBLE|Un valore che indica se il membro calcolato è visibile in un set di righe dello schema. Visible calcolati i membri possono essere aggiunti a un set con il [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md) (funzione). Un valore diverso da zero indica che il membro calcolato è visibile. Il valore predefinito per questa proprietà è *Visible*.<br /><br /> I membri calcolati non visibili, per cui il valore è impostato su zero, vengono in genere utilizzati come passaggi intermedi in membri calcolati più complessi. A tali membri calcolati è possibile fare riferimento anche da altri tipi di membri, ad esempio le misure.|  
|NON_EMPTY_BEHAVIOR|La misura o il set utilizzato per determinare il comportamento dei membri calcolati durante la risoluzione delle celle vuote.<br /><br /> **\*\*Avviso \* \***  questa proprietà è deprecata. Evitare di impostarla. Per informazioni dettagliate, vedere [Funzionalità di Analysis Services deprecate in SQL Server 2016](../analysis-services/deprecated-analysis-services-features-in-sql-server-2016.md).|  
|CAPTION|Una stringa che l'applicazione client utilizza come didascalia per il membro.|  
|DISPLAY_FOLDER|Una stringa che identifica il percorso della cartella di visualizzazione che l'applicazione client utilizza per mostrarla al membro. Il separatore di livello delle cartelle è definito dall'applicazione client. Per gli strumenti e i client forniti da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], la barra rovesciata (\\) è il separatore di livello. Per fornire più cartelle di visualizzazione per un membro definito, utilizzare un punto e virgola (;) per separare le cartelle.|  
|ASSOCIATED_MEASURE_GROUP|Il nome del gruppo di misure al quale questo membro è associato.|  
  
## <a name="see-also"></a>Vedere anche  
 [DROP MEMBER-istruzione &#40; MDX &#41;](../mdx/mdx-data-definition-drop-member.md)   
 [Istruzione membro UPDATE &#40; MDX &#41;](../mdx/mdx-data-definition-update-member.md)   
 [Le istruzioni di definizione dei dati MDX &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  

