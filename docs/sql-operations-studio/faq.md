---
title: SQL Operations Studio (preview) domande frequenti | Documenti Microsoft
description: Domande frequenti (FAQ) per SQL Operations Studio (preview).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ede16ad2aaafd14671cc9e58a4643a07ae85668a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="includename-sosincludesname-sosmd-faq"></a>[!INCLUDE[name-sos](../includes/name-sos.md)]DOMANDE FREQUENTI

## <a name="what-is-includename-sosincludesname-sos-shortmd"></a>Che cos'è [!INCLUDE[name-sos](../includes/name-sos-short.md)]?

[!INCLUDE[name-sos](../includes/name-sos-short.md)]è uno strumento di sviluppo e le operazioni di database leggero gratuito che viene eseguito sul desktop ed è disponibile per Windows, macOS e Linux. [!INCLUDE[name-sos](../includes/name-sos-short.md)]include il supporto incorporato per Database SQL di Azure, Azure SQL Data Warehouse e SQL Server in esecuzione in locale o in qualsiasi cloud. [!INCLUDE[name-sos](../includes/name-sos-short.md)]offre un'esperienza coerenza tra i database di propria scelta per i sistemi operativi Preferiti.

## <a name="where-can-i-get-includename-sosincludesname-sos-shortmd"></a>Dove è possibile ottenere [!INCLUDE[name-sos](../includes/name-sos-short.md)]?

Scaricare [!INCLUDE[name-sos](../includes/name-sos-short.md)] per Windows, macOS e Linux da [http://aka.ms/sqlopsstudio](download.md)

## <a name="how-much-does-includename-sosincludesname-sos-shortmd-cost"></a>Quanto costa [!INCLUDE[name-sos](../includes/name-sos-short.md)] costo?

[!INCLUDE[name-sos](../includes/name-sos-short.md)]è gratuito per uso commerciale o privato.

## <a name="who-should-use-includename-sosincludesname-sos-shortmd"></a>Chi dovrebbe utilizzare [!INCLUDE[name-sos](../includes/name-sos-short.md)]?

Gli utenti possono utilizzare [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Tuttavia, è progettato per semplificare le attività eseguite da fornitori di software indipendenti, gli amministratori di database, gli amministratori di sistema e gli sviluppatori di database.


## <a name="what-can-i-do-with-includename-sosincludesname-sos-shortmd"></a>Operazioni eseguibili con [!INCLUDE[name-sos](../includes/name-sos-short.md)]? 

[!INCLUDE[name-sos](../includes/name-sos-short.md)]è basato su codice di Visual Studio e offre un leggero, tastiera incentrata esperienza del flusso di lavoro di codice moderne, quando si lavora con SQL. 

[!INCLUDE[name-sos](../includes/name-sos-short.md)]rende le esperienze di core che affidano a ogni giorno molto semplice con funzionalità incorporate, ad esempio più finestre scheda, un editor avanzato di SQL, IntelliSense, completamento (parola chiave), frammenti di codice e spostamento di codice e integrazione del controllo codice sorgente (Git e TFS). È possibile eseguire query su richiesta, visualizzare & salvare i risultati come testo, JSON o Excel, modificare i dati, organizzare & gestire le connessioni di database Preferiti e sfogliare oggetti di database in un oggetto familiarità esperienza di esplorazione.

Utilizzare gli strumenti da riga di comando Preferiti (ad esempio, barra rovesciata, PowerShell, sqlcmd, bcp, psql e ssh) nella finestra Terminal integrata direttamente il [!INCLUDE[name-sos](../includes/name-sos-short.md)] interfaccia utente. Facilmente generare ed eseguire CREATE e inserimento script per oggetti di database creare copie del database di sviluppo o a scopo di test. Migliorare la produttività con codice smart frammenti di codice e ricco di grafiche esperienze creare nuovi database e oggetti di database (ad esempio tabelle, viste, stored procedure, gli utenti, account di accesso, ruoli, e così via) o aggiornare gli oggetti di database esistenti. Utilizzare dashboard personalizzabile avanzati per monitorare e risolvere rapidamente eventuali colli di bottiglia nel database locale, in Azure o di qualsiasi cloud.

[!INCLUDE[name-sos](../includes/name-sos-short.md)]offre un'esperienza coerenza per eseguire il backup e ripristino dei database. Con supporto pianificato per SQL Server di gruppi di disponibilità AlwaysOn, sia facilmente possibile configurare, monitorare e risolvere estensivi per i database di SQL Server critici e rapidamente il failover a un database secondario durante un'emergenza.
[!INCLUDE[name-sos](../includes/name-sos-short.md)]è stato progettato per aumentare la produttività del ciclo di vita di DevOps dei database desiderati nei sistemi operativi di propria scelta. Di conseguenza, si può sempre decidere e ridurre i rischi, risolvere i problemi più velocemente e distribuire continuamente il valore che supera le aspettative dei clienti.


## <a name="is-includename-sosincludesname-sos-shortmd-open-source"></a>È [!INCLUDE[name-sos](../includes/name-sos-short.md)] Open Source? 

Il codice sorgente per [!INCLUDE[name-sos](../includes/name-sos-short.md)] e il relativo provider di dati è disponibile su GitHub. Il codice sorgente per il front-end di [!INCLUDE[name-sos](../includes/name-sos-short.md)] (che si basa sul codice di Visual Studio) è disponibile in un contratto di licenza che fornisce diritti per modificare e utilizzare il software, ma non di ridistribuirla o inserirlo in un servizio cloud di codice sorgente. Il codice sorgente per i provider di dati è disponibile in base alla licenza MIT in [https://github.com/Microsoft/sqltoolsservice](https://github.com/Microsoft/sqltoolsservice).

## <a name="do-you-plan-to-open-source-ssms"></a>Si intende aprire origine SQL Server Management Studio?

No. Tuttavia, generazione successiva multi-OS CLI e interfaccia utente grafica di strumenti sono open source di. Ad esempio, l'estensione mssql per Visual Studio Code, mssql scripter e msql-CLI sono tutti open source su GitHub. Il codice sorgente per [!INCLUDE[name-sos](../includes/name-sos-short.md)] è disponibile su GitHub.


## <a name="now-that-there-is-includename-sosincludesname-sos-shortmd-does-microsoft-plan-to-deprecate-ssms-and-ssdt"></a>Ora che è [!INCLUDE[name-sos](../includes/name-sos-short.md)], Microsoft intende deprecare SQL Server Management Studio e SSDT?

No. Gli investimenti in strumenti di Windows all'occhiello (SQL Server Management Studio, SSDT, PowerShell) continuerà oltre la prossima generazione di multi-OS e gli strumenti CLI e interfaccia utente grafica di più database.
L'obiettivo è di offrire ai clienti di scegliere di utilizzare gli strumenti che desiderano sulle piattaforme di propria scelta per i relativi scenari.


## <a name="includename-sosincludesname-sos-shortmd-is-missing-a-feature-that-is-in-ssmsssdt-will-you-add-it"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)]manca una funzionalità in SQL Server Management Studio o SSDT. Si aggiungerà?
A seconda della necessità di scenario & cliente/business. Per definire la priorità, un suggerimento di file in [GitHub](https://github.com/microsoft/sqlopsstudio/issues).


## <a name="i-understand-includename-sosincludesname-sos-shortmd-and-the-mssql-extension-for-vs-code-are-powered-by-a-new-tools-service-that-uses-smo-apis-under-the-covers-is-smo-available-on-linux-and-macos"></a>Sono consapevole [!INCLUDE[name-sos](../includes/name-sos-short.md)] e l'estensione mssql per il codice di Visual Studio con un nuovo *strumenti servizio* che utilizza l'API SMO dietro le quinte. È disponibile in Linux e macOS SMO?

L'API SMO non sono ancora disponibili in Linux o macOS in modo utilizzabile. È stato trasferito su un sottoinsieme delle API SMO a .NET Core necessari per [!INCLUDE[name-sos](../includes/name-sos-short.md)], e si prevede di espandere come parte della funzionalità prevista.
Il servizio di strumenti di SQL è in GitHub: [https://github.com/Microsoft/sqltoolsservice](https://github.com/Microsoft/sqltoolsservice).


## <a name="do-you-plan-to-port-the-dacfx-apis-andor-sqlpackageexe-andor-ssdt-to-linux-and-macos"></a>Si intende la porta di DACFx APIs e/o sqlpackage.exe e/o SSDT per Linux e macOS?

È la roadmap a lungo termine. Per definire la priorità, un suggerimento di file in [GitHub](https://github.com/microsoft/sqlopsstudio/issues).


## <a name="will-sql-powershell-cmdlets-be-available-on-linux-and-macos"></a>I cmdlet di PowerShell per SQL saranno disponibili su Linux e macOS?

PowerShell per SQL è attualmente disponibile in PowerShell gallery ed è possibile utilizzare in Windows per funzionare con SQL Server in esecuzione in qualsiasi posizione, inclusi SQL su Linux. Offerta SQL PowerShell cmdlet Linux & macOS è nella Guida di orientamento. Per definire la priorità, un suggerimento di file in [GitHub](https://github.com/microsoft/sqlopsstudio/issues).

