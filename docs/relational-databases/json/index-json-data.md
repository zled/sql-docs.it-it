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
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 3ed7a51b28d2b17b3239f971d0f4f684bec145cd
ms.contentlocale: it-it
ms.lasthandoff: 06/09/2017

---
# <a name="index-json-data"></a>Indicizzazione dei dati JSON
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

In SQL Server 2016, JSON non è un tipo di dati incorporati e SQL Server non dispone di indici JSON personalizzati. È possibile ottimizzare le query su documenti JSON, tuttavia, tramite indici standard. 

Gli indici di database migliorano le prestazioni delle operazioni di filtro e ordinamento. Senza indici, SQL Server deve eseguire un'analisi completa della tabella ogni volta che viene eseguita una query sui dati.  
  
## <a name="index-json-properties-by-using-computed-columns"></a>Indicizzazione delle proprietà JSON mediante colonne calcolate  
Quando si archiviano i dati JSON in SQL Server, in genere si desidera filtrare o ordinare i risultati di query da uno o più *proprietà* dei documenti JSON.  

### <a name="example"></a>Esempio 
In questo esempio, si supponga che AdventureWorks `SalesOrderHeader` tabella include un `Info` colonna che contiene varie informazioni in formato JSON sugli ordini di vendita. Ad esempio, contiene informazioni sui clienti, venditore, gli indirizzi di spedizione e di fatturazione e così via. Si desidera utilizzare i valori di `Info` colonna per filtrare gli ordini di vendita per un cliente.

### <a name="query-to-optimize"></a>Query da ottimizzare
Di seguito è riportato un esempio del tipo di query da ottimizzare usando un indice.  
  
```sql  
SELECT SalesOrderNumber,
    OrderDate,
    JSON_VALUE(Info, '$.Customer.Name') AS CustomerName
FROM Sales.SalesOrderHeader
WHERE JSON_VALUE(Info, '$.Customer.Name') = N'Aaron Campbell' 
```  

### <a name="example-index"></a>Indice di esempio
Se si desidera velocizzare i filtri o `ORDER BY` clausole su una proprietà in un documento JSON, è possibile utilizzare gli stessi indici che già in uso in altre colonne. Non è tuttavia possibile *direttamente* fare riferimento alle proprietà nei documenti JSON.
    
1.  In primo luogo, è necessario creare una "colonna virtuale" che restituisce i valori che si desidera utilizzare per il filtro.
2.  È quindi necessario creare un indice su quella colonna virtuale.  
  
Nell'esempio seguente viene creata una colonna calcolata che può essere utilizzata per l'indicizzazione. Quindi, viene creato un indice sulla nuova colonna calcolata. Questo esempio viene creata una colonna che espone il nome del cliente, archiviato nel `$.Customer.Name` percorso dei dati JSON. 
  
```sql  
ALTER TABLE Sales.SalesOrderHeader
ADD vCustomerName AS JSON_VALUE(Info,'$.Customer.Name')

CREATE INDEX idx_soh_json_CustomerName
ON Sales.SalesOrderHeader(vCustomerName)  
```  
### <a name="more-info-about-the-computed-column"></a>Altre informazioni sulla colonna calcolata 
La colonna calcolata non è persistente. È calcolata solo quando è necessario ricostruire l'indice. Non occupa spazio aggiuntivo nella tabella.   
  
È importante che si crea la colonna calcolata con la stessa espressione che si intende utilizzare nelle query, in questo esempio, l'espressione è `JSON_VALUE(Info, '$.Customer.Name')`.  
  
Non è necessario riscrivere le query. Se si usano espressioni con la `JSON_VALUE` funzione, come illustrato nella query di esempio precedente, SQL Server rileva che non vi è una colonna calcolata equivalente con la stessa espressione e si applica un indice, se possibile.

### <a name="execution-plan-for-this-example"></a>Piano di esecuzione per questo esempio
Di seguito è riportato il piano di esecuzione per la query in questo esempio.  
  
![Piano di esecuzione](../../relational-databases/json/media/jsonindexblog1.png "Piano di esecuzione")  
  
Anziché un'analisi completa della tabella, SQL Server usa un indice seek nell'indice non cluster e individua le righe che soddisfano le condizioni specificate. Quindi, viene usata una ricerca nella chiave di `SalesOrderHeader` tabella per recuperare altre colonne a cui fa riferimento nella query - in questo esempio, `SalesOrderNumber` e `OrderDate`.  
 
### <a name="optimize-the-index-further-with-included-columns"></a>Ottimizzare ulteriormente l'indice con colonne incluse
Se si aggiungono le colonne richieste nell'indice, è possibile evitare questa ulteriore ricerca nella tabella. È possibile aggiungere tali colonne come colonne incluse standard, come illustrato nell'esempio seguente, che estende il `CREATE INDEX` esempio illustrato in precedenza.  
  
```sql  
CREATE INDEX idx_soh_json_CustomerName
ON Sales.SalesOrderHeader(vCustomerName)
INCLUDE(SalesOrderNumber,OrderDate)
```  
  
In questo caso SQL Server non deve leggere i dati aggiuntivi di `SalesOrderHeader` tabella perché tutto il necessario è incluso nell'indice non cluster JSON. Questo è un buon metodo per combinare i dati JSON e di colonna nelle query e per creare indici ottimali per il carico di lavoro.  
  
## <a name="json-indexes-are-collation-aware-indexes"></a>Gli indici JSON sono in grado di riconoscere le regole di confronto  
Una caratteristica importante degli indici sui dati JSON è che gli indici sono in grado di riconoscere le regole di confronto. Il risultato di `JSON_VALUE` funzione utilizzato quando si crea la colonna calcolata è un valore di testo che eredita le regole di confronto dall'espressione di input. Di conseguenza, i valori dell'indice vengono ordinati usando le regole di confronto definite delle colonne di origine.  
  
Per dimostrare questo concetto, nell'esempio seguente viene creata una semplice tabella di raccolta insieme con una chiave primaria e contenuto JSON.  
  
```sql  
CREATE TABLE JsonCollection
 (
  id INT IDENTITY CONSTRAINT PK_JSON_ID PRIMARY KEY,
  json NVARCHAR(MAX) COLLATE SERBIAN_CYRILLIC_100_CI_AI
  CONSTRAINT [Content should be formatted as JSON]
  CHECK(ISJSON(json)>0)
 ) 
```  
  
Il comando precedente consente di specificare le regole di confronto per il serbo (cirillico) per la colonna JSON. Nell'esempio seguente la tabella viene popolata e viene creato un indice nella proprietà del nome.  
  
```sql  
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
  
I comandi precedenti creano un indice standard per la colonna calcolata `vName`, che rappresenta il valore JSON `$.name` proprietà. Nella tabella codici per il serbo (cirillico), l'ordine delle lettere è ‘А’,’Б’,’В’,’Г’,’Д’,’Ђ’,’Е’, ecc. L'ordine degli elementi nell'indice è conforme alle regole di Serbo (cirillico) perché il risultato di `JSON_VALUE` funzione eredita le regole di confronto dalla colonna di origine. Nell'esempio seguente viene eseguita una query su questa raccolta e i risultati vengono ordinati in base al nome.  
  
```sql  
SELECT JSON_VALUE(json,'$.name'),*
FROM JsonCollection
ORDER BY JSON_VALUE(json,'$.name')
```  
  
 Se si esamina il piano di esecuzione, si noterà che vengono usati valori ordinati dall'indice non cluster.  
  
 ![Piano di esecuzione](../../relational-databases/json/media/jsonindexblog2.png "Piano di esecuzione")  
  
 Anche se la query include un `ORDER BY` clausola, il piano di esecuzione non usa un operatore di ordinamento. L'indice JSON è già ordinato in base alle regole per il serbo (cirillico). SQL Server può pertanto usare l'indice non cluster in cui risultati sono già ordinati.  
  
 Tuttavia, se si modificano le regole di confronto del `ORDER BY` espressione, ad esempio, se si mette `COLLATE French_100_CI_AS_SC` dopo il `JSON_VALUE` funzione, si ottiene un piano di esecuzione di query diverso.  
  
 ![Piano di esecuzione](../../relational-databases/json/media/jsonindexblog3.png "Piano di esecuzione")  
  
 Poiché l'ordine dei valori in corrispondenza dell'indice non è conforme alle regole di confronto per il francese, SQL Server non può usare l'indice per ordinare i risultati. Pertanto, aggiunge un operatore di ordinamento che ordina i risultati usando le regole di confronto per il francese.  
 
## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Acquisire familiarità con il supporto JSON integrato in SQL Server  
Per un numero elevato di soluzioni specifiche, casi di utilizzo e indicazioni, vedere il [post di blog sul supporto JSON predefinito](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e Database SQL di Azure per Microsoft Program Manager Jovan Popovic.

