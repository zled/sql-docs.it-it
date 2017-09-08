---
title: Come creare query MDX con olapR | Microsoft Docs
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: c12b988e-be7e-41ba-a84c-299a5c45d4ab
caps.latest.revision: 3
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: adcc1c80fdd04cfa3f49b550e5ea5fd8cc34003a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="how-to-create-mdx-queries-using-olapr"></a>Come creare query MDX con olapR
## <a name="how-to-build-an-mdx-query-from-r"></a>Come creare una query MDX da R

1. Definire una stringa di connessione che specifica l'origine dati OLAP (istanza di SSAS) e il provider MSOLAP.

2. Usare la funzione `OlapConnection(connectionString)` per creare un handle per la query MDX e passare la stringa di connessione.

3. Usare il costruttore `Query()` per creare un'istanza di un oggetto query.

4. Usare le funzioni helper seguenti per fornire altri dettagli sulle dimensioni e sulle misure da includere nella query MDX:
     + `cube()` Specificare il nome del database SSAS.
     + `columns()` Specificare i nomi delle misure da usare nell'argomento ON COLUMNS.  
     + `rows()` Specificare i nomi delle misure da usare nell'argomento ON ROWS.
     + `slicers()` Specificare un campo o i membri da usare come filtro dei dati. Si tratta di un filtro che viene applicato a tutti i dati delle query MDX.
     
     + `axis()` Specificare il nome di un altro asse da usare nella query. Un cubo OLAP può contenere un massimo di 128 assi di query. In genere, i primi quattro assi sono definiti Column, Row, Page e Chapter. Se la query è relativamente semplice, è possibile usare le funzioni `columns`, `rows`e così via per crearla.     
     È tuttavia possibile usare anche la funzione `axis()` con un valore di indice diverso da zero per creare una query MDX con molti qualificatori o aggiungere altre dimensioni come qualificatori.

5. Passare l'handle e la query MDX completata nelle funzioni `executeMD` o `execute2D`, a seconda della forma dei risultati.

  + `executeMD` restituisce una matrice multidimensionale
  + `execute2D` restituisce un frame di dati bidimensionale (tabulare)


## <a name="how-to-run-an-existing-mdx-query-from-r"></a>Come eseguire una query MDX esistente da R

1. Definire una stringa di connessione che specifica l'origine dati OLAP (istanza di SSAS) e il provider MSOLAP.

2. Usare la funzione `OlapConnection(connectionString)` per creare un handle per la query MDX e passare la stringa di connessione.

3. Definire una variabile R per archiviare il testo della query MDX.

4. Passare l'handle e la variabile contenente la query MDX nella funzione `executeMD` o `execute2D`, a seconda della forma dei risultati.

    + `executeMD` restituisce una matrice multidimensionale
    + `execute2D` restituisce un frame di dati bidimensionale (tabulare)



## <a name="examples"></a>Esempi

### <a name="1-basic-mdx-with-slicer"></a>1. Query MDX di base con filtro dei dati

Questa query MDX seleziona le _misure_ per il conteggio e la quantità di Internet sales count e Sales amount e li inserisce nell'asse Column. Aggiunge un membro della dimensione SalesTerritory come *filtro dei dati*per filtrare la query in modo da includere nei calcoli solo le vendite relative all'Australia.

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, 
{[Product].[Product Line].[Product Line].MEMBERS} ON ROWS 
FROM [Analysis Services Tutorial] 
WHERE [Sales Territory].[Sales Territory Country].[Australia]
```

+ Nelle colonne è possibile specificare più misure come elementi di una stringa con valori delimitati da virgole.
+ L'asse Row usa tutti i valori possibili (tutti i MEMBERS) della dimensione "Product Line". 
+ Questa query restituisce una tabella con tre colonne, che contiene un riepilogo di _rollup_ delle vendite Internet relative a tutti i paesi. 
+ La clausola WHERE descrive l' _asse del filtro dei dati_. Il filtro dei dati usa un membro della dimensione SalesTerritory per filtrare la query in modo da includere nei calcoli solo le vendite relative all'Australia.

#### <a name="to-build-this-query-using-the-functions-provided-in-olapr"></a>Per compilare la query con le funzioni di olapR

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)

qry <- Query()
cube(qry) <- "[Analysis Services Tutorial]"
columns(qry) <- c("[Measures].[Internet Sales Count]", "[Measures].[Internet Sales-Sales Amount]")
rows(qry) <- c("[Product].[Product Line].[Product Line].MEMBERS") 
slicers(qry) <- c("[Sales Territory].[Sales Territory Country].[Australia]")

result1 <- executeMD(ocs, qry)

```

#### <a name="to-run-this-query-as-a-predefined-mdx-string"></a>Per eseguire la query come stringa MDX predefinita

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)

mdx <- "SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, {[Product].[Product Line].[Product Line].MEMBERS} ON ROWS FROM [Analysis Services Tutorial] WHERE [Sales Territory].[Sales Territory Country].[Australia]"

result2 <- execute2D(ocs, mdx)
```

Si noti che, se si definisce una query con il Generatore MDX in SQL Server Management Studio e quindi salva la stringa MDX, gli assi verranno numerati a partire da 0, come illustrato di seguito: 

~~~~
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Country].[Australia]
~~~~

La query può sempre essere eseguita come stringa MDX predefinita. Tuttavia, per creare la stessa query con R usando la funzione `axis()`, assicurarsi di numerare gli assi a partire da 1.


### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2. Esplorare i cubi e i relativi campi in un'istanza di SSAS

È possibile usare la funzione `explore` per restituire un elenco di cubi, dimensioni o membri da usare per creare una query. Questa funzione è utile se non si può accedere ad altri strumenti di esplorazione OLAP o se si desidera modificare o creare la query MDX a livello di codice.

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>Per elencare i cubi disponibili per la connessione specificata

Per visualizzare tutti i cubi o le prospettive dell'istanza per i quali si dispone dei diritti di visualizzazione, specificare l'handle come argomento di `explore`.
Si noti che il risultato finale non è un cubo. TRUE indica semplicemente che l'operazione sui metadati è riuscita. Se gli argomenti non sono validi, viene generato un errore.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)
explore(ocs)
```

| Risultati  |  
| ----|
| _Analysis Services Tutorial_|
|_Internet Sales_|
|_Reseller Sales_|
|_Sales Summary_|
|_[1] TRUE_|
     


#### <a name="to-get-a-list-of-cube-dimensions"></a>Per ottenere un elenco delle dimensioni del cubo

Per visualizzare tutte le dimensioni del cubo o della prospettiva, specificare il nome del cubo o della prospettiva.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs \<- OlapConnection(cnnstr)
explore(ocs, "Sales")
```

| Risultati  |  
| ----|
| _Customer_|
|_Date_|
|_Region_|


#### <a name="to-return-all-members-of-the-specified-dimension-and-hierarchy"></a>Per restituire tutti i membri della dimensione e della gerarchia specificate

Dopo aver definito l'origine e la creazione dell'handle, specificare il cubo, la dimensione e la gerarchia da restituire.
Si noti che gli elementi nei risultati restituiti con il prefisso **->** rappresentano gli elementi figlio del membro precedente.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs \<- OlapConnection(cnnstr)
explore(ocs, "Analysis Services Tutorial", "Product", "Product Categories", "Category")
```

| Risultati  |  
| ----|
| _Accessories_|
|_Bikes_|
|_Clothing_|
|_Components_|
|-> Assembly Components|
|-> Assembly Components|



## <a name="see-also"></a>Vedere anche

[Uso dei dati dai cubi OLAP in R](../../advanced-analytics/r-services/using-data-from-olap-cubes-in-r.md)

