---
title: Graph processing con SQL Server e Database SQL di Azure | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: graphs
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, overview
ms.assetid: ''
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 276ef0d34d04f58b0b23b213dc52faf5b404693e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43101811"
---
# <a name="graph-processing-with-sql-server-and-azure-sql-database"></a>Graph processing con SQL Server e Database SQL di Azure
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre funzionalità di database di grafi per modellare le relazioni molti-a-molti. Le relazioni di graph sono integrate [!INCLUDE[tsql-md](../../includes/tsql-md.md)] e ricevere i vantaggi dell'uso [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come sistema di gestione di database fondamentali.


## <a name="what-is-a-graph-database"></a>Che cos'è un database a grafo?  
Un database a grafo è una raccolta di nodi (o i vertici) e i bordi (o le relazioni). Un nodo rappresenta un'entità (ad esempio, una persona o un'organizzazione) e una rete perimetrale rappresenta una relazione tra i due nodi che si connette (ad esempio, mi piace o amici). I nodi e bordi possono avere proprietà associate. Ecco alcune funzionalità che rendono un database a grafo univoco:  
-   Perimetri o le relazioni sono entità di prima classe in un Database a grafo e possono avere attributi o le proprietà associate. 
-   Un bordo singolo può connettersi in modo flessibile più nodi in un Database a grafo.
-   È possibile esprimere facilmente criteri di ricerca e query di esplorazione multi hop.
-   È possibile esprimere query polimorfica e chiusura transitiva con facilità.

## <a name="when-to-use-a-graph-database"></a>Quando usare un database a grafo

Non è possibile ottenere un database a grafo, che non può essere ottenuta utilizzando un database relazionale. Tuttavia, un database a grafo può rendere più semplice esprimere determinato tipo di query. Inoltre, con le ottimizzazioni specifiche, determinate query siano migliori. La decisione di scegliere uno di essi può essere basata sui fattori seguenti:  
-   L'applicazione include i dati gerarchici. Il tipo di dati HierarchyID consente di implementare le gerarchie, ma presenta alcune limitazioni. Ad esempio, non consentono di archiviare più elementi padre per un nodo.
-   L'applicazione presenta le complesse relazioni molti-a-molti; l'evoluzione dell'applicazione, vengono aggiunte nuove relazioni.
-   È necessario analizzare le relazioni e i dati interconnessi.

## <a name="graph-features-introduced-in-includesssqlv14includessssqlv14-mdmd"></a>Funzionalità di Graph introdotte in [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 
Sta iniziando l'aggiunta di estensioni graph per SQL Server, per rendere più semplice l'esecuzione di query e l'archiviazione dei dati del grafico. Le funzionalità seguenti vengono introdotti nella prima versione. 


### <a name="create-graph-objects"></a>Creare gli oggetti di graph
[!INCLUDE[tsql-md](../../includes/tsql-md.md)] le estensioni consentirà agli utenti di creare le tabelle nodi o bordi. I nodi e bordi possono avere proprietà associate a essi. Poiché, nodi e archi vengono archiviati come tabelle, tutte le operazioni che sono supportate nelle tabelle relazionali sono supportate nella tabella nodi o bordi. Esempio:  

```   
CREATE TABLE Person (ID INTEGER PRIMARY KEY, Name VARCHAR(100), Age INT) AS NODE;
CREATE TABLE friends (StartDate date) AS EDGE;
```   

![le tabelle Person-amici](../../relational-databases/graphs/media/person-friends-tables.png "nodo /People/Person e amici edge tabelle")  
I nodi e archi vengono archiviati come tabelle  

### <a name="query-language-extensions"></a>Estensioni del linguaggio di query  
Nuovo `MATCH` clausola è stata introdotta per supportare criteri di ricerca e l'esplorazione multi hop tramite graph. Il `MATCH` funzione Usa sintassi grafica ASCII per criteri di ricerca. Esempio:  

```   
-- Find friends of John
SELECT Person2.Name 
FROM Person Person1, Friends, Person Person2
WHERE MATCH(Person1-(Friends)->Person2)
AND Person1.Name = 'John';
```   
 
### <a name="fully-integrated-in-includessnoversionincludesssnoversion-mdmd-engine"></a>Completamente integrato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore 
Estensioni per i grafi sono completamente integrate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore. Usiamo lo stesso motore di archiviazione, i metadati, il processore di query, e così via per archiviare ed eseguire query sui dati del grafico. Ciò consente agli utenti di eseguire query tra loro graph e i dati relazionali in una singola query. Gli utenti possono trarre vantaggio dalla combinazione di funzionalità di grafi con altri [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tecnologie come la tecnologia columnstore, a disponibilità elevata, R services, e così via. Database a grafo SQL supporta anche tutte le sicurezza e conformità di funzionalità disponibili con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
 
### <a name="tooling-and-ecosystem"></a>Gli strumenti e l'ecosistema  
Gli utenti possono beneficiare gli strumenti esistenti e l'ecosistema che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre. Strumenti come il backup e ripristino, importare ed esportare, funzionano perfettamente BCP impostazione predefinita. Altri strumenti o servizi, ad esempio SSIS, SSRS o Power BI funzionerà con tabelle, graph nel modo in cui funzionano con tabelle relazionali.
 
 ## <a name="next-steps"></a>Passaggi successivi  
Lettura di [Database a grafo SQL - architettura](./sql-graph-architecture.md)
   

