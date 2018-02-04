---
title: SQL Server in Linux domande frequenti | Documenti Microsoft
description: In questo articolo fornisce le risposte alle domande frequenti su SQL Server in esecuzione in Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/21/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Active
ms.openlocfilehash: 2da90e6cdf49531980e9014075d7b094b61271fd
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="sql-server-on-linux-frequently-asked-questions-faq"></a>SQL Server in Linux domande frequenti (FAQ)

Le sezioni seguenti forniscono le domande frequenti e risposte per SQL Server in esecuzione in Linux.

## <a name="general-questions"></a>Domande di carattere generale

1. **Quali piattaforme Linux sono supportati?**

   SQL Server è attualmente supportato in Red Hat Enterprise Server, SUSE Linux Enterprise Server e Ubuntu. Per informazioni aggiornate sulle versioni supportate, vedere [le piattaforme supportate](sql-server-linux-setup.md#supportedplatforms).

1. **Le funzionalità di SQL Server supportate in Linux?**

   Per un elenco completo di funzionalità supportate e i problemi noti, vedere il [note sulla versione](sql-server-linux-release-notes.md).

1. **Quali sono i criteri di supporto per SQL Server?**

   Per comprendere i criteri di supporto, vedere il [criteri di supporto tecnico per SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

1. **Sono provenienti da uno sfondo di Windows SQL Server. Sono presenti risorse che consentono di imparare a utilizzare SQL Server in Linux?**

   Il [Guide rapide](sql-server-linux-setup.md#platforms) vengono fornite istruzioni dettagliate su come installare SQL Server in Linux ed eseguire query Transact-SQL. Altre esercitazioni forniscono istruzioni aggiuntive sull'utilizzo di SQL Server in Linux. Per un elenco di terze parti dei suggerimenti, vedere il [elenco MSSQLTIPS di SQL Server in Linux suggerimenti](https://www.mssqltips.com/sql-server-tip-category/226/sql-server-on-linux/).

## <a name="installation"></a>Installazione

1. **Come ottenere SQL Server installata in my server Linux?**

   Microsoft gestisce il repository di pacchetti per l'installazione di SQL Server e supporta l'installazione tramite gestori di pacchetti nativo, ad esempio yum, zypper e appartamento. Per installare rapidamente, vedere uno del [Guide rapide](sql-server-linux-setup.md#platforms).

1. **È possibile installare SQL Server nel sottosistema di Linux per Windows 10?**

   No. Linux in esecuzione in Windows 10 non è attualmente una piattaforma supportata per SQL Server e strumenti correlati.

1. **Quali sistemi di file Linux 2017 di SQL Server possono usare per i file di dati?**

   SQL Server in Linux supporta attualmente ext4 e XFS. Verrà aggiunto il supporto per altri sistemi di file in base alle esigenze in futuro.

1. **È possibile scaricare i pacchetti di installazione per installare SQL Server in modalità offline?**

   Sì. Per ulteriori informazioni, vedere il pacchetto di download di collegamenti nel [note sulla versione](sql-server-linux-release-notes.md). Inoltre, esaminare il [istruzioni per le installazioni non in linea](sql-server-linux-setup.md#offline).

1. **È possibile eseguire un'installazione automatica di SQL Server in Linux?**

   Sì. Per informazioni di installazione automatica, vedere [Guida all'installazione per SQL Server in Linux](sql-server-linux-setup.md#unattended). Vedere gli script di esempio per [Red Hat](sample-unattended-install-redhat.md), [SUSE Linux Enterprise Server](sample-unattended-install-suse.md), e [Ubuntu](sample-unattended-install-ubuntu.md). È inoltre possibile rivedere [questo script di esempio](https://blogs.msdn.microsoft.com/sqlcat/2017/10/03/unattended-install-and-configuration-for-sql-server-2017-on-linux/) creato per il Team di consulenza clienti di SQL Server.

## <a name="tools"></a>Strumenti

1. **È possibile utilizzare il client di SQL Server Management Studio in Windows per accedere a SQL Server in Linux?**

   Sì, è possibile utilizzare tutti gli strumenti esistenti in esecuzione su Windows per accedere a SQL Server in Linux. Sono inclusi strumenti forniti da Microsoft, ad esempio SQL Server Management Studio (SSMS), SQL Server Data Tools (SSDT) e sistemi operativi e gli strumenti di terze parti.

1. **È uno strumento quale SQL Server Management Studio in esecuzione su Linux?**

   Nuovo Microsoft SQL operazioni Studio (anteprima) è uno strumento multipiattaforma per la gestione di SQL Server. Per ulteriori informazioni, vedere [che cos'è Microsoft SQL operazioni Studio (anteprima)](../sql-operations-studio/what-is.md).

1. **Sono disponibili in Linux comandi sqlcmd e bcp?**

   Sì, [sqlcmd e bcp](sql-server-linux-setup-tools.md) sono disponibili in modo nativo in Linux, macOS e Windows. Inoltre, usare il nuovo [mssql scripter](https://github.com/Microsoft/mssql-scripter) strumento da riga di comando in Linux, macOS o Windows per generare script T-SQL per il database SQL eseguito su qualsiasi. Vedere anche l'anteprima di rilascio per [mssql-cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/).

1. **È possibile visualizzare Monitoraggio attività quando è connesso tramite SQL Server Management Studio in Windows per un'istanza in esecuzione in Linux?**

   Sì, è possibile utilizzare SQL Server Management Studio in Windows per connettersi in remoto e utilizzare strumenti / funzionalità quali comandi di Monitoraggio attività in un'istanza di Linux.

1. **Quali sono disponibili strumenti per monitorare le prestazioni di SQL Server in Linux?**

   È possibile utilizzare [viste a gestione dinamica (DMV) sistema](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) per raccogliere i vari tipi di informazioni su SQL Server, incluse le informazioni sul processo di Linux. È possibile utilizzare [archivio Query](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md) per migliorare le prestazioni delle query. Altri strumenti, ad esempio predefinito [Dashboard prestazioni](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-performance-dashboard-built-in/)funziona in modalità remota in SQL Server Management Studio (SSMS) da Windows.

## <a name="administration"></a>Amministrazione

1. **Ha creato un'app, ad esempio Gestione configurazione SQL Server in Linux?**

   Sì, è uno strumento di configurazione per SQL Server in Linux: [mssql conf](sql-server-linux-configure-mssql-conf.md).

1. **SQL Server in Linux supporta più istanze nello stesso host?**

   Si consiglia di eseguire più contenitori in un host di avere più istanze distinte. Ogni contenitore sarà necessario per l'ascolto su una porta diversa. Per ulteriori informazioni, vedere [eseguire più contenitori di SQL Server](sql-server-linux-configure-docker.md#run-multiple-sql-server-containers).

1. **Autenticazione di Active Directory è supportata in Linux?**

   Sì. Per ulteriori informazioni, vedere [l'autenticazione di Active Directory con SQL Server in Linux](sql-server-linux-active-directory-authentication.md).

1. **Always On e clustering supportate in Linux?**

   Clustering di failover e la disponibilità elevata in Linux si ottengono con Pacemaker in Linux. Per ulteriori informazioni, vedere [continuità aziendale e database di ripristino, SQL Server in Linux](sql-server-linux-business-continuity-dr.md).

1. **È possibile configurare la replica da Linux a Windows e viceversa?**

   Le repliche di scala di lettura è utilizzabile tra Windows e Linux per la replica unidirezionale dei dati.

1. **È possibile eseguire la migrazione di database esistenti nelle versioni precedenti di SQL Server da Windows a Linux?**

   Sì, esistono [diversi metodi](sql-server-linux-migrate-overview.md) di raggiungere questo obiettivo.

1. **È possibile migrare dati da Oracle e altri motori di database a SQL Server in Linux?**

   Sì. SSMA supporta la migrazione da diversi tipi di motori di database: Microsoft Access, DB2, MySQL, Oracle e SAP ASE (in precedenza SAP Sybase ASE). Per un esempio di come utilizzare SSMA, vedere [eseguire la migrazione di uno schema Oracle a SQL Server 2017 in Linux con SQL Server Migration Assistant](../ssma/oracle/sql-server-linux-convert-from-oracle.md?toc=%2fsql%2flinux%2ftoc.json).

1. **Quali autorizzazioni sono necessarie per i file di SQL Server?**

   Tutti i file di `/var/opt/mssql` cartella del file deve essere di proprietà il **mssql** utente e appartengono al **mssql** gruppo. Entrambi i **mssql** utente e gruppo deve disporre delle autorizzazioni di lettura / scrittura di tutti i file e directory. Tenere presente i seguenti scenari speciali che includono le autorizzazioni file e directory:

   * Le autorizzazioni per gruppo e il proprietario mssql sono necessari montate condivisioni di rete utilizzata per archiviare i file di SQL Server.
   * Se si individua file di database o backup in una directory non predefinito, è necessario impostare anche le autorizzazioni per tale directory.
   * Se si modifica il umask radice predefinito da 0022, configurazione di SQL Server non riesce dopo l'installazione. Quindi è necessario applicare manualmente le autorizzazioni necessarie all'account di avvio di SQL Server.

1. **È possibile modificare la proprietà di SQL Server file e directory mssql installato account dal gruppo?**

   Non è supportata la modifica del proprietario della directory di SQL Server e i file di installazione predefinita. Il conto mssql e il gruppo è utilizzato in particolare per SQL Server e non dispone dell'accesso interattivo accesso.

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni sull'esecuzione di SQL Server in Linux, vedere il [Panoramica di SQL Server in Linux](sql-server-linux-overview.md).