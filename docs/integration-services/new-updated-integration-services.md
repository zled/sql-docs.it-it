---
title: 'Aggiornato: documentazione di Integration Services per SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato per modifiche recenti nella documentazione, per Integration Services per Microsoft SQL Server.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.workload: integration-services
ms.openlocfilehash: 9660fa7239c14c3adc963cc75ceb98de8316734c
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-integration-services-for-sql-server"></a>Articoli nuovi e aggiornati di recente: Integration Services per SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **28/09/2017** &nbsp; - &nbsp; **02/12/2017**
- *Area di interesse:* &nbsp; **Integration Services per SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Archiviare e recuperare file nelle condivisioni file in locale e in Azure con SSIS](lift-shift/ssis-azure-files-file-shares.md)
2. [Convalidare pacchetti SSIS distribuiti in Azure](lift-shift/ssis-azure-validate-packages.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Gestione connessione Hadoop](#TitleNum_1)
2. [Connettersi a origini dati locali e condivisioni file di Azure con autenticazione di Windows](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-hadoop-connection-managerconnection-managerhadoop-connection-managermd"></a>1. &nbsp; [Gestione connessione Hadoop](connection-manager/hadoop-connection-manager.md)

*Aggiornamento: 28/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 65.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2d68f4e884304f1a28045b42b680c15cc6a41ec5 fb2429466ea4d545682975d8dbea47451ce98ec7  (PR=4113  ,  Filename=hadoop-connection-manager.md  ,  Dirpath=docs\integration-services\connection-manager\  ,  MergeCommitSha40=28cccac53767db70763e5e705b8cc59a83c77317) -->



**Connettersi con l'autenticazione Kerberos**

Esistono due opzioni per configurare l'ambiente locale per poter usare l'autenticazione Kerberos con Gestione connessione Hadoop. È possibile scegliere l'opzione che meglio si adatta alle circostanze.
-   Opzione 1: [Aggiungere il computer SSIS all'area di autenticazione Kerberos--#kerberos-join-realm)
-   Opzione 2: [Abilitare il trust reciproco tra il dominio Windows e l'area di autenticazione Kerberos--#kerberos-mutual-trust)

**<a name="kerberos-join-realm"></a>Opzione 1: Aggiungere il computer SSIS all'area di autenticazione Kerberos**


**Requisiti:**


-   Il computer gateway deve fare parte dell'area di autenticazione Kerberos e non può fare parte di domini Windows.

**Modalità di configurazione:**


**Nel computer SSIS:**

1.  Eseguire l'utilità **Ksetup** per configurare l'area di autenticazione e il server KDC Kerberos.

    Il computer deve essere configurato come membro di un gruppo di lavoro, perché un'area di distribuzione Kerberos è diversa da un dominio Windows. Impostare l'area di autenticazione Kerberos e aggiungere un server KDC, come illustrato nell'esempio seguente. Sostituire *REALM.COM* con la propria rispettiva area di autenticazione, se necessario.

```
    C:> Ksetup /setdomain REALM.COM`
    C:> Ksetup /addkdc REALM.COM <your_kdc_server_address>
```

    Restart the computer after executing these two commands.

2.  Verificare la configurazione con il comando **Ksetup**. L'output sarà simile a quello contenuto nell'esempio seguente:

```
    C:> Ksetup
    default realm = REALM.COM (external)
    REALM.com:
        kdc = <your_kdc_server_address>
```

**<a name="kerberos-mutual-trust"></a>Opzione 2: Abilitare il trust reciproco tra il dominio Windows e l'area di autenticazione Kerberos**


**Requisiti:**

-   Il computer gateway deve fare parte di un dominio Windows.
-   È necessaria l'autorizzazione per aggiornare le impostazioni del controller di dominio.

**Modalità di configurazione:**


> [!NOTE]
> Sostituire REALM.COM e AD.COM nell'esercitazione seguente con la propria area di autenticazione e il proprio controller di dominio, se necessario.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-connect-to-on-premises-data-sources-and-azure-file-shares-with-windows-authenticationlift-shiftssis-azure-connect-with-windows-authmd"></a>2. &nbsp; [Connettersi a origini dati locali e condivisioni file di Azure con l'autenticazione di Windows](lift-shift/ssis-azure-connect-with-windows-auth.md)

*Aggiornamento: 27/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_1))

<!-- Source markdown line 66.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 673386fca53cb60b983e0cb3cd4b9e2ee1dee0de 65458b4dceb92d01184c5e9c6f68ec0e8f16ba08  (PR=4104  ,  Filename=ssis-azure-connect-with-windows-auth.md  ,  Dirpath=docs\integration-services\lift-shift\  ,  MergeCommitSha40=19e1c4067142d33e8485cb903a7a9beb7d894015) -->



**Connettersi a SQL Server locale**

Per verificare se è possibile connettersi a un'istanza di SQL Server locale, eseguire le operazioni seguenti:

1.  Per eseguire questo test, cercare un computer non appartenente al dominio.

2.  Nel computer non appartenente al dominio eseguire il comando riportato di seguito per avviare SQL Server Management Studio (SSMS) con le credenziali del dominio che si vuole usare:

```
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
```

3.  Controllare da SSMS se è possibile connettersi all'istanza di SQL Server locale che si prevede di usare.

**Connettersi a una condivisione file locale**

Per verificare se è possibile connettersi a una condivisione file locale, eseguire le operazioni seguenti:

1.  Per eseguire questo test, cercare un computer non appartenente al dominio.

2.  Nel computer non appartenente al dominio eseguire questo comando. Il comando apre una finestra del prompt dei comandi con le credenziali del dominio che si vuole usare, quindi verifica la connettività della condivisione file recuperando un elenco di directory.

```
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
```

3.  Verificare se viene restituito l'elenco di directory per la condivisione file locale che si vuole usare.

**Connettersi a una condivisione file in una VM di Azure**

Per connettersi a una condivisione file in una macchina virtuale di Azure, seguire questa procedura:

1.  Con SQL Server Management Studio (SSMS) o un altro strumento connettersi al database SQL che ospita il database del catalogo SSIS (SSISDB).

2.  Con SSISDB come database corrente, aprire una finestra di query.

3.  Eseguire la stored procedure `catalog.set_execution_credential` come descritto nelle opzioni seguenti:

```
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
```

**Connettersi a una condivisione file in File di Azure**

Per altre informazioni sui file di Azure, vedere [File di Azure](https://azure.microsoft.com/services/storage/files/).







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3+14): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (1+0): **Analysis Services for SQL (Analysis Services per SQL)** Docs](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (87+0): documentazione della **piattaforma di strumenti analitici per SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (5+4): documentazione della **connessione a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+1): documentazione del **motore di database di SQL Server**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (2+2): documentazione di **SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (10+9): documentazione di **Linux per SQL Server**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (2+4): documentazione dei **database relazionali per SQL Server**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (4+2): documentazione di **SQL Server Reporting Services**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0+1): documentazione degli **esempi per SQL Server**](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (21+0): documentazione di **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (5+1): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1): **SQL Server Data Tools (SSDT)** Docs](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1+0): documentazione di **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+1): **SQL Server Management Studio (SSMS)** Docs](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0 + 0): documentazione di **Data Migration Assistant (DMA) per SQL Server**](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


