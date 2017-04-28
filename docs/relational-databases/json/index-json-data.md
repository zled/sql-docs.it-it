---
title: Indicizzare dati JSON | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 06/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, indexing JSON data
- indexing JSON data
ms.assetid: ced241e1-ff09-4d6e-9f04-a594a9d2f25e
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: cf3c58c7d71a98bfaa1f27611762bf7fb3fe8725
ms.lasthandoff: 04/11/2017

---
# <a name="index-json-data"></a>Indicizzazione dei dati JSON
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Gli indici del database migliorano le prestazioni delle operazioni di filtro e ordinamento. Senza indici, SQL Server deve eseguire un'analisi completa della tabella ogni volta che viene eseguita una query sui dati.  
  
 JSON non è un tipo di dati incorporato in SQL Server 2016 e SQL Server 2016 non dispone di indici JSON personalizzati. Tuttavia, è possibile ottimizzare le query su documenti JSON tramite indici standard.  
  
## <a name="index-json-properties-by-using-computed-columns"></a>Indicizzazione delle proprietà JSON mediante colonne calcolate  
 Quando si archiviano i dati JSON in SQL Server, in genere si desidera filtrare o ordinare i risultati delle query in base alle proprietà dei documenti JSON.  
  
 In questo esempio, la tabella AdventureWorks SalesOrderHeader include una colonna "Info" che contiene varie informazioni sugli ordini di vendita - ad esempio informazioni sul cliente, sul venditore, sugli indirizzi di spedizione o fatturazione e così via. Si desidera usare i valori della colonna Info per filtrare gli ordini di vendita per un cliente. Di seguito viene riportata la query da ottimizzare usando un indice.  
  
```tsql  
SELECT SalesOrderNumber,OrderDate,JSON_VALUE(Info,'$.Customer.Name') AS CustomerName
FROM Sales.SalesOrderHeader
WHERE JSON_VALUE(Info,'$.Customer.Name')=N'Aaron Campbell' 
```  
  
 Se si desidera velocizzare i filtri o le clausole ORDER BY su una proprietà in un documento JSON, è possibile usare gli stessi indici in uso in altre colonne. Tuttavia, non è possibile fare direttamente riferimento alle proprietà nei documenti JSON. Innanzitutto è necessario creare una "colonna virtuale" che restituisca i valori desiderati per il filtraggio. È quindi necessario creare un indice su quella colonna virtuale.  
  
 Nell'esempio seguente viene creata una colonna calcolata che può essere usata per l'indicizzazione e successivamente viene creato un indice in quella colonna. In questo esempio viene creata una colonna che espone il nome del cliente archiviato nel percorso $.Customer.Name nei documenti JSON.  
  
```tsql  
ALTER TABLE Sales.SalesOrderHeader
ADD vCustomerName AS JSON_VALUE(Info,'$.Customer.Name')

CREATE INDEX idx_soh_json_CustomerName
ON Sales.SalesOrderHeader(vCustomerName)  
```  
  
 La colonna calcolata non è persistente. Non occupa spazio aggiuntivo nella tabella. È calcolata solo quando è necessario ricostruire l'indice.  
  
 È importante creare la colonna calcolata con la stessa espressione che si intende usare nelle query, in questo esempio `JSON_VALUE(Info, '$.Customer.Name')`.  
  
 Non è necessario riscrivere le query. Se si usano espressioni con la funzione JSON_VALUE, SQL Server rileva la presenza di una colonna calcolata equivalente con la stessa espressione e, se possibile, applica un indice. Di seguito viene riportato il piano di esecuzione per la query in questo esempio.  
  
 ![Piano di esecuzione](../../relational-databases/json/media/jsonindexblog1.png "Piano di esecuzione")  
  
 Anziché un'analisi completa della tabella, SQL Server usa un indice seek nell'indice non cluster e individua le righe che soddisfano le condizioni specificate. Quindi, usa una ricerca chiave nella tabella SalesOrderHeader per recuperare altre colonne a cui si fa riferimento nella query - in questo esempio, SalesOrderNumber e OrderDate.  
  
 Se si aggiungono le colonne richieste nell'indice JSON, è possibile evitare questa ulteriore ricerca nella tabella. È possibile aggiungere tali colonne come colonne incluse standard, come illustrato nell'esempio seguente.  
  
```tsql  
CREATE INDEX idx_soh_json_CustomerName
ON Sales.SalesOrderHeader(vCustomerName)
INCLUDE(SalesOrderNumber,OrderDate)
```  
  
 In questo caso SQL Server non legge i dati aggiuntivi della tabella SalesOrderHeader perché tutto il necessario è incluso nell'indice non cluster JSON. Questo è un buon metodo per combinare i dati JSON e di colonna nelle query e per creare indici ottimali per il carico di lavoro.  
  
## <a name="json-indexes-are-collation-aware-indexes"></a>Gli indici JSON sono in grado di riconoscere le regole di confronto  
 Una caratteristica importante degli indici JSON è che sono in grado di riconoscere le regole di confronto. Il risultato della funzione JSON_VALUE è un valore di testo che eredita le regole di confronto dall'espressione di input. Di conseguenza, i valori dell'indice vengono ordinati usando le regole di confronto definite delle colonne di origine.  
  
 Per dimostrare questo concetto, nell'esempio seguente viene creata una semplice tabella di raccolta insieme con una chiave primaria e contenuto JSON.  
  
```tsql  
CREATE TABLE JsonCollection
 (
  id INT IDENTITY CONSTRAINT PK_JSON_ID PRIMARY KEY,
  json NVARCHAR(MAX) COLLATE SERBIAN_CYRILLIC_100_CI_AI
  CONSTRAINT [Content should be formatted as JSON]
  CHECK(ISJSON(json)>0)
 ) 
```  
  
 Il comando precedente consente di specificare le regole di confronto per il serbo (cirillico) per la colonna JSON. Nell'esempio seguente la tabella viene popolata e viene creato un indice nella proprietà del nome.  
  
```tsql  
INSERT INTO JsonCollection
VALUES
(N'{"name":"Иво","surname":"Андрић"}'),
(N'{"name":"Андрија","surname":"Герић"}'),
(N'{"name":"Владе","surname":"Дивац"}'),
(N'{"name":"Новак","surname":"Ђоковић"}'),
(N'{"name":"Предраг","surname":"Стојаковић"}'),
(N'{"name":"Михајло","surname":"Пупин"}'),
(N'{"name":"Борислав","surname":"Станковић"}'),
(N'{"name":"Владимир","surname":"Грбић"}'),
(N'{"name":"Жарко","surname":"Паспаљ"}'),
(N'{"name":"Дејан","surname":"Бодирога"}'),
(N'{"name":"Ђорђе","surname":"Вајферт"}'),
(N'{"name":"Горан","surname":"Бреговић"}'),
(N'{"name":"Милутин","surname":"Миланковић"}'),
(N'{"name":"Никола","surname":"Тесла"}')
GO  
ALTER TABLE JsonCollection
ADD vName AS JSON_VALUE(json,'$.name')

CREATE INDEX idx_name
ON JsonCollection(vName)
```  
  
 I comandi precedenti creano un indice standard nel nome virtuale della colonna calcolata, che rappresenta il valore della proprietà $.name JSON. Nella tabella codici per il serbo (cirillico), l'ordine delle lettere è ‘А’,’Б’,’В’,’Г’,’Д’,’Ђ’,’Е’, ecc. L'ordine degli elementi nell'indice è conforme alle regole per il serbo (cirillico) perché il risultato della funzione JSON_VALUE eredita le regole di confronto dalla colonna di origine. Nell'esempio seguente viene eseguita una query su questa raccolta e i risultati vengono ordinati in base al nome.  
  
```tsql  
SELECT JSON_VALUE(json,'$.name'),*
FROM JsonCollection
ORDER BY JSON_VALUE(json,'$.name')
```  
  
 Se si esamina il piano di esecuzione, si noterà che vengono usati valori ordinati dall'indice non cluster.  
  
 ![Piano di esecuzione](../../relational-databases/json/media/jsonindexblog2.png "Piano di esecuzione")  
  
 Anche se la query include una clausola ORDER BY, il piano di esecuzione non usa un operatore di ordinamento. L'indice JSON è già ordinato in base alle regole per il serbo (cirillico). SQL Server può pertanto usare l'indice non cluster in cui risultati sono già ordinati.  
  
 Tuttavia, se le regole di confronto dell'ordine vengono cambiate in base all'espressione (ad esempio, se si mette `COLLATE French_100_CI_AS_SC` dopo la funzione JSON_VALUE) si ottiene un piano di esecuzione di query diverso.  
  
 ![Piano di esecuzione](../../relational-databases/json/media/jsonindexblog3.png "Piano di esecuzione")  
  
 Poiché l'ordine dei valori in corrispondenza dell'indice non è conforme alle regole di confronto per il francese, SQL Server non può usare l'indice per ordinare i risultati. Pertanto, aggiunge un operatore di ordinamento che ordina i risultati usando le regole di confronto per il francese.  
  
  

