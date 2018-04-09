---
title: Sistema di piattaforma Analitica per i documenti del Server SQL - aggiornato | Documenti Microsoft
description: Visualizzare i frammenti di contenuto aggiornato per modificati di recente nella documentazione, sistema di piattaforma Analitica per Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: aps-pdw
ms.date: 02/03/2018
ms.openlocfilehash: f3a8a14c0c01ff99c8ad613bbc9f5e1e01955e7e
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2018
---
# <a name="new-and-recently-updated-analytics-platform-system-for-sql-server"></a>Nuovi e aggiornati: Analitica piattaforma sistema per SQL Server



Quasi ogni giorno Microsoft aggiorna alcuni articoli esistenti nel relativo [Docs.Microsoft.com](http://docs.microsoft.com/) sito Web di documentazione. In questo articolo consente di visualizzare estratti dagli articoli aggiornati di recente. Potrebbero anche essere elencati collegamenti a nuovi articoli.

In questo articolo viene generato da un programma che viene eseguito di nuovo periodicamente. In alcuni casi un estratto può apparire con formattazione perfetto, o come markdown nell'articolo di origine. Le immagini non vengono mai visualizzate qui.

Aggiornamenti recenti vengono indicati per il seguente intervallo di date e l'oggetto:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/12/2017** &nbsp; - &nbsp; **03/02/2018**
- *Area di interesse:* &nbsp; **Analitica Platform System per SQL Server**.




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

1. [Configurazione della connettività di PolyBase per i dati esterni](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-polybase-connectivity-to-external-dataconfigure-polybase-connectivity-to-external-datamd"></a>1. &nbsp; [Configurazione della connettività di PolyBase per i dati esterni](configure-polybase-connectivity-to-external-data.md)

*Aggiornamento: 29/01/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 132.  ms.author= "barbkess".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 947f789480da66b9f636f39b30caec6be60d8c4d d4d4d45fbbb8e10ed6f26fe12f9a25d2e8e4f068  (PR=4741  ,  Filename=configure-polybase-connectivity-to-external-data.md  ,  Dirpath=docs\analytics-platform-system\  ,  MergeCommitSha40=0a44ce9993ebf61f86e409255a1d58d47993951a) -->



**Configurazione di Kerberos**

Si noti che quando PolyBase esegue l'autenticazione a un cluster protetto con Kerberos, l'impostazione hadoop.rpc.protection deve essere impostata per l'autenticazione. La comunicazione dei dati tra i nodi Hadoop rimane non crittografata.

 Per connettersi a un cluster Hadoop protetto con Kerberos [utilizzando KDC MIT]:


1.  Trovare la directory di configurazione Hadoop nel percorso di installazione nel nodo di controllo:

    ```
    C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf
    ```

2.  Trovare il valore di configurazione lato Hadoop delle chiavi di configurazione elencate nella tabella. Nel computer Hadoop trovare i file nella directory di configurazione Hadoop.

3.  Copiare i valori di configurazione nella proprietà del valore nei file corrispondenti sul nodo del controllo.

    |**#**|**File di configurazione**|**Chiave di configurazione**|**Azione**|
    |------------|----------------|---------------------|----------|
    |1|core-site.xml|polybase.kerberos.kdchost|Specificare il nome host KDC. Ad esempio: kerberos.area-di-autenticazione.com.|
    |2|core-site.xml|polybase.kerberos.realm|Specificare l'area di autenticazione Kerberos. Ad esempio: AREA-DI-AUTENTICAZIONE.COM|
    |3|core-site.xml|hadoop.security.authentication|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: KERBEROS<br></br>**Nota sulla sicurezza:** è necessario scrivere KERBEROS in maiuscolo. Se si usano lettere minuscole, potrebbe non essere disponibile.|
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: hdfs/_HOST@YOUR-REALM.COM|
    |5|mapred-site.xml|mapreduce.jobhistory.principal|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: mapred/_HOST@YOUR-REALM.COM|
    |6|mapred-site.xml|mapreduce.jobhistory.address|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: 10.193.26.174:10020|
    |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Esempio: yarn/_HOST@YOUR-REALM.COM|







## <a name="similar-articles-about-new-or-updated-articles"></a>Articoli simili su articoli nuovi o aggiornati

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Aree di interesse *con* articoli nuovi o aggiornati di recente


- [Nuovo + aggiornato (1+3):&nbsp; documentazione di **Advanced Analytics per SQL** ](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione della **piattaforma di strumenti analitici per SQL** ](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione della **connessione a SQL Server** ](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione del **motore di database di SQL Server** ](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (12+1): documentazione di **SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (6+2):&nbsp; documentazione di **Linux per SQL Server** ](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (15+0):**documentazione di**PowerShell per SQL Server](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (2+9):&nbsp; documentazione dei **database relazionali per SQL Server** ](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (1+0):&nbsp; documentazione di **SQL Server Reporting Services** ](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di **SQL Operations Studio** ](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di **Microsoft SQL Server** ](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione di **SQL Server Data Tools (SSDT)** ](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1+2):&nbsp; documentazione di **SQL Server Management Studio (SSMS)** ](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di **Transact-SQL** ](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Aree di interesse *senza* articoli nuovi o aggiornati di recente


- [Nuovo + aggiornato (0 + 0): documentazione di **Data Migration Assistant (DMA) per SQL Server**](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0 + 0): **oggetti ADO (ActiveX Data) per SQL** documenti](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): documentazione di **Analysis Services per SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0 + 0): **Data Quality Services per SQL** documenti](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0 + 0): **estensioni DMX (Data Mining) per SQL** documenti](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0 + 0): **MDX (Multidimensional Expressions) per SQL** documenti](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0 + 0): **ODBC (Open Database Connectivity) per SQL** documenti](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0 + 0): **esempi per SQL** documenti](../samples/new-updated-samples.md)
- [Nuovo + aggiornato (0 + 0): **SQL Server Migration Assistant (SSMA)** documenti](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0 + 0): **XQuery per SQL** documenti](../xquery/new-updated-xquery.md)


