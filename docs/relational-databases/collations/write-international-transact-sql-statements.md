---
title: "Scrittura di istruzioni Transact-SQL internazionali | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "scrittura di istruzioni internazionali"
  - "Transact-SQL - considerazioni sulle funzionalità internazionali"
  - "considerazioni sulle funzionalità internazionali [SQL Server], Transact-SQL"
  - "considerazioni sulle funzionalità internazionali del motore di database [SQL Server], Transact-SQL"
  - "istruzioni [SQL Server], funzionalità internazionali"
  - "considerazioni sulle funzionalità di database internazionali [SQL Server], Transact-SQL"
  - "date [SQL Server], considerazioni sulle funzionalità internazionali"
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Scrittura di istruzioni Transact-SQL internazionali
  Le linee guida seguenti consentono di aumentare il grado di portabilità tra lingue diverse, nonché il supporto di più lingue, per i database e le applicazioni di database che utilizzano istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Sostituire tutte le occorrenze dei tipi di dati **char**, **varchar** e **text** con **nchar**, **nvarchar** e **nvarchar(max)**. In questo modo non si verificano problemi a livello di conversione della tabella codici. Per altre informazioni, vedere [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
-   Quando si eseguono confronti e operazioni con mesi o giorni della settimana, utilizzare le parti numeriche della data anziché le stringhe di nomi. I nomi dei mesi e dei giorni della settimana restituiti variano a seconda dell'impostazione della lingua. Ad esempio, DATENAME (MONTH,GETDATE()) restituisce May quando la lingua è impostata sull'inglese (Stati Uniti) Mai se è impostato il tedesco e mai se è impostato il francese. Specificare pertanto una funzione quale DATEPART che utilizza il numero anziché il nome del mese. Utilizzare i nomi DATEPART quando si compilano i set di risultati da visualizzare all'utente, in quanto le stringhe di nomi sono più significative delle parti numeriche. Non creare tuttavia il codice di logica che dipende dai nomi visualizzati di una lingua specifica.  
  
-   Quando si specificano le date nei confronti o nell'input di istruzioni INSERT e UPDATE, utilizzare costanti che vengono interpretate nello stesso modo indipendentemente dall'impostazione della lingua:  
  
    -   Le applicazioni ADO, OLE DB e ODBC devono utilizzare le clausole di escape seguenti relative a timestamp, data e ora:  
  
         **{ ts'**aaaa**-***mm***-***gg**hh***:***mm***:***ss*[**.***fff*] **'}** ad esempio: **{ ts'**1998**-**09**-**24 10**:**02**:**20**' }**  
  
         **{ d'** *aaaa* **-** *mm* **-** *gg* **'}** ad esempio: **{ d'**1998**-**09**-**24**'}**  
  
         **{ t'** *hh* **:** *mm* **:** *ss* **'}** ad esempio: **{ t'**10:02:20**'}**  
  
    -   Nelle applicazioni che utilizzano altre API, oppure script, stored procedure e trigger di [!INCLUDE[tsql](../../includes/tsql-md.md)], è necessario utilizzare le stringhe numeriche non separate, Ad esempio, *aaaammgg* come 19980924.  
  
    -   Nelle applicazioni che usano altre API oppure script, stored procedure e trigger di [!INCLUDE[tsql](../../includes/tsql-md.md)] è anche possibile usare l'istruzione CONVERT con un parametro di stile esplicito per tutte le conversioni tra i tipi di dati **time**, **date**, **smalldate**, **datetime**, **datetime2** e **datetimeoffset** e i tipi di dati stringa di caratteri. L'istruzione seguente viene interpretata nello stesso modo indipendentemente dalle impostazioni di connessione della lingua o del formato della data:  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         Per altre informazioni, vedere [CAST and CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
  