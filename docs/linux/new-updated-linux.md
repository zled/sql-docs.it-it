---
title: 'Aggiornato: SQL Server in Linux docs | Documenti Microsoft'
description: Visualizzare i frammenti di contenuto aggiornato per la documentazione modificato di recente in, per Microsoft SQL Server in Linux.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: rothja
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: linux-sql
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 07/17/2017
ms.author: genemi
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 13c237af359c543f6a99a0fce101af81b5eb2bcf
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Nuovi e recentemente aggiornato: SQL Server in Linux documenti

Quasi ogni giorno Microsoft aggiorna alcuni articoli esistenti nel relativo [Docs.Microsoft.com](http://docs.microsoft.com/) sito Web di documentazione. In questo articolo consente di visualizzare estratti dagli articoli aggiornati di recente. Potrebbero anche essere elencati collegamenti a nuovi articoli.

In questo articolo viene generato da un programma che viene eseguito di nuovo periodicamente. In alcuni casi un estratto può apparire con formattazione perfetto, o come markdown nell'articolo di origine. Le immagini non vengono mai visualizzate qui.

Aggiornamenti recenti vengono indicati per il seguente intervallo di date e l'oggetto:



- *Intervallo degli aggiornamenti di date:* &nbsp; **2017-05-23** &nbsp; - a - &nbsp; **2017-07-17**
- *Area di interesse:* &nbsp; **Microsoft SQL Server in Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Eseguire l'immagine di SQL Server 2017 contenitore con Docker](quickstart-install-connect-docker.md)
2. [Installazione di SQL Server e creare un database in Red Hat](quickstart-install-connect-red-hat.md)
3. [Installazione di SQL Server e creare un database in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
4. [Installazione di SQL Server e creare un database in Ubuntu](quickstart-install-connect-ubuntu.md)
5. [Esempio: Script di installazione automatica di SQL Server per Red Hat Enterprise Linux](sample-unattended-install-redhat.md)
6. [Esempio: Script di installazione automatica di SQL Server per SUSE Linux Enterprise Server](sample-unattended-install-suse.md)
7. [Esempio: Script di installazione automatica di SQL Server per Ubuntu](sample-unattended-install-ubuntu.md)
8. [Autenticazione di Active Directory con SQL Server in Linux](sql-server-linux-active-directory-authentication.md)
9. [Elevata disponibilità e protezione dei dati per le configurazioni di gruppo di disponibilità](sql-server-linux-availability-group-ha.md)
10. [Configurare le immagini contenitore di SQL Server 2017 in Docker](sql-server-linux-configure-docker.md)
11. [Suggerimenti dei clienti per SQL Server in Linux](sql-server-linux-customer-feedback.md)
12. [Crittografia delle connessioni a SQL Server in Linux](sql-server-linux-encrypted-connections.md)
13. [Installare SQL Server Integration Services (SSIS) in Linux](sql-server-linux-setup-ssis.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Compact elenco degli articoli aggiornato di recente

Questo elenco compact vengono forniti collegamenti a tutti gli articoli aggiornati elencati nella sezione estratti.



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione vengono estratti gli aggiornamenti raccolti dagli articoli di cui si sono verificati recentemente un aggiornamento di grandi dimensioni.

Gli estratti visualizzati qui vengono visualizzati separatamente dal relativo contesto semantica corretto Inoltre, talvolta un estratto è separato dalla sintassi markdown importante che la racchiude nell'articolo effettivo. Di conseguenza questi estratti sono solo a scopo generale. Gli estratti consentono solo di sapere se i tuoi interessi garantiscono la necessità di fare clic e visitare l'articolo effettivo.

Per queste e altre ragioni, non copiare da questi estratti di codice e non prendono come verità esatta qualsiasi testo estratto. In alternativa, visitare l'articolo effettivo.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-sles-cluster-for-sql-server-availability-groupsql-server-linux-availability-group-cluster-slesmd"></a>1. &nbsp;[Configurare SLES Cluster per il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-sles.md)

*Updated: 2017-06-22* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 189.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f8d28af253be1dc67615f1ea04135b2f6dff3b71 8be07deddcf0c348d75bf5b4f44615c2383e0722  (PR=2150  ,  Filename=sql-server-linux-availability-group-cluster-sles.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=6dccaff93a6c8b2374a1fad069b2f597898802fc) -->



**Impostare la proprietà cluster start-errore-è-errore irreversibile per false**


`Start-failure-is-fatal`indica se un errore di avvio di una risorsa in un nodo impedisce ulteriori tentativi di avvio in tale nodo. Se impostato su `false`, il cluster stabilirà se provare ad avviare nello stesso nodo in base alle corrente conteggio e la migrazione soglia di errore della risorsa. In tal caso, dopo che si verifica il failover, Pacemaker tenterà di avviare la risorsa del gruppo di disponibilità sulla prima primario quando l'istanza SQL è disponibile. Pacemaker si occuperà di abbassamento di livello la replica secondaria e verrà automaticamente aggiunto nuovamente il gruppo di disponibilità. Inoltre, se `start-failure-is-fatal` è impostato su `false`, il cluster eseguirà il fallback per i limiti configurati failcount configurati con la soglia di migrazione, pertanto è necessario verificare che predefinito per il limite di migrazione viene aggiornato di conseguenza.

Per aggiornare il valore della proprietà per l'esecuzione false:
```
sudo crm configure property start-failure-is-fatal=false
sudo crm configure rsc_defaults migration-threshold=5000
```
Se la proprietà ha il valore predefinito di `true`, se il primo tentativo di avviare la risorsa non, l'intervento dell'utente è obbligatorio dopo un failover automatico per eseguire la pulizia il conteggio degli errori di risorse e reimposta la configurazione mediante: `sudo crm resource cleanup <resourceName>` comando.

Per ulteriori informazioni sulle proprietà del cluster Pacemaker vedere [la configurazione di risorse Cluster](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_config_crm_resources.html).

**Configurare fencing (STONITH)**

I fornitori di cluster pacemaker richiedono STONITH deve essere abilitata e un dispositivo fencing configurato per l'installazione del cluster supportate. Quando il gestore delle risorse cluster non è possibile determinare lo stato di un nodo o di una risorsa in un nodo, fencing viene utilizzato per visualizzare di nuovo il cluster in uno stato noto.
Fencing livello risorse principalmente garantisce che non vi sia alcun danneggiamento dei dati in caso di interruzione tramite la configurazione di una risorsa. È possibile utilizzare fencing livello di risorse, ad esempio, con DRBD (Distributed replicati blocco dispositivo) per contrassegnare il disco in un nodo come obsoleta quando il collegamento di comunicazione si arresta.




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-release-notes-for-sql-server-2017-on-linuxsql-server-linux-release-notesmd"></a>2. &nbsp;[Note sulla versione di SQL Server 2017 su Linux](sql-server-linux-release-notes.md)

*Updated: 2017-06-20* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1))

<!-- Source markdown line 156.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 684da20f7834000886d7a93f83563c55dc3cf9a6 8597bcde7e5754bb7f38de1ec980027245dac6e5  (PR=2115  ,  Filename=sql-server-linux-release-notes.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=424a23fd98876db808b91f017e7acbcb5b4daa45) -->



**SQL Server Integration Services (SSIS)**

È possibile eseguire pacchetti SSIS in Linux. Per altre informazioni, vedere il [post di blog annunciato il supporto SSIS per Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/). Tenere presente i seguenti problemi noti con questa versione.

- Il **mssql server è** pacchetto è supportato solo in Ubuntu in questo momento.

- Le funzionalità seguenti non sono supportate durante l'esecuzione di pacchetti SSIS in Linux:
  - Database del catalogo SSIS
  - Pianificare l'esecuzione di pacchetti da SQL Agent
  - Autenticazione di Windows
  - Componenti di terze parti
  - Driver ODBC di terze parti
  - Gestione connessione ODBC, origine e destinazione (supportato con SSIS in Linux CTP 2.1 aggiornamento)
  - Change Data Capture (CDC)
  - Scalabilità orizzontale
  - Azure Feature Pack
  - Hadoop e HDFS supporto
  - Microsoft Connector for SAP BW

Con SSIS in Linux CTP 2.1 aggiornamento, i pacchetti SSIS possono utilizzare connessioni di ODBC in Linux. Per altre informazioni, vedere il [post del blog annuncia il supporto ODBC in Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>Articoli simili

Questa sezione sono elencati gli articoli molto simili per gli articoli aggiornati di recente in altre aree di interesse, nello stesso repository GitHub.com: [MicrosoftDocs /**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse che hanno gli articoli di nuovi o aggiornati di recente

- [Nuovo + aggiornati (4 + 4): **Analitica avanzate per SQL** documenti](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (2 + 0): **Analysis Services per SQL** documenti](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (1 + 2): **Connect to SQL** documenti](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (6 + 0): **motore di Database per SQL** documenti](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (13 + 2): **Linux per SQL** documenti](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (1 + 0): **Master Data Services (MDS) per SQL** documenti](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (1 + 0): **ODBC (Open Database Connectivity) per SQL** documenti](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornati (4 8 +): **database relazionali di SQL** documenti](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (2 + 2): **Microsoft SQL Server** documenti](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0 + 1): **SQL Server Management Studio (SSMS)** documenti](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (1 + 0): **Transact-SQL** documenti](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (1 + 0): **Tools per SQL** documenti](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse che non dispone di alcun nuovo o aggiornati di recente articoli

- [Nuovo + aggiornato (0 + 0): **oggetti ADO (ActiveX Data) per SQL** documenti](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0 + 0): **Data Quality Services per SQL** documenti](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0 + 0): **estensioni DMX (Data Mining) per SQL** documenti](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0 + 0): **Integration Services per SQL** documenti](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (0 + 0): **MDX (Multidimensional Expressions) per SQL** documenti](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0 + 0): **PowerShell per SQL** documenti](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0 + 0): **Reporting Services per SQL** documenti](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0 + 0): **esempi per SQL** documenti](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0 + 0): **SQL Server Data Tools (SSDT)** documenti](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0 + 0): **SQL Server Migration Assistant (SSMA)** documenti](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0 + 0): **XQuery per SQL** documenti](../xquery/new-updated-xquery.md)


&nbsp;


