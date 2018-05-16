---
title: Domande frequenti su SQL Operations Studio (anteprima) | Microsoft Docs
description: Domande frequenti (FAQ) su SQL Operations Studio (anteprima).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b902c414c1e1d0405595109f45a0c6e495424c00
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="includename-sosincludesname-sosmd-faq"></a>Domande frequenti su [!INCLUDE[name-sos](../includes/name-sos.md)]

## <a name="what-is-includename-sosincludesname-sos-shortmd"></a>Che cos'è [!INCLUDE[name-sos](../includes/name-sos-short.md)]?

[!INCLUDE[name-sos](../includes/name-sos-short.md)] è uno strumento di sviluppo e di gestione delle operazioni su database, leggero e gratuito, eseguito su desktop, disponibile per Windows, macOS e Linux. [!INCLUDE[name-sos](../includes/name-sos-short.md)] include il supporto incorporato per Database SQL di Azure, Azure SQL Data Warehouse e SQL Server installati in locale o in qualsiasi cloud. [!INCLUDE[name-sos](../includes/name-sos-short.md)] offre un'esperienza coerente tra i propri database e nei sistemi operativi preferiti.

## <a name="where-can-i-get-includename-sosincludesname-sos-shortmd"></a>Dove è possibile ottenere [!INCLUDE[name-sos](../includes/name-sos-short.md)]?

Scaricare [!INCLUDE[name-sos](../includes/name-sos-short.md)] per Windows, macOS e Linux da [http://aka.ms/sqlopsstudio](download.md)

## <a name="how-much-does-includename-sosincludesname-sos-shortmd-cost"></a>Quanto costa [!INCLUDE[name-sos](../includes/name-sos-short.md)] costo?

[!INCLUDE[name-sos](../includes/name-sos-short.md)] è gratuito per uso commerciale o privato.

## <a name="who-should-use-includename-sosincludesname-sos-shortmd"></a>Chi dovrebbe utilizzare [!INCLUDE[name-sos](../includes/name-sos-short.md)]?

Gli utenti possono utilizzare [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Tuttavia, è progettato per semplificare le attività eseguite da fornitori di software indipendenti, gli amministratori di database, gli amministratori di sistema e gli sviluppatori di database.


## <a name="what-can-i-do-with-includename-sosincludesname-sos-shortmd"></a>Operazioni eseguibili con [!INCLUDE[name-sos](../includes/name-sos-short.md)]? 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] è costruito su Visual Studio Code e offre un'esperienza leggera, focalizzata sull'utilizzo della tastiera e basata su un moderno workflow di codice, quando si lavora con SQL.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] rende il lavoro di ogni giorno molto semplice tramite funzionalità incorporate, come ad esempio la gestione a schede, un editor avanzato di SQL, IntelliSense, il completamento automatico delle parole chiave, i frammenti di codice, la navigazione del codice e l'integrazione del controllo del codice sorgente (Git e TFS). È possibile eseguire query a richiesta, visualizzare e salvare i risultati come testo, JSON o Excel, modificare i dati, organizzare e gestire le connessioni ai database preferiti e sfogliare oggetti di database tramite una familiare esperienza di esplorazione.

Utilizza gli strumenti da riga di comando (ad esempio, bash, PowerShell, sqlcmd, bcp, psql e ssh) nella finestra del terminale integrato direttamente nell'interfaccia utente di [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Genera ed esegui script di CREATE e INSERT per gli oggetti di database al fine di creare copie del database di sviluppo o a scopo di test. Migliora la produttività con frammenti di codice intelligenti e con grafiche ricche ed intuitive per creare nuovi oggetti di database (ad esempio tabelle, viste, stored procedure, utenti, account di accesso, ruoli e così via) o per aggiornare gli oggetti di database esistenti. Utilizza le dashboard personalizzabili al fine di monitorare e risolvere rapidamente eventuali colli di bottiglia nei database locali, in Azure o in qualsiasi cloud.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] offre un'esperienza coerente per eseguire backup e ripristino dei database. Con il supporto pianificato dei gruppi di disponibilità AlwaysOn per SQL Server, è possibile configurare, monitorare e risolvere problemi sui database di SQL Server mission-critical ed eseguire rapidamente il failover a un database secondario durante un'emergenza.
[!INCLUDE[name-sos](../includes/name-sos-short.md)] è stato progettato per aumentare la produttività del ciclo di vita di DevOps dei database desiderati nei sistemi operativi di propria scelta. Di conseguenza, si riducono i rischi, si risolvono i problemi più velocemente e si distribuisce continuamente valore che supera le aspettative dei clienti.


## <a name="is-includename-sosincludesname-sos-shortmd-open-source"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)] è Open Source? 

Il codice sorgente di [!INCLUDE[name-sos](../includes/name-sos-short.md)] e il relativo provider di dati sono disponibili su GitHub. Il codice sorgente per il front-end di [!INCLUDE[name-sos](../includes/name-sos-short.md)] (che si basa su Visual Studio Code) è disponibile con un contratto di licenza che fornisce diritti per modificare e utilizzare il software, ma non per ridistribuirlo o inserirlo in un servizio cloud di codice sorgente. Il codice sorgente per i provider di dati è disponibile con licenza MIT in [https://github.com/Microsoft/sqltoolsservice](https://github.com/Microsoft/sqltoolsservice).

## <a name="do-you-plan-to-open-source-ssms"></a>Si desidera rendere SQL Server Management Studio open source?

No. Tuttavia, la nuova generazione di CLI e di interfacce utente per gli strumenti con supporto multi-OS sono open source. Ad esempio, l'estensione mssql per Visual Studio Code, mssql scripter e msql-CLI sono tutti open source su GitHub. Il codice sorgente di [!INCLUDE[name-sos](../includes/name-sos-short.md)] è disponibile su GitHub.


## <a name="now-that-there-is-includename-sosincludesname-sos-shortmd-does-microsoft-plan-to-deprecate-ssms-and-ssdt"></a>Ora che è [!INCLUDE[name-sos](../includes/name-sos-short.md)], Microsoft intende deprecare SQL Server Management Studio e SSDT?

No. Gli investimenti per i principali strumenti Windows (SQL Server Management Studio, SSDT, PowerShell) continueranno insieme alla nuova generazione di strumenti ed interfacce grafiche multi-OS e multi-DB.
L'obiettivo è quello di offrire ai clienti la possibilità di scegliere gli strumenti che desiderano utilizzare sulle piattaforme di propria scelta, in base ai relativi scenari.


## <a name="includename-sosincludesname-sos-shortmd-is-missing-a-feature-that-is-in-ssmsssdt-will-you-add-it"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)]manca di una funzionalità presente in SQL Server Management Studio o SSDT. Verrà aggiunta?
A seconda dello scenario e delle necessità del cliente/business. Per aiutare a definire la priorità, invia un suggerimento in [GitHub](https://github.com/microsoft/sqlopsstudio/issues).


## <a name="i-understand-includename-sosincludesname-sos-shortmd-and-the-mssql-extension-for-vs-code-are-powered-by-a-new-tools-service-that-uses-smo-apis-under-the-covers-is-smo-available-on-linux-and-macos"></a>Sono consapevole che [!INCLUDE[name-sos](../includes/name-sos-short.md)] e l'estensione mssql per Visual Studio Code si basano su un nuovo *servizio di strumenti* che utilizza l'API di SMO dietro le quinte. SMO è disponibile in Linux e macOS?

Le API di SMO non sono ancora utilizzabili in Linux o macOS. È stato trasferito solo un sottoinsieme delle API di SMO a .NET Core, necessario per [!INCLUDE[name-sos](../includes/name-sos-short.md)], e si prevede di espanderlo come definito in roadmap.
Il servizio di strumenti di SQL è in GitHub: [ https://github.com/Microsoft/sqltoolsservice ](https://github.com/Microsoft/sqltoolsservice).


## <a name="do-you-plan-to-port-the-dacfx-apis-andor-sqlpackageexe-andor-ssdt-to-linux-and-macos"></a>È prevista la conversione di DACFx APIs e/o sqlpackage.exe e/o SSDT per Linux e macOS?

È sulla roadmap a lungo termine. Per aiutare a definire la priorità, invia un suggerimento in [GitHub](https://github.com/microsoft/sqlopsstudio/issues).


## <a name="will-sql-powershell-cmdlets-be-available-on-linux-and-macos"></a>I cmdlet di PowerShell per SQL saranno disponibili su Linux e macOS?

PowerShell per SQL è attualmente disponibile nella PowerShell gallery ed è possibile utilizzarlo in Windows con SQL Server in esecuzione in qualsiasi posizione, incluso su Linux. Rendere disponibili le cmdlet PowerShell di SQL su Linux e macOS è nella roadmap. Per aiutare a definire la priorità, invia un suggerimento in [GitHub](https://github.com/microsoft/sqlopsstudio/issues).

