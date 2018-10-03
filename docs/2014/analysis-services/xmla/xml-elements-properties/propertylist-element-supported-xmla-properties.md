---
title: Proprietà XMLA (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- properties [XML for Analysis]
- XML for Analysis, properties
- XMLA, properties
ms.assetid: 5745f7b4-6b96-44d5-b77c-f2831a898e5e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7d7898c0f7263bf5355934ec072511bfd8483028
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48215921"
---
# <a name="supported-xmla-properties-xmla"></a>Proprietà XMLA supportate (XMLA)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta le proprietà elencate nella tabella seguente. È usare le proprietà elencate nella [delle proprietà](properties-element-xmla.md) elemento del [Discover](../xml-elements-methods-discover.md) e [Execute](../xml-elements-methods-execute.md) metodi.  
  
|nome|Elemento|  
|----------|-------------|  
|AxisFormat|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Determina il formato utilizzato in un' [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) set di risultati per descrivere gli assi del dataset multidimensionale. Questa proprietà può assumere i valori elencati nella tabella seguente.|  
  
|valore|Description|  
|-----------|-----------------|  
|*ClusterFormat*|Il `MDDataSet` asse è costituito da uno o più [CrossProduct](crossproduct-element-xmla.md) elementi.|  
|*CustomFormat*|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Usa il *TupleFormat* formato per questa impostazione.|  
|*TupleFormat*|(Impostazione predefinita) Il `MDDataSet` asse contiene uno o più [tupla](tuple-element-xmla.md) elementi.|  
  
 Questa proprietà può essere utilizzata con il metodo `Execute`.  
  
|nome|Elemento|  
|----------|-------------|  
|BeginRange|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Contiene un valore intero in base zero che corrisponde a un valore dell'attributo `CellOrdinal`. (Il `CellOrdinal` attributo fa parte del [cella](cell-element-mddataset-xmla.md) elemento il [CellData](celldata-element-xmla.md) sezione di `MDDataSet`.)<br /><br /> Se utilizzata insieme alla proprietà `EndRange`, questa proprietà può essere utilizzata dall'applicazione client per limitare un set di dati OLAP restituito da un comando a un intervallo specifico di celle. Se viene specificato il valore -1, vengono restituite tutte le celle fino a quella specificata nella proprietà `EndRange`.<br /><br /> Il valore predefinito per questa proprietà è -1.<br /><br /> Questa proprietà può essere utilizzata con il metodo `Execute`.|  
|Catalogo|*Utilizzo*<br /> Proprietà `String` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Quando si stabilisce una sessione con un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per inviare un comando XMLA, questa proprietà è equivalente alla proprietà OLE DB DBPROP_INIT_CATALOG.<br /><br /> Quando si imposta questa proprietà durante una sessione per modificare il database corrente per la sessione, questa proprietà è equivalente alla proprietà OLE DB DBPROP_CURRENTCATALOG.<br /><br /> Il valore predefinito di questa proprietà è una stringa vuota.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|CatalogLocation|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_CATALOGLOCATION.<br /><br /> Il valore predefinito di questa proprietà è zero (0), equivalente a DBPROPVAL_CL_START.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|ClientProcessID|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Contiene l'identificatore (ID) del thread di processo per la sessione corrente.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|CommitTimeout|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Determina il tempo di attesa, in secondi, da parte della fase di commit di un comando XMLA attualmente in esecuzione prima dell'esecuzione del rollback. La fase di commit corrisponde a comandi XMLA, ad esempio [istruzione](../xml-elements-commands/statement-element-xmla.md) oppure [processo](../xml-elements-commands/process-element-xmla.md).<br /><br /> Un valore zero (0) indica che l'istanza attende indefinitamente.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|Contenuto|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Determina il tipo di dati restituiti dai metodi `Discover` e `Execute`. Questa proprietà può assumere i valori elencati nella tabella seguente.|  
  
|valore|Description|  
|-----------|-----------------|  
|*Nessuno*|Consente la verifica della struttura del comando, ma non l'esecuzione.|  
|*Schema*|Restituisce XML Schema relativo al comando richiesto. XML Schema indica le colonne e altre informazioni.|  
|*Dati*|Restituisce solo i dati richiesti.|  
|*SchemaData*|(Impostazione predefinita) Restituisce i dati e le informazioni sullo schema.|  
  
 Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.  
  
|nome|Elemento|  
|----------|-------------|  
|Cube|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Contiene il nome del cubo che definisce il contesto per un comando. Se il comando stesso contiene il nome di un cubo, ad esempio all'interno della clausola FROM di una MDX (Multidimensional Expressions) [seleziona](/sql/mdx/mdx-data-manipulation-select) istruzione, l'impostazione di questa proprietà viene ignorata.<br /><br /> Il valore predefinito di questa proprietà è una stringa vuota.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DataSourceInfo|*Utilizzo*<br /> Proprietà `String` obbligatoria, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Contiene le informazioni, ad esempio il nome dell'istanza, necessarie per la connessione all'origine dati.<br /><br /> Le applicazioni client non devono costruire il contenuto della proprietà `DataSourceInfo` da inviare a un'istanza. Al contrario, l'applicazione client deve trovare le origini dati supportate dal provider tramite il `Discover` metodo per recuperare il [DISCOVER_DATASOURCES](../../schema-rowsets/xml/discover-datasources-rowset.md) set di righe. L'applicazione client restituisce quindi lo stesso valore per la proprietà `DataSourceInfo` recuperato dal client dal set di righe DISCOVER_DATASOURCES.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropCatalogTerm|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_CATALOGTERM.<br /><br /> Il valore predefinito di questa proprietà è "Database".<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropCatalogUsage|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_CATALOGUSAGE.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropColumnDefinition|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_COLUMNDEFINITION.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropConcatNullBehavior|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_CONCATNULLBEHAVIOR.<br /><br /> Il valore predefinito di questa proprietà è 1, equivalente a DBPROPVAL_CB_NULL.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropDataSourceReadOnly|*Utilizzo*<br /> Proprietà `Boolean` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_DATASOURCEREADONLY.<br /><br /> Il valore predefinito di questa proprietà è FALSE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropGroupBy|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_GROUPBY.<br /><br /> Il valore predefinito di questa proprietà è 2, equivalente a DBPROPVAL_GB_EQUALS_SELECT.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropHeterogeneousTables|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_HETEROGENEOUSTABLES.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropIdentifierCase|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_IDENTIFIERCASE.<br /><br /> Il valore predefinito di questa proprietà è 8, equivalente a DBPROPVAL_IC_MIXED.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropInitMode|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_INIT_MODE.<br /><br /> Gli unici valori supportati per questa proprietà sono DB_MODE_READWRITE e DB_MODE_READ.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMaxIndexSize|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_MAXINDEXSIZE.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMaxOpenChapters|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_MAXOPENCHAPTERS.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMaxRowSize|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_MAXROWSIZE.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMaxRowSizeIncludeBlob|*Utilizzo*<br /> Proprietà `Boolean` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_MAXROWSIZEINCLUDESBLOB.<br /><br /> Il valore predefinito di questa proprietà è TRUE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMaxTablesInSelect|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_MAXTABLESINSELECT.<br /><br /> Il valore predefinito per questa proprietà è 1.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMsmdAutoexists|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Determina il comportamento di Auto Exist. Questa proprietà può assumere i valori elencati nella tabella seguente.|  
  
|valore|Description|  
|-----------|-----------------|  
|*0*|Valore predefinito, equivale a 1.|  
|*1*|Applica Auto Exist complete per set denominati e assi di query. Include clausole WHERE e sub-SELECT.|  
|*2*|Applica Auto Exist complete per assi di query ed esclude set denominati da Auto Exist. Include clausole WHERE e sub-SELECT.|  
|*3*|Non applica Auto Exist per i set denominati con clausola WHERE. Applica Auto Exist superficiali per gli assi di query con clausola WHERE. Applica Auto Exist complete per assi di query con sub-SELECT e set denominati con sub-SELECT.|  
  
 I valori predefiniti di questa proprietà sono zero o vuoto. Si tratta di una proprietà della sessione che può essere impostata solo quando viene creata la sessione.  
  
|nome|Elemento|  
|----------|-------------|  
|DbpropMsmdCacheMode|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMsmdCachePolicy|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMsmdCacheRatio|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMsmdCacheRatio2|*Utilizzo*<br /> Proprietà `Double` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMsmdCompareCaseNotSensitiveStringFlags|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Determina le funzionalità di ordinamento e confronto di stringhe con distinzione tra maiuscole e minuscole. Questa proprietà controlla in che modo vengono eseguiti i confronti in set di caratteri che non supportano i caratteri maiuscoli e minuscoli, ad esempio Katakana per il giapponese e l'Hindi. Il valore di questa proprietà viene impostato alla prima connessione del thread di processo e influenza tutte le connessioni successive in tale thread.<br /><br /> Fare riferimento alla tabella seguente per determinare i flag da utilizzare.|  
  
|nome|valore|Description|  
|----------|-----------|-----------------|  
|NORM_IGNORECASE|*0x00000001*|Non viene fatta distinzione tra maiuscole e minuscole.|  
|Non applicabile|*0x00000002*|Confronto binario. I caratteri vengono confrontati in base al relativo valore sottostante nel set di caratteri, non al relativo ordine nell'alfabeto specifico.|  
|NORM_IGNORENONSPACE|*0x00000010*|I caratteri senza spaziatura vengono ignorati.|  
|NORM_IGNORESYMBOLS|*0x00000100*|I simboli vengono ignorati.|  
|NORM_IGNOREKANATYPE|*0x00001000*|Non viene fatta alcuna distinzione tra i caratteri Hiragana e Katakana. Quando vengono confrontati, i caratteri Hiragana e Katakana corrispondenti sono considerati uguali.|  
|NORM_IGNOREWIDTH|*0x00010000*|Non viene fatta alcuna distinzione tra le versioni a un byte e a due byte (DBCS) dello stesso carattere.|  
|SORT_STRINGSORT|*0x00100000*|La punteggiatura viene trattata nello stesso modo dei simboli.|  
  
 Per ulteriori informazioni sul confronto di stringhe in OLE DB, cercare "CompareString" nella sezione Platform SDK di MSDN Library.  
  
 Questa proprietà non ha alcun valore predefinito.  
  
 Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.  
  
|nome|Elemento|  
|----------|-------------|  
|DbpropMsmdCompareCaseSensitiveStringFlags|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Determina le funzionalità di ordinamento e confronto di stringhe senza distinzione tra maiuscole e minuscole. Questa proprietà controlla in che modo vengono eseguiti i confronti in set di caratteri che non supportano i caratteri maiuscoli e minuscoli, ad esempio Katakana per il giapponese e l'Hindi. Il valore di questa proprietà viene impostato alla prima connessione del thread di processo e influenza tutte le connessioni successive in tale thread.<br /><br /> Fare riferimento alla tabella seguente per determinare i flag da utilizzare.|  
  
|nome|valore|Description|  
|----------|-----------|-----------------|  
|NORM_IGNORECASE|*0x00000001*|Non viene fatta distinzione tra maiuscole e minuscole.|  
|Non applicabile|*0x00000002*|Confronto binario. I caratteri vengono confrontati in base al relativo valore sottostante nel set di caratteri, non al relativo ordine nell'alfabeto specifico.|  
|NORM_IGNORENONSPACE|*0x00000010*|I caratteri senza spaziatura vengono ignorati.|  
|NORM_IGNORESYMBOLS|*0x00000100*|I simboli vengono ignorati.|  
|NORM_IGNOREKANATYPE|*0x00001000*|Non viene fatta alcuna distinzione tra i caratteri Hiragana e Katakana. Quando vengono confrontati, i caratteri Hiragana e Katakana corrispondenti sono considerati uguali.|  
|NORM_IGNOREWIDTH|*0x00010000*|Non viene fatta alcuna distinzione tra le versioni a un byte e a due byte (DBCS) dello stesso carattere.|  
|SORT_STRINGSORT|*0x00100000*|La punteggiatura viene trattata nello stesso modo dei simboli.|  
  
 Per ulteriori informazioni sul confronto di stringhe in OLE DB, cercare "CompareString" nella sezione Platform SDK di MSDN Library.  
  
 Questa proprietà non ha alcun valore predefinito.  
  
 Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.  
  
|nome|Elemento|  
|----------|-------------|  
|DbpropMsmdDebugMode|*Utilizzo*<br /> Proprietà `String` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMsmdDynamicDebugLimit|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMsmdFlattened2|*Utilizzo*<br /> Proprietà `Boolean` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Restituisce tutti i membri di una gerarchia padre-figlio in un'unica colonna di tabella nel risultato bidimensionale, a meno che la gerarchia padre-figlio venga richiesta sull'asse 0. Il modello di livello per le colonne di output non viene utilizzato.<br /><br /> Il valore predefinito di questa proprietà è FALSE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMsmdMDXCompatibility|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Determina in che modo vengono trattati i membri segnaposto di una gerarchia incompleta o sbilanciata. Questa proprietà può assumere i valori elencati nella tabella seguente.|  
  
|valore|Description|  
|-----------|-----------------|  
|*0*|Per compatibilità con le versioni precedenti di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], questo valore è equivalente a 1.|  
|*1*|Le gerarchie nelle dimensioni con ruoli multipli ricevono una didascalia che include il nome della dimensione e il nome della gerarchia. Il formato della didascalia è il seguente:<br /><br /> [Dimensione].[Gerarchia]<br /><br /> I membri segnaposto sono esposti.|  
|*2*|Le gerarchie nelle dimensioni con ruoli multipli ricevono una didascalia che include il nome della dimensione e il nome della gerarchia. Il formato della didascalia è il seguente:<br /><br /> [Dimensione].[Gerarchia]<br /><br /> I membri segnaposto non sono esposti.|  
|*3*|(Impostazione predefinita) I membri segnaposto non sono esposti.|  
  
 Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.  
  
|nome|Elemento|  
|----------|-------------|  
|DbpropMsmdMDXUniqueNameStyle|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Determina l'algoritmo per la generazione di nomi univoci dei membri in una dimensione. Questa proprietà può assumere i valori elencati nella tabella seguente.<br /><br /> Il valore predefinito per questa proprietà è 6.|  
  
|valore|Description|  
|-----------|-----------------|  
|*0*|Per compatibilità con le versioni precedenti di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], questo valore è equivalente a 2.|  
|*1*|Utilizza un algoritmo del percorso della chiave:<br /><br /> [dim].&[chiave1].&[chiave2]|  
|*2*|Utilizza un algoritmo del percorso del nome:<br /><br /> [dim].[nome1].&[nome2]|  
|*3*|Utilizza nomi univoci garantiti stabili nel tempo.|  
  
 Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.  
  
|nome|Elemento|  
|----------|-------------|  
|DbpropMsmdSQLCompatibility|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMsmdSubQueries|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Maschera di bit che determina il comportamento delle sottoquery. Questa proprietà può assumere i valori elencati nella tabella seguente.|  
  
|valore|Description|  
|-----------|-----------------|  
|*0*|Valore predefinito, compatibile con le versioni precedenti di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> I membri calcolati o i set calcolati non sono consentiti nelle sub-SELECT o nei sottocubi.|  
|*1*|I membri o i set calcolati sono consentiti nelle sub-SELECT o nei sottocubi. I predecessori del membro calcolato non sono inclusi nello spazio della sub-SELECT o del sottocubo.|  
|*2*|I membri o i set calcolati sono consentiti nelle sub-SELECT o nei sottocubi. I predecessori del membro calcolato sono inclusi nello spazio della sub-SELECT o del sottocubo.|  
  
 I valori predefiniti di questa proprietà sono zero o vuoto.  
  
 Si tratta di una proprietà della sessione che può essere impostata solo quando viene creata la sessione.  
  
 Visualizzare [membri calcolati in sub-SELECT e sottocubi](../../multidimensional-models/mdx/calculated-members-in-subselects-and-subcubes.md) per una spiegazione dettagliata del comportamento dei membri calcolati o dei set calcolati nelle sub-SELECT e sottocubi.  
  
|nome|Elemento|  
|----------|-------------|  
|DbpropMsmdUseFormulaCache|*Utilizzo*<br /> Proprietà `String` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropMultiTableUpdate|*Utilizzo*<br /> Proprietà `Boolean` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_MULTITABLEUPDATE.<br /><br /> Il valore predefinito di questa proprietà è FALSE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropNullCollation|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_NULLCOLLATION.<br /><br /> Il valore predefinito di questa proprietà è 4, equivalente a DBPROPVAL_NC_LOW.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropOrderByColumnsInSelect|*Utilizzo*<br /> Proprietà `Boolean` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_ORDERBYCOLUMNSINSELECT.<br /><br /> Il valore predefinito di questa proprietà è FALSE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropOutputParameterAvailable|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_OUTPUTPARAMETERAVAILABILITY.<br /><br /> Il valore predefinito di questa proprietà è 1, equivalente a DBPROPVAL_OA_NOTSUPPORTED.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropPersistentIdType|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_PERSISTENTIDTYPE.<br /><br /> Il valore predefinito di questa proprietà è 4, equivalente a DBPROPVAL_PT_NAME.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropPrepareAbortBehavior|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_PREPAREABORTBEHAVIOR.<br /><br /> Il valore predefinito di questa proprietà è 1, equivalente a DBPROPVAL_CB_DELETE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropPrepareCommitBehavior|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_PREPARECOMMITBEHAVIOR.<br /><br /> Il valore predefinito di questa proprietà è 1, equivalente a DBPROPVAL_CB_DELETE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropProcedureTerm|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_PROCEDURETERM.<br /><br /> Il valore predefinito di questa proprietà è "Calculated member".<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropQuotedIdentifierCase|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_QUOTEDIDENTIFIERCASE.<br /><br /> Il valore predefinito di questa proprietà è 8, equivalente a DBPROPVAL_IC_MIXED.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropSchemaUsage|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_SCHEMAUSAGE.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropSqlSupport|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_SQLSUPPORT.<br /><br /> Il valore predefinito di questa proprietà è 512, equivalente a DBPROPVAL_SQL_SUBMINIMUM.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropSubqueries|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_SUBQUERIES.<br /><br /> **Nota.** Sebbene in DMX (Data Mining Extensions) siano supportate le sottoquery, questa proprietà fa riferimento al supporto delle sottoquery in SQL.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropSupportedTxnDdl|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_SUPPORTEDTXNDDL.<br /><br /> Il valore predefinito di questa proprietà è zero (0), equivalente a DBPROPVAL_TC_NONE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropSupportedTxnIsoLevels|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_SUPPORTEDTXNISOLEVELS.<br /><br /> Il valore predefinito di questa proprietà è 4096, equivalente a DBPROPVAL_TI_READCOMMITTED.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropSupportedTxnIsoRetain|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_SUPPORTEDTXNISORETAIN.<br /><br /> Il valore predefinito di questa proprietà è 292, equivalente a una combinazione di DBPROPVAL_TR_ABORT_NO, DBPROPVAL_TR_COMMIT_NO e DBPROPVAL_TR_NONE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|DbpropTableTerm|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_TABLETERM.<br /><br /> Il valore predefinito di questa proprietà è "Cube".<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|Dialect|*Utilizzo*<br /> Proprietà `String` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Stabilisce il sottolinguaggio utilizzato nelle situazioni seguenti:<br /><br /> -Il sottolinguaggio che il provider Usa la prima volta in cui il provider prova a eseguire una query.<br />-Il sottolinguaggio utilizzato per gli errori di esecuzione restituiti come risultato di errori di query.<br /><br /> È possibile utilizzare la proprietà `Dialect` quando si prevede che nella maggior parte delle query verrà utilizzato un sottolinguaggio specifico.<br /><br /> La sintassi delle query può essere simile per i sottolinguaggi dei linguaggi, ad esempio DMX e SQL. Poiché la sintassi può essere simile, tramite [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] potrebbe non essere possibile dedurre il sottolinguaggio dalla sintassi delle query. Se una query non viene eseguita in un sottolinguaggio, tramite l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] può venire effettuato un nuovo tentativo di eseguire la query in un sottolinguaggio diverso.<br /><br /> Se la proprietà `Dialect` è impostata, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] restituisce errori di esecuzione delle query nel sottolinguaggio che ha precedenza, anche se il provider tenta di eseguire di nuovo la query in un altro sottolinguaggio. La proprietà `Dialect` è ad esempio impostata su MDGUID_DM. Il provider tenta innanzitutto di eseguire la query come query di data mining, ma l'esecuzione ha esito negativo. Il provider tenta quindi di eseguire di nuovo la query come query SQL. Anche questa query SQL ha tuttavia esito negativo. Poiché il valore della proprietà `Dialect` è MDGUID_DM, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] restituisce un messaggio di errore di data mining, non un messaggio di errore SQL.<br /><br /> Se la proprietà `Dialect` non è impostata, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] restituisce errori di esecuzione delle query nel sottolinguaggio utilizzato per ultimo. La proprietà `Dialect` non è ad esempio impostata e si verifica un errore della query di data mining. Il provider tenta quindi di eseguire di nuovo la query come query SQL, ma anche in questo caso la query ha esito negativo. Poiché la proprietà `Dialect` non è impostata, il provider restituisce un messaggio di errore SQL anziché un messaggio di errore di data mining.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.<br /><br /> I sottolinguaggi disponibili per questa proprietà sono elencati nella tabella seguente.|  
  
|nome|valore|Description|  
|----------|-----------|-----------------|  
|DBGUID_SQL|*C8B522D7-5CF3-11CE-ADE5-00AA0044773D*|Il parser SQL ha la precedenza.|  
|MDGUID_DM|*62C58FED-CCA5-44F1-83B6-7B45682B3904*|Il parser DMX ha la precedenza.|  
|MDGUID_MDX|*A07CCCD0-8148-11D0-87BB-00C04FC33942*|Il parser MDX ha la precedenza.|  
  
|nome|Elemento|  
|----------|-------------|  
|Disable Prefetch Facts|*Utilizzo*<br /> Proprietà `Boolean` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Quando è impostata su True, il motore arresta il tentativo di recuperare i valori per la durata della sessione.<br /><br /> Il valore predefinito per questa proprietà è `False`.|  
|EffectiveRoles|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|EffectiveUserName|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Specifica il nome di un account da utilizzare per sostituire il nome utente durante la connessione a un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Il valore della proprietà non è normalizzato, in quanto MDX [UserName](/sql/mdx/username-mdx) funzione restituisce il valore letterale se questa proprietà viene utilizzata. Questa proprietà può essere utilizzata solo dagli amministratori del server.<br /><br /> Questa proprietà supporta i tipi SID seguenti: User, Group, Alias, WellKnownGroup, Computer.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|EndRange|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Specifica un valore intero in base zero che corrisponde a un valore dell'attributo `CellOrdinal`. L'attributo `CellOrdinal` fa parte dell'elemento `Cell` nella sezione `CellData` di `MDDataSet`.<br /><br /> Se utilizzata insieme alla proprietà `BeginRange`, questa proprietà può essere utilizzata dall'applicazione client per limitare un set di dati OLAP restituito da un comando a un intervallo specifico di celle. Se viene specificato il valore -1, vengono restituite tutte le celle a partire da quella specificata nella proprietà `BeginRange`.<br /><br /> Il valore predefinito per questa proprietà è -1.<br /><br /> Questa proprietà può essere utilizzata con il metodo `Execute`.|  
|ExecutionMode|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Il valore predefinito per questa proprietà è *Execute*.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|ForceCommitTimeout|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Determina il tempo di attesa, in secondi, da parte della fase di commit di un comando XMLA attualmente in esecuzione prima di forzare il rollback dei comandi eseguiti in precedenza. La fase di commit corrisponde a comandi XMLA come `Statement` o `Process`.<br /><br /> Un valore zero (0) indica che l'istanza attende indefinitamente.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|Formato|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Determina il tipo di set di risultati restituito dai metodi `Discover` e `Execute`. Questa proprietà può assumere i valori elencati nella tabella seguente.|  
  
 Il valore predefinito per questa proprietà è *nativa*.  
  
 Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.  
  
|valore|Description|  
|-----------|-----------------|  
|*Tabulare*|Restituisce un set di risultati utilizzando il [set di righe](../xml-data-types/rowset-data-type-xmla.md) tipo di dati.|  
|*Multidimensionale*|Restituisce un set di righe utilizzando la [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) tipo di dati.|  
|*Nativo*|Non è specificato in modo esplicito alcun formato. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] restituisce il formato adatto per il comando. Il tipo di risultato effettivo è identificato dallo spazio dei nomi del risultato.|  
  
|nome|Elemento|  
|----------|-------------|  
|ImpactAnalysis|*Utilizzo*<br /> Proprietà `Boolean` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|LocaleIdentifier|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Legge o imposta l'identificatore delle impostazioni locali (LCID) utilizzato dal metodo `Discover` o `Execute`. Per l'elenco esadecimale completo degli identificatori di lingua, cercare l'argomento relativo agli identificatori di lingua in MSDN Library.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MaximumRows|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropAggregateCellUpdate|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_AGGREGATECELL_UPDATE.<br /><br /> Il valore predefinito di questa proprietà è 4, equivalente a MDPROPVAL_AU_SUPPORTED.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropAxes|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_AXES.<br /><br /> Il valore predefinito per questa proprietà è 2147483647.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropDrillFunctions|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Determina il livello di supporto per le funzioni di drill sul server. Per compilare una maschera di bit valida, si utilizzano i valori seguenti:<br /><br /> MDPROPVAL_MDF_BASIC (0x01)<br /><br /> MDPROPVAL_MDF_ASYMMETRIC (0x02)<br /><br /> MDPROPVAL_MDF_CALC_MEMBERS (0x04)<br /><br /> I valori predefiniti sono:<br /><br /> 3 per SQL Server 2008<br /><br /> 7 per SQL Server 2008 R2 e [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropFlatteningSupport|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_FLATTENING_SUPPORT.<br /><br /> Il valore predefinito di questa proprietà è 1, equivalente a MDPROPVAL_FS_FULL_SUPPORT.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxCaseSupport|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_CASESUPPORT.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxDescFlags|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_DESCFLAGS.<br /><br /> Il valore predefinito di questa proprietà è 7, equivalente a MDPROPVAL_MD_BEFORE, MDPROPVAL_MD_AFTER e MDPROPVAL_MD_SELF.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxFormulas|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_FORMULAS.<br /><br /> Il valore predefinito di questa proprietà è 63, equivalente a una combinazione di MDPROPVAL_MF_WITH_CALCMEMBERS, MDPROPVAL_MF_WITH_NAMEDSETS, MDPROPVAL_MF_CREATE_CALCMEMBERS, MDPROPVAL_MF_CREATE_NAMEDSETS, MDPROPVAL_MF_SCOPE_SESSION e MDPROPVAL_MF_SCOPE_GLOBAL.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxJoinCubes|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_JOINCUBES.<br /><br /> Il valore predefinito di questa proprietà è 1, equivalente a MDPROPVAL_MJC_SINGLECUBE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxMemberFunctions|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_MEMBER_FUNCTIONS.<br /><br /> Il valore predefinito di questa proprietà è 15, equivalente a una combinazione di tutti i valori OLE DB disponibili.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxNamedSets|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Maschera di bit dei valori elencati nella tabella che segue.|  
  
|valore|Description|  
|-----------|-----------------|  
|*0x01*|MDPROPVAL_MNS_BASIC.|  
|*0x02*|MDPROPVAL_MNS_DYNAMIC.|  
|*0x04*|MDPROPVAL_MNS_DISPLAYFOLDER.|  
|*0x08*|MDPROPVAL_MNS_CAPTION.|  
  
 Il valore predefinito di questa proprietà è 15.  
  
|nome|Elemento|  
|----------|-------------|  
|MdpropMdxNonMeasureExpressions|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_NONMEASURE_EXPRESSIONS.<br /><br /> Il valore predefinito di questa proprietà è zero (0), equivalente a MDPROPVAL_NME_ALLDIMENSIONS.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxNumericFunctions|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_NUMERIC_FUNCTIONS.<br /><br /> Il valore predefinito di questa proprietà è 2047, equivalente a una combinazione di MDPROPVAL_MNF_MEDIAN, MDPROPVAL_MNF_VAR, MDPROPVAL_MNF_STDDEV, MDPROPVAL_MNF_RANK, MDPROPVAL_MNF_AGGREGATE, MDPROPVAL_MNF_COVARIANCE, MDPROPVAL_MNF_CORRELATION, MDPROPVAL_MNF_LINREGSLOPE, MDPROPVAL_MNF_LINREGVARIANCE, MDPROPVAL_MNF_LINREG2 e MDPROPVAL_MNF_LINREGPOINT.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxObjQualification|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_OBJQUALIFICATION.<br /><br /> Il valore predefinito di questa proprietà è 496, equivalente a una combinazione di MDPROPVAL_MOQ_DIM_HIER, MDPROPVAL_MOQ_DIMHIER_LEVEL, MDPROPVAL_MOQ_DIMHIER_MEMBER, MDPROPVAL_MOQ_LEVEL_MEMBER e MDPROPVAL_MOQ_MEMBER_MEMBER.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxOuterReference|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_OUTERREFERENCE.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxQueryByProperty|*Utilizzo*<br /> Proprietà `Boolean` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_QUERYBYPROPERTY.<br /><br /> Il valore predefinito di questa proprietà è TRUE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxRangeRowset|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_RANGEROWSET.<br /><br /> Il valore predefinito di questa proprietà è 4, equivalente a MDPROPVAL_RR_UPDATE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxSetFunctions|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_SET_FUNCTIONS.<br /><br /> Il valore predefinito di questa proprietà è 524287, equivalente a una combinazione di MDPROPVAL_MSF_TOPPERCENT, MDPROPVAL_MSF_BOTTOMPERCENT, MDPROPVAL_MSF_TOPSUM, MDPROPVAL_MSF_BOTTOMSUM, MDPROPVAL_MSF_PERIODSTODATE, MDPROPVAL_MSF_LASTPERIODS, MDPROPVAL_MSF_YTD, MDPROPVAL_MSF_QTD, MDPROPVAL_MSF_MTD, MDPROPVAL_MSF_WTD, MDPROPVAL_MSF_DRILLDOWNMEMBER, MDPROPVAL_MSF_DRILLDOWNLEVEL, MDPROPVAL_MSF_DRILLDOWNMEMBERTOP, MDPROPVAL_MSF_DRILLDOWNMEMBERBOTTOM, MDPROPVAL_MSF_DRILLDOWNLEVEL, MDPROPVAL_MSF_DRILLDOWNLEVELTOP, MDPROPVAL_MSF_DRILLDOWNLEVELBOTTOM, MDPROPVAL_MSF_DRILLUPMEMBER, MDPROPVAL_MSF_DRILLUPLEVEL e MDPROPVAL_MSF_TOGGLEDRILLSTATE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxSlicer|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_SLICER.<br /><br /> Il valore predefinito di questa proprietà è 2, equivalente a MDPROPVAL_MS_SINGLETUPLE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxStringCompop|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_MDX_STRING_COMPOP.<br /><br /> Il valore predefinito di questa proprietà è 15, equivalente a una combinazione di MDPROPVAL_MSC_LESSTHAN, MDPROPVAL_MSC_GREATERTHAN, MDPROPVAL_MSC_LESSTHANEQUAL e MDPROPVAL_MSC_GREATERTHANEQUAL.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdpropMdxSubQueries|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Il valore predefinito di questa proprietà è 63 in SQL Server 2014.<br /><br /> Il valore predefinito di questa proprietà è 31 in SQL Server 2008 R2 e [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]<br /><br /> Il valore predefinito di questa proprietà è 15 in SQL Server 2008<br /><br /> Indica il livello di supporto per le sottoquery in MDX. Maschera di bit dei valori elencati nella tabella che segue.|  
  
|valore|Description|  
|-----------|-----------------|  
|*0x01*|MDPROPVAL_MSQ_BASIC.|  
|*0x02*|MDPROPVAL_MSQ_ARBITRARYSHAPE.|  
|*0x04*|MDPROPVAL_MSQ_NONVISUAL.|  
|*0x08*|MDPROPVAL_MSQ_CALCMEMBERS.|  
  
|||  
|-|-|  
|*0x10*|MDPROPVAL_MSQ_CALCMEMBERS2|  
  
|nome|Elemento|  
|----------|-------------|  
|MdpropNamedLevels|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_NAMED_LEVELS.<br /><br /> Il valore predefinito di questa proprietà è 3, equivalente a una combinazione di MDPROPVAL_NL_NAMEDLEVELS e MDPROPVAL_NL_NUMBEREDLEVELS.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|MdxMissingMemberMode|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Indica se i membri mancanti vengono ignorati nelle istruzioni MDX.<br /><br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_MDX_MISSING_MEMBER_MODE.<br /><br /> Il valore predefinito per questa proprietà è *predefinito*.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.<br /><br /> Questa proprietà può assumere i valori elencati nella tabella seguente.|  
  
|valore|Description|  
|-----------|-----------------|  
|*Valore predefinito*|Viene utilizzato il valore generato dall'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|*Errore*|Viene generato un errore.|  
|*Ignora*|I membri mancanti vengono sempre ignorati.|  
  
|nome|Elemento|  
|----------|-------------|  
|MDXSupport|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Specifica un'enumerazione che descrive il livello di supporto MDX.<br /><br /> `Value` = *Core* MDX tutte le opzioni sono supportate.<br /><br /> Attualmente, è l'unico valore contenuto nell'enumerazione *Core*. Nelle versioni future verranno definiti altri valori per questa enumerazione.<br /><br /> Il valore predefinito per questa proprietà è *Core*.<br /><br /> Questa proprietà può essere utilizzata con il metodo `Discover`.|  
|NonEmptyThreshold|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|Password|**Questa proprietà non è più supportata.**<br /><br /> *Utilizzo*<br /> Proprietà `String` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Per garantire la compatibilità con le versioni precedenti, questa proprietà viene ignorata senza generare un errore quando viene utilizzata con il metodo `Execute` o `Discover`.|  
|ProviderName|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_DBMSNAME.<br /><br /> Il valore predefinito di questa proprietà è "OLAP Server".<br /><br /> Questa proprietà può essere utilizzata con il metodo `Discover`.|  
|ProviderType|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_DATASOURCE_TYPE.<br /><br /> Il valore predefinito per questa proprietà è 6.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|ProviderVersion|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_DBMSVER.<br /><br /> Il valore predefinito di questa proprietà corrisponde alla versione dell'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Questa proprietà può essere utilizzata con il metodo `Discover`.|  
|ReadOnlySession|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|RealTimeOlap|*Utilizzo*<br /> Proprietà `Boolean` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Quando è impostata su TRUE, indica che su tutte le partizioni che sono in ascolto delle notifiche per le tabelle devono essere eseguite query in tempo reale, ignorando la memorizzazione nella cache. Questa proprietà è equivalente alla proprietà OLE DB DBPROP_MSMD_REAL_TIME_OLAP.<br /><br /> Il valore predefinito di questa proprietà è FALSE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|ReturnCellProperties|*Utilizzo*<br /> Proprietà `Boolean` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Il valore predefinito di questa proprietà è FALSE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|Ruoli|*Utilizzo*<br /> Proprietà `String` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Specifica una stringa con valori delimitati da virgole dei nomi di ruolo con cui un'applicazione client si connette a un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Questa proprietà consente all'utente di connettersi utilizzando un ruolo diverso da quello correntemente utilizzato. Un amministratore del server può, ad esempio, connettersi a un cubo come membro di un ruolo per testare le autorizzazioni concesse a tale ruolo. Per connettersi utilizzando questa proprietà, l'utente deve essere un membro del ruolo specificato.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.<br /><br /> **Nota.** Per i nomi dei ruoli è rilevante la distinzione tra maiuscole e minuscole. **Non usare** spazi tra i nomi dei ruoli delimitato da virgole. In caso contrario, potrebbero venire restituiti errori e risultati imprevisti dalle query nei set di celle protetti.|  
|SafetyOptions|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Determina se le librerie non sicure possono essere registrate e caricate dalle applicazioni client.<br /><br /> Il valore di questa proprietà determina inoltre se la parola chiave PASSTHROUGH è consentita nei cubi locali. Si verifica un errore nelle situazioni seguenti:<br /><br /> -Se un'applicazione client tenta di creare un cubo locale con un'istruzione INSERT INTO che contiene la parola chiave PASSTHROUGH.<br />-Se un'applicazione client tenta di aggiornare un cubo locale contenente un'istruzione INSERT INTO che utilizza la parola chiave PASSTHROUGH.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.<br /><br /> Questa proprietà può assumere i valori elencati nella tabella seguente.|  
  
|nome|valore|Description|  
|----------|-----------|-----------------|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_DEFAULT|*0*|Questo valore viene trattato come DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_SAFE.<br /><br /> Per le connessioni a un cubo locale, questo valore dipende dal fatto che la proprietà della stringa di connessione CREATECUBE sia o meno utilizzata. Se viene utilizzata la proprietà della stringa di connessione CREATECUBE, questo valore corrisponde a DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL. In caso contrario, il valore corrisponde a DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_SAFE.|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL|*1*|Questo valore consente di attivare tutte le librerie di funzioni definite dall'utente senza verificare che siano sicure per l'inizializzazione e lo scripting. Per le connessioni ai cubi locali, questo valore consente l'utilizzo di stored procedure e della parola chiave PASSTHROUGH nelle istruzioni INSERT INTO.<br /><br /> **Si sconsiglia questa opzione**.|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_SAFE|*2*|Questo valore consente di assicurarsi che tutte le classi per una particolare libreria di funzioni definita dall'utente vengano controllate per verificare che siano sicure per l'inizializzazione e lo scripting. Per le connessioni ai cubi locali, questo valore impedisce l'utilizzo della parola chiave PASSTHROUGH nelle istruzioni INSERT INTO e delle stored procedure se la proprietà PermissionSet non è impostata su Safe.<br /><br /> Questo valore rimuove anche le azioni nel [MDSCHEMA_ACTIONS](../../schema-rowsets/ole-db-olap/mdschema-actions-rowset.md) che include un valore del codice HTML o comando nella colonna ACTION_TYPE oppure hanno un valore dell'URL nella colonna ACTION_TYPE e un valore nella colonna CONTENT che non sono presenti set di righe dello schema iniziare con "http://" o "https://".|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_NONE|*3*|Questo valore impedisce l'utilizzo delle funzioni definite dall'utente durante la sessione. Per le connessioni ai cubi locali, questo valore impedisce l'utilizzo di tutte le stored procedure e della parola chiave PASSTHROUGH nelle istruzioni INSERT INTO.<br /><br /> Questo valore consente inoltre di rimuovere tutte le azioni nel set di righe dello schema MDSCHEMA_ACTIONS.|  
  
|nome|Elemento|  
|----------|-------------|  
|SecuredCellValue|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Specifica il codice di errore e i valori per le proprietà delle celle `Value` e `Formatted Value` da restituire quando viene eseguito un tentativo di accesso a una cella protetta.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.<br /><br /> Questa proprietà può assumere i valori elencati nella tabella seguente.|  
  
|valore|Description|  
|-----------|-----------------|  
|*0*|(Impostazione predefinita) Per garantire la compatibilità con le versioni precedenti, questo valore è identico *1*. Il significato di questo valore predefinito è soggetto a modifiche nelle versioni future.|  
|*1*|Restituisce HRESULT = NO_ERROR<br /><br /> La proprietà `Value` della cella contiene il risultato come tipo di dati Variant. Nella proprietà `Formatted Value` viene restituita la stringa "#N/A".|  
|*2*|Restituisce un errore come valore di HRESULT.|  
|*3*|Restituisce NULL in entrambe le proprietà `Value` e `Formatted Value`|  
|*4*|Restituisce uno zero numerico (0) nella proprietà `Value` e uno zero formattato nella proprietà `Formatted Value`. Nella proprietà `Formatted Value` per una cella la cui proprietà `Format` è "#. ##" viene ad esempio restituito 0.00.|  
|*5*|Restituisce la stringa "#SEC" in entrambe le proprietà `Value` e `Formatted Value`.|  
  
|nome|Elemento|  
|----------|-------------|  
|ServerName|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB DBPROP_SERVERNAME.<br /><br /> Il valore predefinito di questa proprietà corrisponde al nome dell'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|ShowHiddenCubes|*Utilizzo*<br /> Proprietà `Boolean` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Il valore predefinito di questa proprietà è FALSE.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|SQLQueryMode|*Utilizzo*<br /> Proprietà `String` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Determina se i calcoli sono inclusi nelle query SQL.<br /><br /> Il valore predefinito per questa proprietà è *Calculated*.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.<br /><br /> Questa proprietà può assumere i valori elencati nella tabella seguente.|  
  
|valore|Description|  
|-----------|-----------------|  
|*Dati*|Non è incluso alcun calcolo.|  
|*Calcolata*|Vengono restituiti i calcoli.|  
|*IncludeEmpty*|Vengono restituiti i calcoli e le righe vuote.|  
  
|nome|Elemento|  
|----------|-------------|  
|SQLSupport|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Il valore predefinito per questa proprietà è 512.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|SspropInitAppName|*Utilizzo*<br /> Proprietà `String` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Contiene il nome dell'applicazione client.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|SspropInitPacketsize|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Contiene l'ID dell'applicazione client.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|SspropInitWsid|*Utilizzo*<br /> Proprietà `String` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Contiene l'ID della workstation client.<br /><br /> Questa proprietà non ha alcun valore predefinito.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|SupportoStato|*Utilizzo*<br /> Proprietà `String` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Specifica il livello di supporto delle informazioni sullo stato.<br /><br /> *Nessuno* = <br />                        Le informazioni sullo stato non sono supportate.<br /><br /> *Le sessioni* = le informazioni sullo stato viene fornito tramite il supporto della sessione.<br /><br /> Per altre informazioni sul supporto di sessione e le informazioni sullo stato, vedere [alla gestione delle connessioni e sessioni &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).<br /><br /> Il valore predefinito per questa proprietà è *sessioni*.<br /><br /> Questa proprietà può essere utilizzata con il metodo `Discover`.|  
|Timeout|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di lettura/scrittura.<br /><br /> *Descrizione*<br /> Specifica il tempo massimo di attesa, in secondi, da parte dell'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per l'esecuzione di una richiesta prima di restituire un errore. Questa proprietà determina inoltre il tempo massimo di attesa da parte dell'istanza per l'esecuzione di un aggiornamento a una tabella writeback prima di restituire un errore, equivalente alla proprietà della stringa di connessione Writeback Timeout.<br /><br /> Il valore predefinito di questa proprietà è zero (0).<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|TransactionDDL|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Riservato per utilizzi futuri.<br /><br /> Il valore predefinito per questa proprietà è 0.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
|UserName|Questa proprietà non è più supportata.<br /><br /> *Utilizzo*<br /> Proprietà `String` facoltativa, di sola lettura.<br /><br /> *Descrizione*<br /> Specifica una stringa che restituisce il nome utente associato dall'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] al comando. Per garantire la compatibilità con le versioni precedenti, questa proprietà viene ignorata senza generare un errore quando viene utilizzata con il metodo `Execute` o `Discover`. Questa proprietà è equivalente alla proprietà OLE DB DBPROP_USERNAME.<br /><br /> Il valore predefinito di questa proprietà corrisponde al nome utente da cui è stata aperta la sessione o la connessione corrente.<br /><br /> Questa proprietà può essere utilizzata con il metodo `Execute`.|  
|VisualMode|*Utilizzo*<br /> Proprietà `Integer` facoltativa, di sola scrittura.<br /><br /> *Descrizione*<br /> Questa proprietà è equivalente alla proprietà OLE DB MDPROP_VISUALMODE.<br /><br /> Il valore predefinito di questa proprietà è zero (0), equivalente a DBPROPVAL_VISUAL_MODE_DEFAULT.<br /><br /> Questa proprietà può essere utilizzata con i metodi `Discover` e `Execute`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento PropertyList &#40;XMLA&#41;](propertylist-element-xmla.md)  
  
  
