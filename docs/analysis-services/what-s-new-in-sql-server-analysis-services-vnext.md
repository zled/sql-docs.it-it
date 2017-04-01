---
title: "Novit&#224; di SQL Server Analysis Services vNext | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1eb6afc9-76ed-45a2-a188-374a4fc23224
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# Novit&#224; di SQL Server Analysis Services vNext
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

## <a name="sql-server-analysis-services-on-windows-ctp-12"></a>SQL Server Analysis Services in Windows CTP 1.2

In questa versione non sono presenti nuove funzionalità. I miglioramenti includono correzioni di bug e o potenziamento delle prestazioni.

L'ultima versione di anteprima di SQL Server Data Tools (SSDT), che coincide con Server SQL vNext CTP 1.2, migliora la nuova esperienza moderna per il recupero di dati introdotta nella versione CTP 1.1 con un nuovo menu dell'editor di query e una nuova funzionalità di accesso rapido. 

## <a name="sql-server-analysis-services-on-windows-ctp-11"></a>SQL Server Analysis Services in Windows CTP 1.1 

In questa versione sono stati introdotti miglioramenti per i modelli tabulari. 

### <a name="1400-compatibility-level-for-tabular-models"></a>Livello di compatibilità&1400; per i modelli tabulari
  Per poter sfruttare le funzionalità descritte in questo articolo, è necessario impostare il livello di compatibilità 1400 per i modelli tabulari nuovi o esistenti. Non è possibile distribuire i modelli con livello di compatibilità 1400 in SQL Server 2016 SP1 o versioni precedenti né effettuare il downgrade a livelli di compatibilità inferiori.
  
  Per creare nuovi progetti di modelli tabulari o aggiornare quelli esistenti con il livello di compatibilità 1400, scaricare e installare una **versione di anteprima** di [SQL Server Data Tools (SSDT) 17.0 RC2](https://go.microsoft.com/fwlink?LinkId=837939). 
  
In SSDT è possibile selezionare il nuovo livello di compatibilità 1400 durante la creazione di nuovi progetti di modelli tabulari. 

![AS_NewTabular1400Project](../analysis-services/media/as-newtabular1400project.png)

>[!NOTE] L'area di lavoro integrata nella versione di dicembre di SQL Server Data Tools (SSDT) supporta il livello di compatibilità 1400. Se si creano nuovi progetti di modelli tabulari in un'istanza del server dell'area di lavoro, tale istanza (o qualsiasi istanza in cui si esegue la distribuzione) deve essere [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 1.1. 

Per aggiornare un modello tabulare esistente in SSDT, in Esplora soluzioni fare clic con il pulsante destro del mouse su **Model.bim** e quindi in **Proprietà** impostare la proprietà **Livello di compatibilità** su **SQL Server vNext (1400)**. 

![AS_Model_Properties](../analysis-services/media/as-model-properties.png)

### <a name="modern-get-data-experience"></a>Funzionalità moderna per il recupero di dati
Nella versione di anteprima più recente di SQL Server Data Tools (SSDT), che coincide con la versione [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 1.1, è stata introdotta una funzionalità moderna per il **recupero di dati** per i modelli tabulari con livello di compatibilità 1400. Questa nuova funzionalità si basa su una funzionalità simile in Power BI Desktop e Microsoft Excel 2016.

![AS_Get_Data_in_SSDT](../analysis-services/media/as-get-data-in-ssdt.png)

>[!NOTE] Per questa versione è supportato un numero limitato di origini dati. Negli aggiornamenti futuri sarà incluso il supporto per altre funzionalità e origini dati.

Per altre informazioni sulla funzionalità moderna per il recupero di dati, vedere il [blog del team di Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2016/12/16/introducing-a-modern-get-data-experience-for-sql-server-vnext-on-windows-ctp-1-1-for-analysis-services/).

## <a name="ragged-hierarchies"></a>Gerarchie incomplete
Nei modelli tabulari è possibile modellare le gerarchie padre-figlio. Le gerarchie con un numero di livelli diverso sono spesso definite gerarchie incomplete. Per impostazione predefinita, le gerarchie di questo tipo presentano spazi vuoti nei livelli al di sotto del figlio minore. Di seguito è riportato un esempio di una gerarchia incompleta in un organigramma:

![AS_Ragged_Hierarchy](../analysis-services/media/as-ragged-hierarchy.png)

In questa versione è stata introdotta la proprietà **Hide Members** (Nascondi membri). È possibile impostare la proprietà **Hide Members** (Nascondi membri) relativa a una gerarchia su **Hide blank members** (Nascondi membri vuoti).

![AS_Hide_Blank_Members](../analysis-services/media/as-hide-blank-members.png)

 >[!NOTE] I membri vuoti nel modello sono rappresentati da un valore vuoto di DAX, non da una stringa vuota.

Quando la proprietà è impostata su **Hide blank members** (Nascondi membri vuoti) e il modello è distribuito, nei client di creazione report come Excel viene visualizzata una versione più leggibile della gerarchia.

![AS_Non_Ragged_Hierarchy](../analysis-services/media/as-non-ragged-hierarchy.png)

### <a name="detail-rows"></a>Righe di dettaglio
È ora possibile definire un set di righe personalizzato che contribuisce a un valore di misura. La funzionalità Righe di dettaglio è paragonabile all'azione di drill-through predefinita nei modelli multidimensionali. Ciò consente agli utenti finali di visualizzare le informazioni in modo più dettagliato rispetto al livello aggregato. 

La tabella pivot seguente mostra i valori annuali di Internet Total Sales del modello tabulare di esempio di AdventureWorks. Per visualizzare le righe di dettaglio è possibile fare clic con il pulsante destro del mouse su una cella con un valore aggregato della misura e quindi scegliere **Mostra dettagli**.

![AS_Show_Details](../analysis-services/media/as-show-details.png)

Per impostazione predefinita, vengono visualizzati i dati associati nella tabella Internet Sales. Questo comportamento limitato spesso non è significativo per l'utente perché la tabella può non includere le colonne necessarie per visualizzare informazioni utili, ad esempio il nome del cliente e i dati relativi agli ordini. Con Righe di dettaglio, è possibile specificare una proprietà **Detail Rows Expression** (Espressione righe di dettaglio) per le misure.

#### <a name="detail-rows-expression-property-for-measures"></a>Proprietà Detail Rows Expression (Espressione righe di dettaglio) per le misure
La proprietà **Detail Rows Expression** (Espressione righe di dettaglio) per le misure consente agli autori di modelli di personalizzare le colonne e le righe restituite all'utente finale.

![AS_Detail_Rows_Expression_Property](../analysis-services/media/as-detail-rows-expression-property.png)

In un'espressione di righe di dettaglio viene in genere usata la funzione DAX [SELECTCOLUMNS](https://msdn.microsoft.com/library/mt761759.aspx). L'esempio seguente definisce le colonne da restituire per le righe della tabella Internet Sales nel modello tabulare di esempio di AdventureWorks:

```
SELECTCOLUMNS(
    'Internet Sales',
    "Customer First Name", RELATED( Customer[Last Name]),
    "Customer Last Name", RELATED( Customer[First Name]),
    "Order Date", 'Internet Sales'[Order Date],
    "Internet Total Sales", [Internet Total Sales]
)
```

Con la proprietà definita e il modello distribuito, quando l'utente seleziona **Mostra dettagli** viene restituito un set di righe personalizzato che rispetta automaticamente il contesto del filtro della cella selezionata. In questo esempio vengono visualizzate solo le righe per il valore 2010:

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
Questa versione include un operatore `IN` per le espressioni DAX. È simile all'operatore [`TSQL IN`](https://msdn.microsoft.com/library/ms177682.aspx) comunemente usato per specificare più valori in una clausola `WHERE`.

In precedenza, era pratica comune specificare filtri con più valori usando l'operatore logico `OR`, come illustrato nell'espressione di misura seguente:

```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
                 'Product'[Color] = "Red"
            || 'Product'[Color] = "Blue"
            || 'Product'[Color] = "Black"
    )
```

Questo processo viene semplificato dall'operatore `IN`:
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], 'Product'[Color] IN { "Red", "Blue", "Black" }
    )
```

In questo caso, l'operatore `IN` fa riferimento a una tabella a colonna singola con 3 righe, una per ogni colore specificato. Si noti che nella sintassi del costruttore della tabella vengono usate le parentesi graffe.

Dal punto di vista funzionale, l'operatore `IN` equivale alla funzione `CONTAINSROW`:
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

Se si usa il nuovo operatore `IN`, l'espressione di misura precedente è formulata nel modo seguente:
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
## <a name="future-updates"></a>Aggiornamenti futuri
Altri miglioramenti verranno inclusi nella versione futura. Questo articolo verrà aggiornato con annunci significativi sulle nuove funzionalità di SQL Server vNext.
