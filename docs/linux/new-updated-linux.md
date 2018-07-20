---
title: 'Articolo aggiornato: SQL Server in Linux docs | Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato per modifiche recenti nella documentazione, per Microsoft SQL Server in Linux.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: conceptual
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.date: 04/28/2018
ms.openlocfilehash: f7f1e437e0b9d4c2940293280ee2c5529da85e6c
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082483"
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Nuovi e aggiornati di recente: SQL Server in Linux docs



Quasi ogni giorno Microsoft aggiorna alcuni articoli esistenti nel relativo sito Web di documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). In questo articolo sono visualizzati estratti degli articoli aggiornati di recente. Potrebbero anche essere elencati collegamenti a nuovi articoli.

Questo articolo viene generato da un programma eseguito periodicamente. In alcuni casi un estratto può apparire con una formattazione imperfetta, o anche come markdown origine dell'articolo. Le immagini non vengono mai visualizzate qui.

Sono indicati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/02/2018** &nbsp; - &nbsp; **28/04/2018**
- *Area di interesse:* &nbsp; **Microsoft SQL Server in Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Autenticazione di Active Directory per SQL Server in Linux](sql-server-linux-active-directory-auth-overview.md)
2. [Configura SQL Server gruppo di disponibilità AlwaysOn in Windows e Linux (multipiattaforma)](sql-server-linux-availability-group-cross-platform.md)
3. [Operare sempre i gruppi di disponibilità in Linux](sql-server-linux-availability-group-operate-ha.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui vengono visualizzati separatamente dal relativo contesto di semantica corretto. Inoltre, talvolta un estratto è separato dalla sintassi markdown importante che lo racchiude nell'articolo effettivo. Di conseguenza questi estratti sono solo a scopo generale. Gli estratti consentono solo di sapere se i tuoi interessi garantiscono la necessità di fare clic e visitare l'articolo effettivo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità esatta qualsiasi testo in essi contenuto. Piuttosto, visitare l'articolo effettivo.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Configurare i repository per l'installazione e aggiornamento di SQL Server in Linux](#TitleNum_1)
2. [Configurare SQL Server in Linux con lo strumento mssql-conf](#TitleNum_2)
3. [Note sulla versione di SQL Server 2017 in Linux](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-repositories-for-installing-and-upgrading-sql-server-on-linuxsql-server-linux-change-repomd"></a>1. &nbsp; [Configurare i repository per l'installazione e aggiornamento di SQL Server in Linux](sql-server-linux-change-repo.md)

*Aggiornamento: 25/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 72.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5ccaa0fcb8895f25c162e4e0494ad4872773de3 29a959be6ee7d58fe0c53e8f91bdd282fb2e6d29  (PR=5676  ,  Filename=sql-server-linux-change-repo.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- Stampare il contenuto del file.

```
   sudo cat /etc/yum.repos.d/mssql-server.repo
```

- Il **nome** proprietà è il repository configurato. È possibile identificarlo con la tabella nella sezione [repository] di questo articolo.

**Rimuovere i vecchi repository (RHEL)**

Se necessario, rimuovere il repository precedente con il comando seguente.

```
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Questo comando dà per scontato che il file identificato nella sezione precedente è stato denominato **mssql-server.repo**.

**Configurare il nuovo repository (RHEL)**

Configurare il nuovo repository da usare per gli aggiornamenti e installazioni di SQL Server. Usare uno dei comandi seguenti per configurare il repository scelto dall'utente.

| Archivio | Comando |
|---|---|
| **CU** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

**<a id="sles"></a> Configurare i repository SLES**

Usare la procedura seguente per configurare i repository in SLES.

**Verificare la presenza di repository configurato in precedenza (SLES)**

Prima di tutto verificare se è già stato registrato un repository di SQL Server.

- Uso **zypper info** per ottenere informazioni su tutti i repository configurata in precedenza.

```
   sudo zypper info mssql-server
```

- Il **Repository** proprietà è il repository configurato. È possibile identificarlo con la tabella nella sezione [repository] di questo articolo.

**Rimuovere i vecchi repository (SLES)**

Se necessario, rimuovere il repository precedente. Usare uno dei comandi seguenti in base al tipo di repository configurato in precedenza.

| Archivio | Comando da rimuovere |
|---|---|
| **Anteprima** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-sql-server-on-linux-with-the-mssql-conf-toolsql-server-linux-configure-mssql-confmd"></a>2. &nbsp; [Configurare SQL Server in Linux con lo strumento mssql-conf](sql-server-linux-configure-mssql-conf.md)

*Ultimo aggiornamento: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_1) | [successivo](#TitleNum_3))

<!-- Source markdown line 151.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3664c4d64ea4840dcbc718461ed04403cc486f30 89f708af45ce262057e967e9047f1328e19248ba  (PR=5676  ,  Filename=sql-server-linux-configure-mssql-conf.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->




**<a id="masterdatabasedir"></a> Modificare il percorso di directory file di database master predefinito**


Il **filelocation.masterdatafile** e **filelocation.masterlogfile** impostazione modifiche della posizione in cui il motore di SQL Server cerca i file di database master. Per impostazione predefinita, questo percorso è /var/opt/mssql/data.

Per modificare queste impostazioni, procedere come segue:

- Creare la directory di destinazione per i nuovi file di log di errore. L'esempio seguente crea una nuova **/tmp/masterdatabasedir** directory:

```
   sudo mkdir /tmp/masterdatabasedir
```

- Modificare il proprietario e il gruppo della directory in cui il **mssql** utente:

```
   sudo chown mssql /tmp/masterdatabasedir
   sudo chgrp mssql /tmp/masterdatabasedir
```

- Usare mssql-conf per passare alla directory di database master predefinito per i file di log e dati master con il **impostare** comando:

```
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /tmp/masterdatabasedir/master.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterlogfile /tmp/masterdatabasedir/mastlog.ldf
```

- Arrestare il servizio SQL Server:

```
   sudo systemctl stop mssql-server
```

- Spostare il master. mdf e masterlog.ldf:

```
   sudo mv /var/opt/mssql/data/master.mdf /tmp/masterdatabasedir/master.mdf
   sudo mv /var/opt/mssql/data/mastlog.ldf /tmp/masterdatabasedir/mastlog.ldf
```

- Avviare il servizio SQL Server:

```
   sudo systemctl start mssql-server
```

> [!NOTE]
> Se SQL Server non è possibile trovare i file mdf e Mastlog nella directory specificata, verrà creata automaticamente una copia basata su modelli di database di sistema nella directory specificata e SQL Server verrà avviato correttamente. Tuttavia, metadati, ad esempio i database utente, account di accesso server, i certificati del server, le chiavi di crittografia, processi di SQL agent o vecchia password di account di accesso SA non essere aggiornato nel nuovo database master. È necessario arrestare SQL Server e spostare il vecchio master. mdf e Mastlog. ldf nel nuovo percorso specificato e l'avvio di SQL Server per continuare a usare i metadati esistenti.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-release-notes-for-sql-server-2017-on-linuxsql-server-linux-release-notesmd"></a>3. &nbsp; [Note sulla versione di SQL Server 2017 in Linux](sql-server-linux-release-notes.md)

*Aggiornamento: 25/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_2))

<!-- Source markdown line 64.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 367d112a9427bbdd18e0e52cc82264dd169c91ae 63a67be08fa39ece778cf9ca0b9746dd28694574  (PR=5676  ,  Filename=sql-server-linux-release-notes.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- [Abilitare SQL Server Agent]

**<a id="CU6"></a> CU6 (aprile 2018)**


Si tratta della versione di aggiornamento cumulativo 6 (CU6) di SQL Server 2017. La versione del motore di SQL Server per questa versione è 14.0.3025.34. Per informazioni sulle correzioni e miglioramenti in questa versione, vedere [ https://support.microsoft.com/help/4101464 ](https://support.microsoft.com/help/4101464).

**Dettagli del pacchetto**


Per le installazioni manuali o offline del pacchetto, è possibile scaricare i pacchetti Debian e RPM con le informazioni nella tabella seguente:

| Pacchetto | Versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto di Red Hat RPM | 14.0.3025.34-3 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Pacchetto RPM ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[Pacchetto SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) |
| Pacchetto RPM SLES | 14.0.3025.34-3 | [pacchetto RPM motore MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Pacchetto RPM ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) |
| Pacchetto Debian Ubuntu 16.04 | 14.0.3025.34-3 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[Pacchetto Debian ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[Pacchetto SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |







## <a name="similar-articles-about-new-or-updated-articles"></a>Articoli simili su articoli nuovi o aggiornati

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Aree di interesse *con* articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (11+6):&nbsp; documentazione di &nbsp;**Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (18+0): &nbsp; documentazione di &nbsp;**Analysis Services per SQL Server**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (218+14):**documentazione della**connessione a SQL Server](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (14+0):&nbsp; documentazione del &nbsp;**motore di database per SQL Server**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (3+2): documentazione di &nbsp;&nbsp;**SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (3+3):&nbsp; documentazione di &nbsp;**Linux per SQL Server**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (7+10):&nbsp; documentazione dei &nbsp;**database relazionali per SQL Server**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di &nbsp;**SQL Server Reporting Services**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (1+3):&nbsp; documentazione di &nbsp;**SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (2+3):&nbsp; documentazione di &nbsp;**Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di &nbsp;**SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (5+2):&nbsp; documentazione di &nbsp;**SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di &nbsp;**Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (1+1): documentazione di &nbsp;&nbsp;**Tools per SQL Server**](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Aree di interesse *senza* articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0):**documentazione della**piattaforma di strumenti analitici per SQL Server](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (0 + 0): **Data Quality Services per SQL** documenti](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0 + 0): **estensioni DMX (Data Mining) per SQL** documenti](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0 + 0): **MDX (Multidimensional Expressions) per SQL** documenti](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0 + 0): **esempi per SQL** documenti](../samples/new-updated-samples.md)
- [Nuovo + aggiornato (0 + 0): **SQL Server Migration Assistant (SSMA)** documenti](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)

