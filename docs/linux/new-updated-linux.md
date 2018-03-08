---
title: 'Aggiornato: SQL Server in Linux docs | Documenti Microsoft'
description: Visualizzare i frammenti di contenuto aggiornato per la documentazione modificato di recente in, per Microsoft SQL Server in Linux.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: sql-linux,UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: 
ms.date: 02/03/2018
ms.openlocfilehash: 827399587a8147c59caf6bf31bf8b10f10c83211
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Nuovi e recentemente aggiornato: SQL Server in Linux documenti



Quasi ogni giorno Microsoft aggiorna alcuni articoli esistenti nel relativo [Docs.Microsoft.com](http://docs.microsoft.com/) sito Web di documentazione. In questo articolo consente di visualizzare estratti dagli articoli aggiornati di recente. Potrebbero anche essere elencati collegamenti a nuovi articoli.

In questo articolo viene generato da un programma che viene eseguito di nuovo periodicamente. In alcuni casi un estratto può apparire con formattazione perfetto, o come markdown nell'articolo di origine. Le immagini non vengono mai visualizzate qui.

Aggiornamenti recenti vengono indicati per il seguente intervallo di date e l'oggetto:



- *Intervallo degli aggiornamenti di date:* &nbsp; **2017-12-03** &nbsp; - a - &nbsp; **2018-02-03**
- *Area di interesse:* &nbsp; **Microsoft SQL Server in Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Configurare più subnet gruppi di disponibilità AlwaysOn e istanze del cluster di failover](sql-server-linux-configure-multiple-subnet.md)
2. [Creare e configurare un gruppo di disponibilità per SQL Server in Linux](sql-server-linux-create-availability-group.md)
3. [Distribuire un cluster Pacemaker per SQL Server in Linux](sql-server-linux-deploy-pacemaker-cluster.md)
4. [SQL Server in Linux domande frequenti (FAQ)](sql-server-linux-faq.md)
5. [Nozioni fondamentali sulla disponibilità di SQL Server per le distribuzioni di Linux](sql-server-linux-ha-basics.md)
6. [Configurazione di un contenitore di SQL Server in Kubernetes per la disponibilità elevata](tutorial-sql-server-containers-kubernetes.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui vengono visualizzati separatamente dal relativo contesto semantica corretto Inoltre, talvolta un estratto è separato dalla sintassi markdown importante che la racchiude nell'articolo effettivo. Di conseguenza questi estratti sono solo a scopo generale. Gli estratti consentono solo di sapere se i tuoi interessi garantiscono la necessità di fare clic e visitare l'articolo effettivo.

Per queste e altre ragioni, non copiare da questi estratti di codice e non prendono come verità esatta qualsiasi testo estratto. In alternativa, visitare l'articolo effettivo.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Compact elenco degli articoli aggiornato di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Gruppi di disponibilità in Linux Always On](#TitleNum_1)
2. [Estrarre, trasformare e caricare i dati in Linux con SSIS](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-always-on-availability-groups-on-linuxsql-server-linux-availability-group-overviewmd"></a>1. &nbsp;[Gruppi di disponibilità in Linux Always On](sql-server-linux-availability-group-overview.md)

*Ultimo aggiornamento: 2018-01-31* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Avanti](#TitleNum_2))

<!-- Source markdown line 85.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 85685bc8ad3528aa26ca3f2bba7b0112808ad6f9 51aff6e55104c8f775d2b4f4461e44f689a9ee6b  (PR=4768  ,  Filename=sql-server-linux-availability-group-overview.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=d4d880dd9c247d1e7fb7a728d5231bc9ac61c989) -->



Failover automatico di un gruppo di disponibilità è possibile quando vengono soddisfatte le condizioni seguenti:

-   Il database primario e la replica secondaria vengono impostate per lo spostamento di dati sincroni.
-   Il database secondario ha uno stato di sincronizzazione (non in sincronizzazione), ovvero che i due sono nello stesso punto dati.
-   Il tipo di cluster è impostato su esterno. Failover automatico non è possibile con un tipo di cluster None.
-   Il `sequence_number` della replica secondaria che diventerà il database primario è il numero di sequenza più alto: in altre parole, la replica secondaria `sequence_number` corrisponda a quella dalla replica primaria originale.

Se queste condizioni vengono soddisfatte e il server che ospita la replica primaria non riesce, il gruppo di disponibilità passerà proprietà a una replica sincrona. Il comportamento per le repliche sincrone (di cui è possibile tre totale: uno primario e due repliche secondarie) può essere controllata ulteriormente da `required_synchronized_secondaries_to_commit`. Funziona con estensivi su Windows e Linux, ma è configurato in modo completamente diverso. In Linux, il valore viene configurato automaticamente dal cluster della risorsa gruppo di disponibilità se stesso.

**Quorum e configurazione di replica di sola**


Anche nuovi in SQL Server 2017 a partire da CU1 è una sola configurazione replica. Poiché Pacemaker è diverso rispetto a un cluster WSFC, soprattutto quando si tratta di quorum e STONITH, richiedere una configurazione di due nodi non funzionerà quando si tratta di un gruppo di disponibilità. Per un'istanza FCI, i meccanismi di quorum forniti da Pacemaker possono costituire un problema, poiché l'arbitraggio di failover tutte le istanza cluster di failover si verifica a livello del cluster. Per un gruppo di disponibilità, arbitraggio in Linux viene eseguita in SQL Server, in cui vengono archiviati tutti i metadati. Si tratta in cui la replica solo configurazione entra in gioco.

Senza altri elementi, un terzo nodo e almeno una replica sincronizzata sarebbe necessari. Questo metodo non funziona per SQL Server Standard, poiché può avere solo due repliche che partecipano a un gruppo di disponibilità. La replica solo configurazione memorizza la configurazione del gruppo di disponibilità nel database master, come le altre repliche nella configurazione del gruppo di disponibilità. La sola configurazione di replica non dispone dei database utente che fanno parte del gruppo di disponibilità. I dati di configurazione viene inviati in modo sincrono dal database primario. Questi dati di configurazione viene quindi utilizzati durante i failover, sia automatico o manuale.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-extract-transform-and-load-data-on-linux-with-ssissql-server-linux-migrate-ssismd"></a>2. &nbsp;[Estrarre, trasformare e caricare i dati in Linux con SSIS](sql-server-linux-migrate-ssis.md)

*Ultimo aggiornamento: 2018-01-31* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_1))

<!-- Source markdown line 50.  ms.author= lle.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9bba002ae3955ebb8376c7c85b7ec1ac8c706073 1533a8e0bfe553e5404de79129119b3f93185ee9  (PR=4768  ,  Filename=sql-server-linux-migrate-ssis.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=d4d880dd9c247d1e7fb7a728d5231bc9ac61c989) -->



    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  Specificare il `/de[crypt]` opzione per immettere la password in modo interattivo, come illustrato nell'esempio seguente:

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de

    Enter decryption password:
    ```

3.  Specificare il `/de` opzione per fornire la password nella riga di comando, come illustrato nell'esempio seguente. Questo metodo è sconsigliato, perché la password di decrittografia con il comando Archivia nella cronologia dei comandi.

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test

    Warning: Using /De[crypt] <password> may store decryption password in command history.

    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

**Progettazione di pacchetti**


**Connettersi a origini dati ODBC**. Con SSIS in aggiornamento di Linux CTP 2.1 e versioni successive, i pacchetti SSIS possono utilizzare connessioni di ODBC in Linux. Questa funzionalità è stata testata con SQL Server e i driver ODBC di MySQL, ma anche dovrebbe funzionare con qualsiasi driver ODBC Unicode che osserva la specifica ODBC. In fase di progettazione, è possibile fornire un DSN o una stringa di connessione per connettersi ai dati ODBC; è inoltre possibile utilizzare l'autenticazione di Windows. Per altre informazioni, vedere il [post del blog annuncia il supporto ODBC in Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).







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


