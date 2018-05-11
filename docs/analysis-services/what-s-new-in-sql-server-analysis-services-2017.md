---
title: Novità di Analysis Services di SQL Server 2017 | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e43a64ace89df488b66a9e40591182ae34e6b66e
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="whats-new-in-sql-server-2017-analysis-services"></a>Novità di SQL Server 2017 Analysis Services
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

Analysis Services di SQL Server 2017 vedere alcuni dei più importanti miglioramenti dopo SQL Server 2012. Dopo il successo della modalità tabulare (introdotta in SQL Server 2012 Analysis Services), questa versione, i modelli tabulari rende più potenti che mai.

Modalità multidimensionale e PowerPivot per la modalità SharePoint sono un graffatura per molte distribuzioni di Analysis Services. Nel ciclo di vita del prodotto di Analysis Services, queste modalità sono avanzate. Non sono presenti funzionalità nuove per una delle modalità seguenti in questa versione. Tuttavia, vengono inclusi correzioni di bug e miglioramenti delle prestazioni.

Le funzionalità descritte di seguito sono inclusi in SQL Server 2017 Analysis Services. Ma per sfruttare al meglio, è necessario utilizzare anche le versioni più recenti di [SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md) (SSDT) e [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md) (SSMS). SSDT e SSMS vengono aggiornati ogni mese con le funzionalità nuove e migliorate in genere coincidano con nuove funzionalità di SQL Server.  

Sebbene sia importante imparare a tutte le nuove funzionalità, è anche importante sapere che cos'è deprecato e non più disponibili in questa versione e versioni successive. Assicurarsi di consultare [compatibilità con le versioni precedenti (SQL Server 2017 Analysis Services)](analysis-services-backward-compatibility-sql2017.md).

Diamo un'occhiata ad alcune delle principali nuove funzionalità in questa versione.

## <a name="1400-compatibility-level-for-tabular-models"></a>Livello di compatibilità 1400 per i modelli tabulari
  Per usufruire di molte delle nuove funzionalità e le funzionalità descritte di seguito, i modelli tabulari nuovi o esistenti devono essere impostati o aggiornati al livello di compatibilità 1400. Non è possibile distribuire i modelli con livello di compatibilità 1400 in SQL Server 2016 SP1 o versioni precedenti né effettuare il downgrade a livelli di compatibilità inferiori. Per ulteriori informazioni, vedere [il livello di compatibilità per i modelli tabulari di Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).
  
In SSDT è possibile selezionare il nuovo livello di compatibilità 1400 durante la creazione di nuovi progetti di modelli tabulari. 

![AS_NewTabular1400Project](../analysis-services/media/as-newtabular1400project.png)


Per aggiornare un modello tabulare esistente in SSDT, in Esplora soluzioni fare doppio clic su **Model.bim**, quindi nel **proprietà**, impostare il **livello di compatibilità** proprietà  **SQL Server 2017 (1400)**. 

![AS_Model_Properties](../analysis-services/media/as-model-properties.png)

È importante tenere presente, quando si aggiorna un modello esistente a 1400, è possibile effettuare il downgrade. Assicurarsi di mantenere un backup del database modello 1200.

## <a name="modern-get-data-experience"></a>Funzionalità moderna per il recupero di dati
Se si desidera importare dati da origini di dati nei modelli tabulari, SQL Server Data Tools (SSDT) introduce il moderno **recupera dati** esperienza per i modelli a livello di compatibilità 1400. Questa nuova funzionalità si basa su una funzionalità simile in Power BI Desktop e Microsoft Excel 2016. L'esperienza di recupera dati moderni offre funzionalità di mashup di dati e la trasformazione dei dati di un'enorme utilizzando il generatore delle query di dati e le espressioni di M.

L'esperienza di recupera dati moderni fornisce supporto per un'ampia gamma di origini dati. In futuro, gli aggiornamenti verranno includono il supporto per ulteriormente.

![AS_Get_Data_in_SSDT](../analysis-services/media/as-get-data-in-ssdt.png)

 Un'interfaccia utente intuitiva e potente facilita la selezione di dati e funzionalità di trasformazione/mashup di dati più semplice che mai.

![Mashup avanzate](../analysis-services/media/as-get-data-advanced.png)


Esperienza moderna recupera dati e le funzionalità di mashup M non si applicano a upraded modelli tabulari esistente dal livello di compatibilità 1200 di 1400. La nuova esperienza si applica solo ai nuovi modelli creati a livello di compatibilità 1400.

## <a name="encoding-hints"></a>Hint di codifica
Questa versione introduce gli hint di codifica, una funzionalità avanzata, usata per ottimizzare l'elaborazione (aggiornamento di dati) dei modelli tabulari di grandi dimensioni in memoria. Per comprendere meglio la codifica, vedere [prestazioni ottimizzazione di modelli tabulari in SQL Server 2012 Analysis Services](https://msdn.microsoft.com/library/dn393915.aspx) white paper per comprendere meglio la codifica.

* Codifica del valore fornisce migliori prestazioni di query per le colonne che sono in genere utilizzata solo per le aggregazioni.

* La codifica hash è preferibile per colonne di raggruppamento (spesso valori di tabella della dimensione) e le chiavi esterne. Colonne di tipo stringa sono sempre con codificata hash.

Le colonne numeriche è possono utilizzare uno di questi metodi di codifica. Quando Analysis Services viene avviato l'elaborazione di una tabella, se la tabella è vuota (con o senza partizioni) o è in corso un'operazione di elaborazione di tabella completa, per ogni colonna numerica determinare se applicare valore o la codifica hash vengono estratti i valori di esempi . Per impostazione predefinita, viene scelto di codifica del valore quando l'esempio di valori distinct nella colonna è sufficiente – in caso contrario la codifica hash in genere fornisce una migliore compressione. È possibile per Analysis Services modificare il metodo di codifica dopo la colonna è parzialmente elaborata in base alle informazioni sulla distribuzione dei dati e riavviare il processo di codifica. Tuttavia, ciò aumenta il tempo di elaborazione ed è inefficiente. Il white paper ottimizzazione delle prestazioni viene illustrata la codifica nuovamente in modo più dettagliato e viene descritto come rilevare utilizzando SQL Server Profiler.

Gli hint di codifica consentono i creatori di modelli specificare una preferenza per il metodo di codifica specificato la conoscenza di dati di profilatura e/o in risposta a ricodifica gli eventi di traccia. Poiché l'aggregazione su colonne con codifica hash è più lento su colonne con valore codificato, codifica del valore può essere specificata come hint per tali colonne. Non è garantito che la preferenza è stata applicata. Si tratta di un hint anziché un'impostazione. Per specificare un hint di codifica, impostare la proprietà EncodingHint nella colonna. I valori possibili sono "Default", "Value" e "Hash". Il seguente frammento di JSON in base a metadati dai file Model.bim Specifica valore di codifica per la colonna Sales Amount.

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

## <a name="ragged-hierarchies"></a>Gerarchie incomplete
Nei modelli tabulari è possibile modellare le gerarchie padre-figlio. Le gerarchie con un numero di livelli diverso sono spesso definite gerarchie incomplete. Per impostazione predefinita, le gerarchie di questo tipo presentano spazi vuoti nei livelli al di sotto del figlio minore. Di seguito è riportato un esempio di una gerarchia incompleta in un organigramma:

![AS_Ragged_Hierarchy](../analysis-services/media/as-ragged-hierarchy.png)

In questa versione è stata introdotta la proprietà **Hide Members** (Nascondi membri). È possibile impostare la proprietà **Hide Members** (Nascondi membri) relativa a una gerarchia su **Hide blank members**(Nascondi membri vuoti).

![AS_Hide_Blank_Members](../analysis-services/media/as-hide-blank-members.png)

 >[!NOTE]
 > I membri vuoti nel modello sono rappresentati da un valore vuoto di DAX, non da una stringa vuota.

Quando la proprietà è impostata su **Hide blank members**(Nascondi membri vuoti) e il modello è distribuito, nei client di creazione report come Excel viene visualizzata una versione più leggibile della gerarchia.

![AS_Non_Ragged_Hierarchy](../analysis-services/media/as-non-ragged-hierarchy.png)


## <a name="detail-rows"></a>Righe di dettaglio
È ora possibile definire un set di righe personalizzato che contribuisce a un valore di misura. La funzionalità Righe di dettaglio è paragonabile all'azione di drill-through predefinita nei modelli multidimensionali. Ciò consente agli utenti finali di visualizzare le informazioni in modo più dettagliato rispetto al livello aggregato. 

La tabella pivot seguente mostra i valori annuali di Internet Total Sales del modello tabulare di esempio di AdventureWorks. Per visualizzare le righe di dettaglio è possibile fare clic con il pulsante destro del mouse su una cella con un valore aggregato della misura e quindi scegliere **Mostra dettagli** .

![AS_Show_Details](../analysis-services/media/as-show-details.png)

Per impostazione predefinita, vengono visualizzati i dati associati nella tabella Internet Sales. Questo comportamento limitato spesso non è significativo per l'utente perché la tabella può non includere le colonne necessarie per visualizzare informazioni utili, ad esempio il nome del cliente e i dati relativi agli ordini. Con Righe di dettaglio, è possibile specificare una proprietà **Detail Rows Expression** (Espressione righe di dettaglio) per le misure.

#### <a name="detail-rows-expression-property-for-measures"></a>Proprietà Detail Rows Expression (Espressione righe di dettaglio) per le misure
La proprietà **Detail Rows Expression** (Espressione righe di dettaglio) per le misure consente agli autori di modelli di personalizzare le colonne e le righe restituite all'utente finale.

![AS_Detail_Rows_Expression_Property](../analysis-services/media/as-detail-rows-expression-property.png)

Il [SELECTCOLUMNS](https://msdn.microsoft.com/library/mt761759.aspx) funzione DAX viene comunemente utilizzato in un'espressione di righe di dettaglio. L'esempio seguente definisce le colonne da restituire per le righe della tabella Internet Sales nel modello tabulare di esempio di AdventureWorks:

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
Oltre alle misure, anche le tabelle hanno una proprietà per definire un'espressione di righe di dettaglio. La proprietà **Default Detail Rows Expression** (Espressione predefinita righe di dettaglio) viene usata come impostazione predefinita per tutte le misure all'interno della tabella. Le misure che non dispongono di propria espressione definita eredita l'espressione della tabella e Mostra il set definito per la tabella di righe. Ciò consente di riutilizzare le espressioni e nuove misure aggiunte alla tabella in un secondo momento automaticamente eredita l'espressione.

![AS_Default_Detail_Rows_Expression](../analysis-services/media/as-default-detail-rows-expression.png)
 
#### <a name="detailrows-dax-function"></a>Funzione DAX DETAILROWS
In questa versione è inclusa una nuova funzione DAX `DETAILROWS` che restituisce il set di righe definito dall'espressione delle righe di dettaglio. Funziona in modo simile all'istruzione `DRILLTHROUGH` in MDX, che è anche compatibile con le espressioni delle righe di dettaglio definite nei modelli tabulari.

La query DAX seguente restituisce il set di righe definito dall'espressione delle righe di dettaglio per la misura o la relativa tabella. Se non è definita alcuna espressione, vengono restituiti i dati per la tabella Internet Sales perché è quella che contiene la misura.

```
EVALUATE DETAILROWS([Internet Total Sales])
```

## <a name="object-level-security"></a>Sicurezza a livello di oggetto
Questa versione introduce [sicurezza a livello di oggetto](../analysis-services/tabular-models/object-level-security.md) per le tabelle e colonne. Oltre a limitare l'accesso ai dati di tabelle e colonne, nomi di tabella e colonna sensibili possono essere protette. Ciò consente di impedire a un utente malintenzionato di individuare una tabella esistente.

Sicurezza a livello di oggetto deve essere impostata utilizzando i metadati basato su JSON, Tabular Model Scripting Language (TMSL) o tabulare oggetto modello TOM (). 

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

## <a name="dynamic-management-views-dmvs"></a>Viste a gestione dinamica (DMV)
[Viste a gestione dinamica](../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md) sono query in SQL Server Profiler che restituiscono informazioni sulle operazioni del server locale e lo stato del server.
Questa versione include miglioramenti apportati alla [viste a gestione dinamica](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) (DMV) per i modelli tabulari a livello di compatibilità 1200 e 1400 di.

[DISCOVER_CALC_DEPENDENCY](../analysis-services/schema-rowsets/xml/discover-calc-dependency-rowset.md) ora funziona con i modelli tabulari 1200 e 1400. I modelli tabulari 1400 mostrano le dipendenze tra le partizioni di M, M espressioni e origini dati strutturati. Per ulteriori informazioni, vedere il [blog di Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/07/17/whats-new-in-sql-server-2017-rc1-for-analysis-services/).

[MDSCHEMA_MEASUREGROUP_DIMENSIONS](../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md) sono state migliorate per questa DMV, viene utilizzata da vari strumenti client per indicare misura dimensionalità. Ad esempio, la funzionalità di esplorazione in tabelle Pivot di Excel consente all'utente di cross-drill alle dimensioni correlate per le misure selezionate. Questa versione consente di correggere le colonne della cardinalità, che sono state in precedenza con valori non corretti.

## <a name="dax-enhancements"></a>Miglioramenti apportati a DAX
Questa versione include il supporto per le funzionalità e nuove funzioni DAX. Per sfruttare i vantaggi, è necessario utilizzare la versione più recente di SSDT. Per ulteriori informazioni, vedere [funzioni DAX nuovo](https://msdn.microsoft.com/library/mt704075.aspx).

Una delle parti più importanti delle nuove funzionalità DAX è il nuovo [operatore IN / funzione CONTAINSROW](https://msdn.microsoft.com/library/mt842621.aspx) per le espressioni DAX. È simile all'operatore [`TSQL IN`](https://msdn.microsoft.com/library/ms177682.aspx) comunemente usato per specificare più valori in una clausola `WHERE` .

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

## <a name="additional-improvements"></a>Ulteriori miglioramenti
Oltre a tutte le nuove funzionalità, Analysis Services, SSDT e SSMS includono anche i seguenti miglioramenti:

* Riutilizzo di gerarchia e di colonne rese disponibili in posizioni più utili nell'elenco dei campi di Power BI.
* Relazioni di data per creare relazioni con dimensioni di data in base ai campi di Data.
* Opzione di installazione predefinita di Analysis Services è ora per la modalità tabulare.
* Nuove origini dati recupera dati (Power Query).
* Editor DAX per SSDT.
* Origini di dati DirectQuery esistente supportano per milione di query.
* Miglioramenti di SQL Server Management Studio, ad esempio la visualizzazione, modifica e il supporto per le origini dati strutturate di script.



## <a name="see-also"></a>Vedere anche
[Note sulla versione di SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)   
[Novità di SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md)
