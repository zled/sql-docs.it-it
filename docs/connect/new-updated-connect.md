---
title: Aggiornato - connettersi a documenti di SQL Server | Documenti Microsoft
description: Visualizzare i frammenti di contenuto aggiornato per la documentazione modificato di recente in, per connettersi a Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: connect
ms.date: 02/03/2018
ms.openlocfilehash: cc4eb05dc4dcd74623c8ce7dfa7b7842449d79b6
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-connect-to-sql-server"></a>Nuovi e aggiornati: connettersi a SQL Server



Quasi ogni giorno Microsoft aggiorna alcuni articoli esistenti nel relativo [Docs.Microsoft.com](http://docs.microsoft.com/) sito Web di documentazione. In questo articolo consente di visualizzare estratti dagli articoli aggiornati di recente. Potrebbero anche essere elencati collegamenti a nuovi articoli.

In questo articolo viene generato da un programma che viene eseguito di nuovo periodicamente. In alcuni casi un estratto può apparire con formattazione perfetto, o come markdown nell'articolo di origine. Le immagini non vengono mai visualizzate qui.

Aggiornamenti recenti vengono indicati per il seguente intervallo di date e l'oggetto:



- *Intervallo degli aggiornamenti di date:* &nbsp; **2017-12-03** &nbsp; - a - &nbsp; **2018-02-03**
- *Area di interesse:* &nbsp; **Connetti al Server SQL**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


***Nessun nuovo articolo da visualizzare.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui vengono visualizzati separatamente dal relativo contesto semantica corretto Inoltre, talvolta un estratto è separato dalla sintassi markdown importante che la racchiude nell'articolo effettivo. Di conseguenza questi estratti sono solo a scopo generale. Gli estratti consentono solo di sapere se i tuoi interessi garantiscono la necessità di fare clic e visitare l'articolo effettivo.

Per queste e altre ragioni, non copiare da questi estratti di codice e non prendono come verità esatta qualsiasi testo estratto. In alternativa, visitare l'articolo effettivo.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Compact elenco degli articoli aggiornato di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Utilizzo di Always Encrypted con il Driver ODBC per SQL Server](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-using-always-encrypted-with-the-odbc-driver-for-sql-serverodbcusing-always-encrypted-with-the-odbc-drivermd"></a>1. &nbsp;[Uso di Always Encrypted con il Driver ODBC per SQL Server](odbc/using-always-encrypted-with-the-odbc-driver.md)

*Ultimo aggiornamento: 2018-01-22* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 524.  ms.author= "v-chojas".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a52abae2a8f27c3b5bc411ef758610116a608f9f 352368eb269b98ab5ca3a9791fae2e70bf26277a  (PR=4686  ,  Filename=using-always-encrypted-with-the-odbc-driver.md  ,  Dirpath=docs\connect\odbc\  ,  MergeCommitSha40=82c9868b5bf95e5b0c68137ba434ddd37fc61072) -->



**Recuperare i dati in parti con SQLGetData**

Prima crittografato 17 Driver ODBC per SQL Server, caratteri e colonne binarie non possono essere recuperate in parti con SQLGetData. Solo una chiamata di SQLGetData può essere effettuata, con un buffer di lunghezza sufficiente per contenere dati dell'intera colonna.

**Inviare i dati in parti con SQLPutData**

Impossibile inviare i dati per l'inserimento o di confronto nelle parti con SQLPutData. Solo una chiamata a SQLPutData può essere effettuata, con un buffer che contiene tutti i dati. Per l'inserimento di dati long in colonne crittografate, utilizzare l'API della copia Bulk, descritto nella sezione successiva, con un file di dati di input.

**Smallmoney e money crittografati**

Crittografati **money** o **smallmoney** colonne non possono essere assegnate dai parametri, poiché non è specifico del tipo di dati ODBC che esegue il mapping di questi tipi, gli errori di conflitto di tipo di operando.

**Copia bulk di colonne crittografate**


Utilizzare il [funzioni di copia Bulk SQL](odbc/../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md) e **bcp** utilità è supportata con crittografia sempre attiva perché 17 Driver ODBC per SQL Server. Testo normale (crittografato in inserimento e recupero decrittografato nel) sia testo crittografato (trasferiti verbatim) possono essere inseriti e recuperati utilizzando la copia di massa (bcp_ *) le API e **bcp** utilità.

- Per recuperare testo crittografato in formato varbinary (max) (ad esempio per il caricamento bulk in un database diverso), connettersi senza il `ColumnEncryption` opzione (o impostarlo su `Disabled`) ed eseguire un'operazione BCP OUT.

- Per inserire e recuperare in testo normale e consente di eseguire in modo trasparente la crittografia e decrittografia come impostazione obbligatoria, il driver `ColumnEncryption` a `Enabled` è sufficiente. In caso contrario, la funzionalità dell'API BCP è invariata.

- Per inserire testo crittografato in formato varbinary (max) (ad esempio come recuperato sopra), impostare il `BCPMODIFYENCRYPTED` opzione su TRUE e di eseguire un'operazione BCP IN. Affinché i dati risultanti da decryptable, verificare che la destinazione CEK della colonna è uguale a quello da cui il testo crittografato è stato ottenuto in origine.







## <a name="similar-articles-about-new-or-updated-articles"></a>Articoli simili su nuovi o aggiornati gli articoli

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Aree di interesse che *si* sono nuovi o recentemente aggiornati gli articoli


- [Nuovo + aggiornato (1 + 3):&nbsp; **Analitica avanzate per SQL** documenti](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (0 + 1):&nbsp; **Analitica Platform System per SQL** documenti](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (0 + 1):&nbsp; **Connect to SQL** documenti](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0 + 1):&nbsp; **motore di Database per SQL** documenti](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (12 + 1): **Integration Services per SQL** documenti](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (6 + 2):&nbsp; **Linux per SQL** documenti](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (15 + 0): **PowerShell per SQL** documenti](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (2 + 9):&nbsp; **database relazionali di SQL** documenti](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (1 + 0):&nbsp; **Reporting Services per SQL** documenti](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (1 + 1):&nbsp; **operazioni SQL Studio** documenti](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (1 + 1):&nbsp; **Microsoft SQL Server** documenti](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0 + 1):&nbsp; **SQL Server Data Tools (SSDT)** documenti](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1 + 2):&nbsp; **SQL Server Management Studio (SSMS)** documenti](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0 + 2):&nbsp; **Transact-SQL** documenti](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Oggetto aree che *non* sono nuovi o recentemente aggiornati gli articoli


- [Nuovo + aggiornato (0 + 0): documentazione di **Data Migration Assistant (DMA) per SQL Server**](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0 + 0): **oggetti ADO (ActiveX Data) per SQL** documenti](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): documentazione di **Analysis Services per SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0 + 0): **Data Quality Services per SQL** documenti](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0 + 0): **estensioni DMX (Data Mining) per SQL** documenti](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0 + 0): **MDX (Multidimensional Expressions) per SQL** documenti](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0 + 0): **ODBC (Open Database Connectivity) per SQL** documenti](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0 + 0): **esempi per SQL** documenti](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0 + 0): **SQL Server Migration Assistant (SSMA)** documenti](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0 + 0): **XQuery per SQL** documenti](../xquery/new-updated-xquery.md)


