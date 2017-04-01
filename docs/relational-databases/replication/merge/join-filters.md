---
title: "Filtri join | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filtri [replica di SQL Server], join"
  - "pubblicazioni [replica di SQL Server], filtri di join"
  - "filtri di join per replica di tipo merge [replica di SQL Server]"
  - "filtri di join"
ms.assetid: dd78fd8f-56e3-4582-9abd-6bc25c91e075
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Filtri join
  Un filtro di join consente di filtrare una tabella in base al tipo di filtro applicato a una tabella correlata nella pubblicazione Viene in genere filtrata una tabella padre mediante un filtro con parametri, quindi vengono definiti uno o più filtri di join così come si definisce un join tra tabelle. I filtri di join estendono il filtro con parametri affinché i dati nelle tabelle correlate vengano replicati solo se corrispondenti alla clausola di filtro di join.  
  
 I filtri join seguono in genere le relazioni tra chiavi primarie e chiavi esterne definite per le tabelle alle quali vengono applicati, ma non sono necessariamente limitati a tali relazioni. Il filtro di join può essere basato su qualsiasi logica di confronto tra i dati correlati di due tabelle.  
  
 Si considerino le tabelle seguenti del database di esempio [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)], correlate tramite relazioni di chiave primaria/chiave esterna:  
  
-   **HumanResources.Employee**  
  
-   **Sales.SalesOrderHeader**  
  
-   **Sales.SalesOrderDetail**  
  
 Queste tabelle potrebbero essere utilizzate in un'applicazione per supportare una forza vendita mobile, ma devono essere filtrate affinché ogni venditore nel **HumanResources. Employee** tabella riceve solo i dati relativi agli ordini dei clienti.  
  
 Il primo passaggio consiste nel definire un filtro con parametri nella tabella padre, che in questo esempio è il **HumanResources. Employee** tabella. Questa tabella è inclusa la colonna **LoginID**, che contiene l'account di accesso per ogni dipendente nel formato *dominio\account di accesso*. Per filtrare questa tabella affinché ogni dipendente riceva soltanto i dati pertinenti, specificare la clausola di filtro con parametri:  
  
```  
LoginID = SUSER_SNAME()  
```  
  
 Questo filtro assicura che la sottoscrizione di ogni dipendente contenga soltanto i dati di **HumanResources. Employee** tabella rilevanti per tale dipendente (che in questo caso è una singola riga). Per altre informazioni, vedere [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 Il passaggio successivo consiste nell'estendere questo filtro a ogni tabella correlata, utilizzando una sintassi simile a quella utilizzata per specificare un join tra due tabelle. La prima clausola di filtro di join è:  
  
```  
Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
```  
  
 Ciò garantisce che la sottoscrizione conterrà soltanto i dati degli ordini rilevanti per ogni venditore. La seconda clausola di filtro di join è:  
  
```  
SalesOrderHeader.SalesOrderID = SalesOrderDetail.SalesOrderID  
```  
  
 Ciò garantisce che la sottoscrizione conterrà soltanto i dati di dettaglio correlati ai dati degli ordini per ogni venditore. In questo esempio viene illustrato il join di una singola tabella in ogni fase. È inoltre possibile unire in join più tabelle in ogni fase.  
  
 È possibile aggiungere filtri di join uno alla volta tramite la creazione guidata nuova pubblicazione e la **Proprietà pubblicazione** la finestra di dialogo o possono essere aggiunti a livello di codice. Possono inoltre essere generati automaticamente tramite la Creazione guidata nuova pubblicazione: specificando un filtro di riga per una tabella verranno applicati filtri di join a tutte le tabelle correlate. Per ulteriori informazioni, vedere [definizione e modifica di un Join filtro tra articoli di Merge](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md), [Genera automaticamente un Set di aggiungere filtri tra articoli di Merge & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/publish/automatically generate join filters between merge articles.md), e [definire un articolo](../../../relational-databases/replication/publish/define-an-article.md).  
  
## Ottimizzazione delle prestazioni dei filtri di join  
 È possibile ottimizzare le prestazioni dei filtri di join attenendosi alle linee guida seguenti:  
  
-   Limitare il numero massimo di tabelle nella gerarchia dei filtri di join.  
  
     I filtri di join possono includere un numero illimitato di tabelle, ma filtri con un numero elevato di tabelle possono influire significativamente sulle prestazioni durante l'elaborazione di processi di merge. Se si generano filtri di join di cinque o più tabelle, considerare altre soluzioni: non filtrare tabelle piccole, non soggette a modifica o tabelle che fungono principalmente da tabelle di ricerca. Utilizzare i filtri di join solo tra tabelle che devono essere partizionate tra diverse sottoscrizioni.  
  
-   Impostare il **chiave univoca di join** opzione **True** dove appropriato.  
  
     Se la colonna unita in join nella tabella padre è univoca, per il processo di merge sono disponibili speciali procedure di ottimizzazione delle prestazioni. Se la condizione di join è basata su una colonna univoca, impostare il **joinuniquekey** opzione per il filtro di join. Per informazioni sull'impostazione di questa proprietà, vedere le procedure elencate nella sezione precedente.  
  
-   Verificare che le colonne a cui viene fatto riferimento nei filtri di join siano indicizzate.  
  
     Se le colonne a cui viene fatto riferimento nel filtro sono indicizzate, i filtri possono essere elaborati dalla replica in modo più efficiente.  
  
-   Non creare filtri di riga che svolgono la funzione di filtri di join.  
  
     È possibile creare filtri di riga che svolgono la funzione di filtri di join utilizzando una sottoquery in una clausola WHERE, ad esempio:  
  
    ```  
    WHERE Customer.SalesPersonID IN (SELECT EmployeeID FROM Employee WHERE LoginID = SUSER_SNAME())   
    ```  
  
     È consigliabile esprimere tale logica in un filtro di join, anziché in una sottoquery. Se l'applicazione richiede l'utilizzo di una sottoquery in un filtro di riga, verificare che la sottoquery faccia riferimento soltanto a dati di ricerca non soggetti a modifiche.  
  
## Vedere anche  
 [Filtro dei dati pubblicati per la replica di tipo merge](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)   
 [Filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
  