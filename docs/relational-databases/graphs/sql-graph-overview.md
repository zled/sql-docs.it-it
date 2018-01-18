---
title: Grafico di elaborazione con SQL Server e Database SQL di Azure | Documenti Microsoft
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: graphs
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, overview
ms.assetid: 
caps.latest.revision: "1"
author: shkale-msft
ms.author: shkale;barbkess
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 3a0828b1e50472ecec5f256c9ddfe13e8f0db8b7
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="graph-processing-with-sql-server-and-azure-sql-database"></a>Grafico di elaborazione con SQL Server e Database SQL di Azure
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]offre funzionalità di database di graph di modellare relazioni molti-a-molti. Le relazioni di grafico sono integrate [!INCLUDE[tsql-md](../../includes/tsql-md.md)] e ricevere i vantaggi dell'utilizzo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come sistema di gestione di database fondamentali.


## <a name="what-is-a-graph-database"></a>Che cos'è un database grafico?  
Un database di grafico è una raccolta di nodi (o vertici) e bordi (o relazioni). Un nodo rappresenta un'entità (ad esempio, una persona o organizzazione) e un bordo rappresenta una relazione tra i due nodi che si connette (ad esempio, simili o amici). I nodi e bordi possono avere proprietà associate. Ecco alcune funzionalità che rendono un database di graph univoco:  
-   Bordi o le relazioni sono entità di prima classe in un diagramma di Database e può avere attributi o proprietà associate. 
-   Un bordo singolo può connettersi in modo flessibile in più nodi in un diagramma di Database.
-   È possibile esprimere criteri di ricerca e query di navigazione di multi-hop facilmente.
-   È possibile esprimere facilmente query polimorfica e chiusura transitiva.

## <a name="when-to-use-a-graph-database"></a>Quando utilizzare un database di graph

Non è possibile ottenere un database di grafico, che non può essere ottenuta utilizzando un database relazionale. Un database grafico può tuttavia rendere più semplice esprimere determinato tipo di query. Inoltre, con le ottimizzazioni specifiche, alcune query può offrono prestazioni migliori. La decisione di scegliere uno di essi può essere basata su fattori seguenti:  
-   L'applicazione dispone di dati gerarchici. Il tipo di dati HierarchyID può essere utilizzato per implementare le gerarchie, ma presenta alcune limitazioni. Ad esempio, quindi non consente di archiviare più elementi padre di un nodo.
-   L'applicazione include relazioni molti-a-molti complesse; Quando l'applicazione continua a evolvere, vengono aggiunte nuove relazioni.
-   È necessario analizzare le relazioni e i dati interconnessi.

## <a name="graph-features-introduced-in-includesssqlv14includessssqlv14-mdmd"></a>Funzionalità di grafico introdotte in[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 
Si inizierà aggiungere estensioni graph a SQL Server, per semplificare l'esecuzione di query e l'archiviazione dei dati del grafico. Le funzionalità seguenti vengono introdotti nella prima versione. 


### <a name="create-graph-objects"></a>Creare gli oggetti del grafico
[!INCLUDE[tsql-md](../../includes/tsql-md.md)]estensioni consentirà agli utenti di creare tabelle di nodo o bordo. I nodi e bordi possono disporre di proprietà associate ad essi. Poiché, nodi e bordi vengono archiviati come tabelle, tutte le operazioni che sono supportate nelle tabelle relazionali sono supportate nella tabella di nodo o bordo. Esempio:  

```   
CREATE TABLE Person (ID INTEGER PRIMARY KEY, Name VARCHAR(100), Age INT) AS NODE;
CREATE TABLE friends (StartDate date) AS EDGE;
```   

![tabelle di amici persona](../../relational-databases/graphs/media/person-friends-tables.png "nodo persona e amici bordo tabelle")  
I nodi e bordi vengono archiviati come tabelle  

### <a name="query-language-extensions"></a>Estensioni del linguaggio di query  
Nuovo `MATCH` clausola è stato introdotto per supportare i criteri di ricerca e navigazione multi-hop tramite graph. Il `MATCH` funzione Usa sintassi grafica ASCII per criteri di ricerca. Esempio:  

```   
-- Find friends of John
SELECT Person2.Name 
FROM Person Person1, Friends, Person Person2
WHERE MATCH(Person1-(Friends)->Person2)
AND Person1.Name = 'John';
```   
 
### <a name="fully-integrated-in-includessnoversionincludesssnoversion-mdmd-engine"></a>Completamente integrato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore 
Le estensioni del grafico sono completamente integrati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore. Viene usato il stesso motore di archiviazione, i metadati, il processore di query, e così via per archiviare ed eseguire query su dati del grafico. Ciò consente agli utenti di eseguire una query tra loro grafico e dati relazionali in una singola query. Gli utenti possono trarre vantaggio dalla combinazione di funzionalità di grafico con altri [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le tecnologie come columnstore, a disponibilità elevata, R services, e così via. Database SQL di grafico supporta inoltre tutte la sicurezza e conformità le funzionalità disponibili con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
 
### <a name="tooling-and-ecosystem"></a>Strumenti e l'ecosistema  
Gli utenti possono beneficiare gli strumenti esistenti e l'ecosistema che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre. Strumenti come backup e ripristino, importare ed esportare, lavoro solo di BCP predefinita. Altri strumenti o i servizi come SSIS, SSRS o Power BI funziona con le tabelle di grafico, nel modo in cui funzionano con le tabelle relazionali.
 
 ## <a name="next-steps"></a>Passaggi successivi  
Lettura di [Database SQL di Graph - architettura](./sql-graph-architecture.md)
   

