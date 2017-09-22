---
title: "Novità &#39; s novità di Analysis Services di SQL Server 2017 | Documenti Microsoft"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1eb6afc9-76ed-45a2-a188-374a4fc23224
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: eb98483d6237f2db2fdb0cb9aa444dd938a431f0
ms.contentlocale: it-it
ms.lasthandoff: 09/21/2017

---
# <a name="what39s-new-in-sql-server-2017-analysis-services"></a>Novità &#39; s novità di SQL Server 2017 Analysis Services
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]


## <a name="sql-server-2017-analysis-services-rc2"></a>SQL Server 2017 Analysis Services RC2
In questa versione non sono presenti nuove funzionalità. In questa versione includono correzioni di bug e le prestazioni.

## <a name="sql-server-2017-analysis-services-rc1"></a>SQL Server 2017 Analysis Services RC1
Non sono presenti nuove funzionalità in questa versione, tuttavia, questa versione include miglioramenti aggiuntivi a [viste a gestione dinamica](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) (DMV) per i modelli tabulari a livello di compatibilità 1200 e 1400 di.

DISCOVER_CALC_DEPENDENCY ora funziona con i modelli tabulari 1200 e 1400. I modelli tabulari 1400 mostrano le dipendenze tra le partizioni di M, M espressioni e origini dati strutturati. Per ulteriori informazioni, vedere il [blog di Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/).

Sono inclusi per questa DMV, che viene utilizzata dai vari strumenti client per visualizzare misure dimensionalità MDSCHEMA_MEASUREGROUP_DIMENSIONS miglioramenti. Ad esempio, la funzionalità di esplorazione in tabelle Pivot di Excel consente all'utente di cross-drill alle dimensioni correlate per le misure selezionate. Questa versione consente di correggere le colonne della cardinalità, che sono state in precedenza con valori non corretti.

## <a name="sql-server-analysis-services-ctp-21"></a>SQL Server Analysis Services versione CTP 2.1
In questa versione non sono presenti nuove funzionalità. Miglioramenti apportati in questa versione includono correzioni di bug e le prestazioni e miglioramenti alle [viste a gestione dinamica](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) (DMV). Viste a gestione dinamica sono query che restituiscono informazioni sulle operazioni del server locale e l'integrità del server in SQL Server Profiler. Per ulteriori informazioni, vedere il [blog di Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/).

## <a name="sql-server-analysis-services-ctp-20"></a>SQL Server Analysis Services versione CTP 2.0
Questa versione include diverse nuove funzionalità migliorate per il modello tabulare, tra cui:

* Sicurezza a livello di oggetto per la protezione dei metadati dei modelli tabulari.
* Miglioramenti delle prestazioni di transazione per un'esperienza di sviluppatore più reattiva.
* Miglioramenti della vista a gestione dinamica per i modelli 1200 e 1400 l'abilitazione di analisi delle dipendenze e creazione di report.
* Miglioramenti all'esperienza di creazione e modifica per le espressioni di righe di dettaglio.
* Gerarchia e colonna riutilizzare per rendere visibili nelle posizioni più utili nell'elenco dei campi di Power BI.
* Relazioni di data per creare relazioni con dimensioni di data in base ai campi di Data.
* Opzione di installazione predefinita di Analysis Services è ora per la modalità tabulare.
* Nuove origini dati recupera dati (Power Qery).
* Editor DAX per SSDT.
* Origini di dati DirectQuery esistente supportano per milione di query.
* Miglioramenti di SQL Server Management Studio, ad esempio la visualizzazione, modifica e il supporto per le origini dati strutturate di script.

Per ottenere ulteriori dettagli su questa versione CTP 2.0, vedere il [blog di Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/).

## <a name="sql-server-analysis-services-on-windows-ctp-14"></a>SQL Server Analysis Services in Windows CTP 1.4
[SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/sql-server-data-tools-ssdt-release-candidate) e [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms-release-candidate) versioni di anteprima coincidono con le versioni di anteprima di SQL Server 2017. Assicurarsi di utilizzare la versione più recente per ottenere le nuove funzionalità. Per ulteriori informazioni, vedere il [blog di Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/).



## <a name="sql-server-analysis-services-on-windows-ctp-13"></a>SQL Server Analysis Services in Windows CTP 1.3

### <a name="encoding-hints"></a>Hint di codifica

Questa versione introduce gli hint di codifica, una funzionalità avanzata, usata per ottimizzare l'elaborazione (aggiornamento di dati) dei modelli tabulari di grandi dimensioni in memoria. Per comprendere meglio la codifica, vedere [prestazioni ottimizzazione di modelli tabulari in SQL Server 2012 Analysis Services](https://msdn.microsoft.com/library/dn393915.aspx) white paper per comprendere meglio la codifica. Il processo di codifica descritto di seguito si applica in CTP 1.3.

* Codifica del valore fornisce migliori prestazioni di query per le colonne che sono in genere utilizzata solo per le aggregazioni.

* La codifica hash è preferibile per colonne di raggruppamento (spesso valori di tabella della dimensione) e le chiavi esterne. Colonne di tipo stringa sono sempre con codificata hash.

Le colonne numeriche è possono utilizzare uno di questi metodi di codifica. Quando Analysis Services viene avviato l'elaborazione di una tabella, se la tabella è vuota (con o senza partizioni) o è in corso un'operazione di elaborazione di tabella completa, per ogni colonna numerica determinare se applicare valore o la codifica hash vengono estratti i valori di esempi . Per impostazione predefinita, viene scelto di codifica del valore quando l'esempio di valori distinct nella colonna è sufficiente – in caso contrario la codifica hash in genere fornirà una migliore compressione. È possibile per Analysis Services modificare il metodo di codifica dopo la colonna è parzialmente elaborata in base alle informazioni sulla distribuzione dei dati e riavviare il processo di codifica. Questo ovviamente aumenta il tempo di elaborazione ed è inefficiente. Il white paper ottimizzazione delle prestazioni viene illustrata la codifica nuovamente in modo più dettagliato e viene descritto come rilevare utilizzando SQL Server Profiler.

Hint per la codifica nella versione CTP 1.3 consente i creatori di modelli specificare una preferenza per il metodo di codifica specificato la conoscenza di dati di profilatura e/o in risposta a ricodifica gli eventi di traccia. Poiché l'aggregazione su colonne con codifica hash è più lento su colonne con valore codificato, codifica del valore può essere specificata come hint per tali colonne. Non è garantito che verrà applicata la preferenza; pertanto si tratta di un hint anziché un'impostazione. Per specificare un hint di codifica, impostare la proprietà EncodingHint nella colonna. I valori possibili sono "Default", "Value" e "Hash". In fase di scrittura, la proprietà non è ancora disponibile in SSDT, pertanto deve essere impostata tramite dei metadati basata su JSON, Tabular Model Scripting Language (TMSL) o del modello a oggetti tabulare (TOM). Il seguente frammento di JSON in base a metadati dai file Model.bim Specifica valore di codifica per la colonna Sales Amount.

```
{
    "name": "Sales Amount",
    "dataType": "decimal",
    "sourceColumn": "SalesAmount",
    "formatString": "\\$#,0.00;(\\$#,0.00);\\$#,0.00",
    "sourceProviderType": "Currency",
    "encodingHint": "Value"
}
```

### <a name="extended-events-not-working-in-ctp-13"></a>Non funziona in CTP 1.3 eventi estesi
Eventi estesi di SSAS non funzionano in CTP 1.3. È stata pianificata una correzione nella versione CTP successiva.

## <a name="sql-server-analysis-services-on-windows-ctp-12"></a>SQL Server Analysis Services in Windows CTP 1.2

In questa versione non sono presenti nuove funzionalità. I miglioramenti includono correzioni di bug e o potenziamento delle prestazioni.

La versione di anteprima più recente di SQL Server Data Tools (SSDT), che coincide con la versione CTP 1.2 di SQL Server 2017, rappresenta un miglioramento la nuova esperienza moderna recupera dati introdotta in CTP 1.1 con menu nuovo editor di query e le funzionalità di accesso rapido. 

## <a name="sql-server-analysis-services-on-windows-ctp-11"></a>SQL Server Analysis Services in Windows CTP 1.1 

In questa versione sono stati introdotti miglioramenti per i modelli tabulari. 

### <a name="1400-compatibility-level-for-tabular-models"></a>Livello di compatibilità&1400; per i modelli tabulari
  Per poter sfruttare le funzionalità descritte in questo articolo, è necessario impostare il livello di compatibilità 1400 per i modelli tabulari nuovi o esistenti. Non è possibile distribuire i modelli con livello di compatibilità 1400 in SQL Server 2016 SP1 o versioni precedenti né effettuare il downgrade a livelli di compatibilità inferiori.
  
  Per creare nuovi progetti di modelli tabulari o aggiornare quelli esistenti con il livello di compatibilità 1400, scaricare e installare una **versione di anteprima** di [SQL Server Data Tools (SSDT) 17.0 RC2](https://go.microsoft.com/fwlink?LinkId=837939). 
  
In SSDT è possibile selezionare il nuovo livello di compatibilità 1400 durante la creazione di nuovi progetti di modelli tabulari. 

![AS_NewTabular1400Project](../analysis-services/media/as-newtabular1400project.png)

>[!NOTE]
> L'area di lavoro integrata nella versione di dicembre di SQL Server Data Tools (SSDT) supporta il livello di compatibilità 1400. Se si creano nuovi progetti di modelli tabulari in un'istanza del server dell'area di lavoro, tale istanza (o qualsiasi istanza in cui si esegue la distribuzione) deve essere [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 1.1. 

Per aggiornare un modello tabulare esistente in SSDT, in Esplora soluzioni fare doppio clic su **Model.bim**, quindi nel **proprietà**, impostare il **livello di compatibilità** proprietà ** SQL Server 2017 (1400)**. 

![AS_Model_Properties](../analysis-services/media/as-model-properties.png)

### <a name="modern-get-data-experience"></a>Funzionalità moderna per il recupero di dati
Nella versione di anteprima più recente di SQL Server Data Tools (SSDT), che coincide con la versione [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 1.1, è stata introdotta una funzionalità moderna per il **recupero di dati** per i modelli tabulari con livello di compatibilità 1400. Questa nuova funzionalità si basa su una funzionalità simile in Power BI Desktop e Microsoft Excel 2016.

![AS_Get_Data_in_SSDT](../analysis-services/media/as-get-data-in-ssdt.png)

>[!NOTE]
> Per questa versione è supportato un numero limitato di origini dati. Negli aggiornamenti futuri sarà incluso il supporto per altre funzionalità e origini dati.

Per altre informazioni sulla funzionalità moderna per il recupero di dati, vedere il [blog del team di Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2016/12/16/introducing-a-modern-get-data-experience-for-sql-server-2017-on-windows-ctp-1-1-for-analysis-services/).

## <a name="ragged-hierarchies"></a>Gerarchie incomplete
Nei modelli tabulari è possibile modellare le gerarchie padre-figlio. Le gerarchie con un numero di livelli diverso sono spesso definite gerarchie incomplete. Per impostazione predefinita, le gerarchie di questo tipo presentano spazi vuoti nei livelli al di sotto del figlio minore. Di seguito è riportato un esempio di una gerarchia incompleta in un organigramma:

![AS_Ragged_Hierarchy](../analysis-services/media/as-ragged-hierarchy.png)

In questa versione è stata introdotta la proprietà **Hide Members** (Nascondi membri). È possibile impostare la proprietà **Hide Members** (Nascondi membri) relativa a una gerarchia su **Hide blank members**(Nascondi membri vuoti).

![AS_Hide_Blank_Members](../analysis-services/media/as-hide-blank-members.png)

 >[!NOTE]
 > I membri vuoti nel modello sono rappresentati da un valore vuoto di DAX, non da una stringa vuota.

Quando la proprietà è impostata su **Hide blank members**(Nascondi membri vuoti) e il modello è distribuito, nei client di creazione report come Excel viene visualizzata una versione più leggibile della gerarchia.

![AS_Non_Ragged_Hierarchy](../analysis-services/media/as-non-ragged-hierarchy.png)

### <a name="detail-rows"></a>Righe di dettaglio
È ora possibile definire un set di righe personalizzato che contribuisce a un valore di misura. La funzionalità Righe di dettaglio è paragonabile all'azione di drill-through predefinita nei modelli multidimensionali. Ciò consente agli utenti finali di visualizzare le informazioni in modo più dettagliato rispetto al livello aggregato. 

La tabella pivot seguente mostra i valori annuali di Internet Total Sales del modello tabulare di esempio di AdventureWorks. Per visualizzare le righe di dettaglio è possibile fare clic con il pulsante destro del mouse su una cella con un valore aggregato della misura e quindi scegliere **Mostra dettagli** .

![AS_Show_Details](../analysis-services/media/as-show-details.png)

Per impostazione predefinita, vengono visualizzati i dati associati nella tabella Internet Sales. Questo comportamento limitato spesso non è significativo per l'utente perché la tabella può non includere le colonne necessarie per visualizzare informazioni utili, ad esempio il nome del cliente e i dati relativi agli ordini. Con Righe di dettaglio, è possibile specificare una proprietà **Detail Rows Expression** (Espressione righe di dettaglio) per le misure.

#### <a name="detail-rows-expression-property-for-measures"></a>Proprietà Detail Rows Expression (Espressione righe di dettaglio) per le misure
La proprietà **Detail Rows Expression** (Espressione righe di dettaglio) per le misure consente agli autori di modelli di personalizzare le colonne e le righe restituite all'utente finale.

![AS_Detail_Rows_Expression_Property](../analysis-services/media/as-detail-rows-expression-property.png)

In un'espressione di righe di dettaglio viene in genere usata la funzione DAX [SELECTCOLUMNS](https://msdn.microsoft.com/library/mt761759.aspx) . L'esempio seguente definisce le colonne da restituire per le righe della tabella Internet Sales nel modello tabulare di esempio di AdventureWorks:

```
SELECTCOLUMNS(
    'Internet Sales',
    "Customer First Name", RELATED( Customer[Last Name]),
    "Customer Last Name", RELATED( Customer[First Name]),
    "Order Date", 'Internet Sales'[Order Date],
    "Internet Total Sales", [Internet Total Sales]
)
```

Con la proprietà definita e il modello distribuito, quando l'utente seleziona **Mostra dettagli**viene restituito un set di righe personalizzato che rispetta automaticamente il contesto del filtro della cella selezionata. In questo esempio vengono visualizzate solo le righe per il valore 2010:

![AS_Detail_Rows](../analysis-services/media/as-detail-rows.png)

#### <a name="default-detail-rows-expression-property-for-tables"></a>Proprietà Default Detail Rows Expression (Espressione predefinita righe di dettaglio) per le tabelle
Oltre alle misure, anche le tabelle hanno una proprietà per definire un'espressione di righe di dettaglio. La proprietà **Default Detail Rows Expression** (Espressione predefinita righe di dettaglio) viene usata come impostazione predefinita per tutte le misure all'interno della tabella. Le misure per cui non è definita un'espressione specifica ereditano automaticamente l'espressione dalla tabella e visualizzano il set di righe definito per la tabella. Questa impostazione consente di riutilizzare le espressioni. In questo modo, infatti, le nuove misure aggiunte successivamente alla tabella erediteranno automaticamente l'espressione.

![AS_Default_Detail_Rows_Expression](../analysis-services/media/as-default-detail-rows-expression.png)
 
#### <a name="detailrows-dax-function"></a>Funzione DAX DETAILROWS
In questa versione è inclusa una nuova funzione DAX `DETAILROWS` che restituisce il set di righe definito dall'espressione delle righe di dettaglio. Funziona in modo simile all'istruzione `DRILLTHROUGH` in MDX, che è anche compatibile con le espressioni delle righe di dettaglio definite nei modelli tabulari.

La query DAX seguente restituisce il set di righe definito dall'espressione delle righe di dettaglio per la misura o la relativa tabella. Se non è definita alcuna espressione, vengono restituiti i dati per la tabella Internet Sales perché è quella che contiene la misura.

```
EVALUATE DETAILROWS([Internet Total Sales])
```

## <a name="dax-enhancements"></a>Miglioramenti apportati a DAX
Questa versione include un operatore `IN` per le espressioni DAX. È simile all'operatore [`TSQL IN`](/sql-docs/docs/t-sql/language-elements/in-transact-sql) comunemente usato per specificare più valori in una clausola `WHERE`.

In precedenza, era pratica comune specificare filtri con più valori usando l'operatore logico `OR` , come illustrato nell'espressione di misura seguente:

```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
                 'Product'[Color] = "Red"
            || 'Product'[Color] = "Blue"
            || 'Product'[Color] = "Black"
    )
```

Questo processo viene semplificato dall'operatore `IN` :
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], 'Product'[Color] IN { "Red", "Blue", "Black" }
    )
```

In questo caso, l'operatore `IN` fa riferimento a una tabella a colonna singola con 3 righe, una per ogni colore specificato. Si noti che nella sintassi del costruttore della tabella vengono usate le parentesi graffe.

Dal punto di vista funzionale, l'operatore `IN` equivale alla funzione `CONTAINSROW` :
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], CONTAINSROW({ "Red", "Blue", "Black" }, 'Product'[Color])
    )
```

L'operatore `IN` può essere usato in modo efficace anche con i costruttori di tabella. Ad esempio, per la misura seguente è specificato un filtro in base alle combinazioni di colore e categoria del prodotto:
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
        FILTER( ALL('Product'),
              ( 'Product'[Color] = "Red"   && Product[Product Category Name] = "Accessories" )
         || ( 'Product'[Color] = "Blue"  && Product[Product Category Name] = "Bikes" )
         || ( 'Product'[Color] = "Black" && Product[Product Category Name] = "Clothing" )
        )
    )
```

Se si usa il nuovo operatore `IN` , l'espressione di misura precedente è formulata nel modo seguente:
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
        FILTER( ALL('Product'),
            ('Product'[Color], Product[Product Category Name]) IN
            { ( "Red", "Accessories" ), ( "Blue", "Bikes" ), ( "Black", "Clothing" ) }
        )
    )
```


## <a name="table-level-security"></a>Sicurezza a livello di tabella
In questa versione è stata introdotta la sicurezza a livello di tabella. Oltre a limitare l'accesso ai dati della tabella, è possibile proteggere i nomi di tabella sensibili. Ciò consente di impedire a un utente malintenzionato di individuare una tabella esistente.

Per impostare la sicurezza a livello di tabella è necessario usare i metadati basati su JSON, il linguaggio TMSL (Tabular Model Scripting Language) o il modello a oggetti tabulare (TOM, Tabular Object Model). 

Ad esempio, il codice seguente consente di proteggere la tabella Product del modello tabulare di esempio di AdventureWorks impostando la proprietà **MetadataPermission** della classe **TablePermission** su **None**.

```
//Find the Users role in Adventure Works and secure the Product table
ModelRole role = db.Model.Roles.Find("Users");
Table productTable = db.Model.Tables.Find("Product");
if (role != null && productTable != null)
{
    TablePermission tablePermission;
    if (role.TablePermissions.Contains(productTable.Name))
    {
        tablePermission = role.TablePermissions[productTable.Name];
    }
    else
    {
        tablePermission = new TablePermission();
        role.TablePermissions.Add(tablePermission);
        tablePermission.Table = productTable;
    }
    tablePermission.MetadataPermission = MetadataPermission.None;
}
db.Update(UpdateOptions.ExpandFull);
```


