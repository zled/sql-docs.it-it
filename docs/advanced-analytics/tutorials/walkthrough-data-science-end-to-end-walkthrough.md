---
title: Procedura dettagliata di analisi scientifica dei dati end-to-end per R e SQL Server | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3d4f38fd424c881392d48b0a6a24feb7f7e27ee0
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086503"
---
# <a name="end-to-end-data-science-walkthrough-for-r-and-sql-server"></a>Procedura dettagliata di analisi scientifica dei dati end-to-end per R e SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa procedura dettagliata, si sviluppa una soluzione end-to-end per la modellazione predittiva basata sul supporto delle funzionalità di R in SQL Server 2016 o SQL Server 2017.

Questa procedura dettagliata è basata su un set di dati pubblico molto diffuso, il set di dati dei taxi di New York City. Si utilizza una combinazione di codice R, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati e funzioni SQL personalizzate per compilare un modello di classificazione che indica la probabilità che il driver potrebbe riceverà una Mancia in una determinata corsa. È inoltre distribuire il modello R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e usare i dati del server per generare punteggi basati sul modello.

In questo esempio può essere esteso a tutti i tipi di problemi reali, ad esempio alla previsione delle risposte dei clienti alle campagne di vendita o alla previsione di spesa o partecipazione agli eventi. Poiché il modello può essere richiamato da una stored procedure, è possibile incorporarlo facilmente in un'applicazione.

Poiché la procedura dettagliata è progettata per illustrare agli sviluppatori R [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], R viene usato laddove possibile. Tuttavia, ciò non significa che R sia necessariamente lo strumento migliore per ogni attività. In molti casi, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe offrire prestazioni migliori, in particolare in attività quali l'aggregazione dei dati e la progettazione delle funzionalità.  Tali attività possono trarre vantaggio dalle nuove funzionalità di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ad esempio gli indici columnstore con ottimizzazione per la memoria. Cerchiamo di evidenziare le ottimizzazioni possibili lungo il percorso.

## <a name="target-audience"></a>Destinatari

Questa procedura dettagliata è destinata agli sviluppatori di R o SQL. Offre un'introduzione su come integrare R nei flussi di lavoro aziendali usando [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  È necessario avere familiarità con le operazioni di database, ad esempio la creazione di tabelle e database, l'importazione di dati e l'esecuzione di query.

+ Sono inclusi tutti gli script SQL e R.
+ Si potrebbe essere necessario modificare le stringhe negli script per l'esecuzione nell'ambiente in uso. È possibile farlo con qualsiasi editor di codice, ad esempio [Visual Studio Code](https://code.visualstudio.com/Download).

## <a name="prerequisites"></a>Prerequisiti

È consigliabile eseguire questa procedura dettagliata su un computer portatile o un altro computer con installate le librerie di Microsoft R. È necessario essere in grado di connettersi, nella stessa rete, a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer con SQL Server e il linguaggio R abilitata.

È possibile eseguire la procedura dettagliata in un computer che abbia sia [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un ambiente di sviluppo R, ma è sconsigliato questa configurazione per un ambiente di produzione.

Se si desidera eseguire comandi R da un computer remoto, ad esempio un portatile o un altro computer connesso alla rete, è necessario installare le librerie Microsoft R Open. È possibile installare Microsoft R Client o Microsoft R Server. Il computer remoto deve essere in grado di connettersi al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.

Se è necessario includere client e server nello stesso computer, assicurarsi di installare un set separato di librerie di Microsoft R da usare nell'invio di script R da un client "remoto". Non usare le librerie R che vengono installate per l'uso per l'istanza di SQL Server per questo scopo.

## <a name="add-r-to-sql-server"></a>Aggiungere R a SQL Server

È necessario avere accesso a un'istanza di SQL Server con il supporto per R installato. Questa procedura dettagliata è stata originariamente sviluppata per SQL Server 2016 e testata nel 2017, pertanto dovrebbe essere possibile usare una delle seguenti versioni di SQL Server. (Esistono alcune lievi differenze nelle funzioni RevoScaleR tra le versioni.)

+ [Installare SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Installare SQL Server 2016 R Services](../install/sql-r-services-windows-install.md).

## <a name="install-an-r-development-environment"></a>Installare un ambiente di sviluppo R

Per questa procedura dettagliata, è consigliabile che usare un ambiente di sviluppo R. Di seguito sono riportati alcuni suggerimenti:

- **R Tools per Visual Studio** (RTVS) è disponibile gratuitamente come plug-in che offre Intellisense, debug e il supporto per Microsoft R. È possibile usarlo con R Server e SQL Server Machine Learning Services. Per scaricarlo, vedere [R Tools per Visual Studio](https://www.visualstudio.com/vs/rtvs/).

- **Microsoft R Client** è uno strumento di sviluppo leggero che supporta lo sviluppo in R usando il pacchetto RevoScaleR. Per ottenerlo, vedere [Introduzione a Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client).

- **RStudio** è uno degli ambienti più diffusi per lo sviluppo di R. Per altre informazioni, vedere [ https://www.rstudio.com/products/RStudio/ ](https://www.rstudio.com/products/RStudio/).

    Non è possibile completare questa esercitazione usando un'installazione generica di RStudio o un altro ambiente; è anche necessario installare i pacchetti R e librerie di connettività per Microsoft R Open. Per altre informazioni, vedere [Configurare un client per l'analisi scientifica dei dati](../r/set-up-a-data-science-client.md).

- Strumenti R di base (R.exe, RTerm.exe, RScripts.exe) inoltre vengono installati per impostazione predefinita quando si installa R in SQL Server o Client R. Se non si desidera installare un IDE, è possibile usare questi strumenti.

## <a name="get-permissions-on-the-sql-server-instance-and-database"></a>Ottenere le autorizzazioni per l'istanza di SQL Server e database

Per connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire gli script e caricare i dati, è necessario un account di accesso valido nel server di database.  È possibile usare un account di accesso SQL o un'autenticazione integrata di Windows. Chiedere all'amministratore del database per configurare le autorizzazioni seguenti per l'account, nel database in cui si usa r:

- Creare database, tabelle, funzioni e stored procedure
- Scrivere dati nelle tabelle
- Possibilità di eseguire script R (`GRANT EXECUTE ANY EXTERNAL SCRIPT to <user>`)

Per questa procedura dettagliata, abbiamo utilizzato l'account di accesso SQL **RTestUser**. È consigliabile in genere si utilizza l'autenticazione integrata di Windows, ma utilizzando l'account di accesso SQL è più semplice per alcune finalità di demo.

## <a name="next-steps"></a>Passaggi successivi

[Preparare i dati usando PowerShell](walkthrough-prepare-the-data.md)
