---
title: Aggiornato - docs database relazionali | Documenti Microsoft
description: Visualizzare i frammenti di contenuto aggiornato per la documentazione modificato di recente in, per i database relazionali.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 05/23/2017
ms.author: genemi
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 3ab051a6fd00670139bb1089dcd3f4af76b9ecef
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Nuovi e recentemente aggiornato: docs database relazionali



Quasi ogni giorno Microsoft aggiorna alcuni articoli esistenti nel relativo [Docs.Microsoft.com](http://docs.microsoft.com/) sito Web di documentazione. In questo articolo consente di visualizzare estratti dagli articoli aggiornati di recente. Potrebbero anche essere elencati collegamenti a nuovi articoli.

In questo articolo viene generato da un programma che viene eseguito di nuovo periodicamente. In alcuni casi un estratto può apparire con formattazione perfetto, o come markdown nell'articolo di origine. Le immagini non vengono mai visualizzate qui.

Aggiornamenti recenti vengono indicati per il seguente intervallo di date e l'oggetto:



- *Intervallo degli aggiornamenti di date:* &nbsp; **2017-05-01** &nbsp; - a - &nbsp; **2017-05-23**
- *Area di interesse:* &nbsp; **database relazionali**.




&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione vengono estratti gli aggiornamenti raccolti dagli articoli di cui si sono verificati recentemente un aggiornamento di grandi dimensioni.

Gli estratti visualizzati qui vengono visualizzati separatamente dal relativo contesto semantica corretto Inoltre, talvolta un estratto è separato dalla sintassi markdown importante che la racchiude nell'articolo effettivo. Di conseguenza questi estratti sono solo a scopo generale. Gli estratti consentono solo di sapere se i tuoi interessi garantiscono la necessità di fare clic e visitare l'articolo effettivo.

Per queste e altre ragioni, non copiare da questi estratti di codice e non prendono come verità esatta qualsiasi testo estratto. In alternativa, visitare l'articolo effettivo.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-create-a-graph-database-and-run-some-pattern-matching-queries-using-t-sqlgraphssql-graph-samplemd"></a>1. &nbsp;[Creare un diagramma database ed eseguire alcuni criteri di ricerca di query utilizzando T-SQL](graphs/sql-graph-sample.md)

*Updated: 2017-05-04* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 68.  ms.author= "shkale".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ff467bf5fcf13592c796836def36e16e34f8cc31 99fcf0399006de16d0ac7cc9057564d307cb981b -->


```
INSERT INTO Person VALUES (1,'John');
INSERT INTO Person VALUES (2,'Mary');
INSERT INTO Person VALUES (3,'Alice');
INSERT INTO Person VALUES (4,'Jacob');
INSERT INTO Person VALUES (5,'Julie');

INSERT INTO Restaurant VALUES (1,'Taco Dell','Bellevue');
INSERT INTO Restaurant VALUES (2,'Ginger and Spice','Seattle');
INSERT INTO Restaurant VALUES (3,'Noodle Land', 'Redmond');

INSERT INTO City VALUES (1,'Bellevue','wa');
INSERT INTO City VALUES (2,'Seattle','wa');
INSERT INTO City VALUES (3,'Redmond','wa');

-- Insert into edge table. While inserting into an edge table, 
-- you need to provide the $node_id from $from_id and $to_id columns.
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 1), 
       (SELECT $node_id FROM Restaurant WHERE id = 1),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 2), 
      (SELECT $node_id FROM Restaurant WHERE id = 2),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 3), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 4), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 5), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);

INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 1),
      (SELECT $node_id FROM City WHERE id = 1));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 2),
      (SELECT $node_id FROM City WHERE id = 2));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 3),
      (SELECT $node_id FROM City WHERE id = 3));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 4),
      (SELECT $node_id FROM City WHERE id = 3));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 5),
      (SELECT $node_id FROM City WHERE id = 1));

INSERT INTO locatedIn VALUES ((SELECT $node_id FROM Restaurant WHERE id = 1),
      (SELECT $node_id FROM City WHERE id =1));
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sysfngetauditfile-transact-sqlsystem-functionssys-fn-get-audit-file-transact-sqlmd"></a>2. &nbsp; [Sys. fn_get_audit_file (Transact-SQL)](system-functions/sys-fn-get-audit-file-transact-sql.md)

*Updated: 2017-05-16* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1) | [Next](#TitleNum_3))

<!-- Source markdown line 145.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 046fa92ad1b7e6bb7a956493ca06cf72d45b5285 fbf55361da90663835d7e107fda697c358e0e061 -->



- **Database SQL di Azure**

  In questo esempio viene eseguita la lettura da un file denominato `ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel`.  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel',default,default);
  GO  
  ```  

  Il primo esempio legge tutti i registri dai server che iniziano con `Sh`.  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/Sh',default,default);
  GO  
  ```





&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-manage-retention-of-historical-data-in-system-versioned-temporal-tablestablesmanage-retention-of-historical-data-in-system-versioned-temporal-tablesmd"></a>3. &nbsp;[Gestire la conservazione dei dati cronologici nelle tabelle temporali con controllo delle versioni del sistema](tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)

*Updated: 2017-05-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_2))

<!-- Source markdown line 425.  ms.author= "carlrab".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ee69beb6a46913934d4a322f5d95343cc86f2ec4 94da98fec4ab16636a4581c16eb4456e2d1ff66b -->



**Approccio criteri di conservazione di cronologia temporale**

> **Nota:** approccio utilizzando i criteri di conservazione della cronologia temporale si applica a [! Includi [sqldbesa--... /.. /Includes/sqldbesa-MD.MD]) e SQL Server 2017 a partire dalla versione CTP 1.3.  

Periodo di memorizzazione cronologia temporale può essere configurato a livello di singola tabella, che consente agli utenti di creare degli oggetti eliminati flessibile criteri. L'applicazione di memorizzazione temporale è semplice: è necessario un solo parametro da impostare durante la modifica dello schema o di creazione tabella.

Dopo aver definito i criteri di conservazione, Database SQL di Azure avvia verifica regolarmente se sono presenti righe cronologiche idonei per la pulizia automatica dei dati. Identificazione delle righe corrispondenti e la rimozione dalla tabella di cronologia si verificano in modo trasparente, l'attività in background pianificata, eseguire dal sistema. Condizione di validità per le righe della tabella di cronologia viene controllato in base alla colonna che rappresenta di fine del periodo SYSTEM_TIME. Se il periodo di memorizzazione, ad esempio, è impostato su sei mesi, idonei per la pulizia delle righe della tabella soddisfano la condizione seguente:
```
ValidTo < DATEADD (MONTH, -6, SYSUTCDATETIME())
```
Nell'esempio precedente, si presuppone che la colonna ValidTo corrisponde alla fine del periodo SYSTEM_TIME.
**Come configurare i criteri di conservazione?**

Prima di configurare criteri di conservazione per una tabella temporale, controllare innanzitutto se il mantenimento di cronologia temporale è abilitato a livello di database:
```
SELECT is_temporal_history_retention_enabled, name
FROM sys.databases
```
Flag del database **is_temporal_history_retention_enabled** è impostata su ON per impostazione predefinita, ma gli utenti possono modificare con l'istruzione ALTER DATABASE. Si è impostato su OFF anche automaticamente dopo il punto di ripristino di tempo. Per attivare la pulizia di memorizzazione cronologia temporale per il database, eseguire l'istruzione seguente:
```
ALTER DATABASE <myDB>
SET TEMPORAL_HISTORY_RETENTION  ON
```
Criteri di conservazione viene configurato durante la creazione della tabella, specificando un valore per il parametro HISTORY_RETENTION_PERIOD:
```
CREATE TABLE dbo.WebsiteUserInfo
```





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Compact elenco degli articoli aggiornato di recente

Questo elenco compact vengono forniti collegamenti a tutti gli articoli aggiornati elencati nella sezione precedente.

1. [Creare un diagramma database ed eseguire alcuni criteri di ricerca di query utilizzando T-SQL](#TitleNum_1)
2. [Sys. fn_get_audit_file (Transact-SQL)](#TitleNum_2)
3. [Gestire la conservazione dei dati cronologici nelle tabelle temporali con controllo delle versioni di sistema](#TitleNum_3)


<a name="sisters2"/>

&nbsp;

## <a name="sister-articles"></a>Articoli sorella

In questa sezione sono elencati gli articoli molto simili per gli articoli aggiornati di recente in altre aree di interesse, nello stesso repository GitHub.


&nbsp;

[Microsoft /**sql-docs-pr** ](https://github.com/microsoftdocs/sql-docs-pr/) repository in GitHub.com:

- [Aggiornato di recente: **database relazionali e Microsoft SQL Server** documenti](/sql/relational-databases/relational-databases-new-updated-sql-docs-pr)
- [Aggiornato di recente: **Microsoft SQL Server** documenti](/sql/sql-server/sql-server-new-updated-sql-docs-pr)
- [Aggiornato di recente: **Transact-SQL in SQL Server** documenti](/sql/t-sql/t-sql-new-updated-sql-docs-pr)


&nbsp;

<!--
[Microsoft/**azure-docs**](https://github.com/microsoft/azure-docs/) repository on GitHub.com:

- [Sisters list for **azure-docs** repo](https://docs.microsoft.com/azure/sql-server-new-updated-azure-docs/#sisters2)
-->

&nbsp;



