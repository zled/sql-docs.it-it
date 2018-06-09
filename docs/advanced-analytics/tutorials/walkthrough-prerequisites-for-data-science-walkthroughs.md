---
title: Prerequisiti per la procedura dettagliata dell'analisi scientifica dei dati per SQL Server e R | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4f0e6130882ea5af6dd0827ed2d5e798d3c11c5f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585493"
---
# <a name="prerequisites-for-the-data-science-walkthrough-for-sql-server-and-r"></a>Prerequisiti per la procedura dettagliata dell'analisi scientifica dei dati per SQL Server e R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

È consigliabile eseguire questa procedura dettagliata su un computer portatile o un altro computer che installate le librerie di Microsoft R. È necessario essere in grado di connettersi, nella stessa rete, a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer con servizi di machine learning e il linguaggio R abilitato.

È possibile eseguire la procedura dettagliata in un computer che dispone di entrambe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un ambiente di sviluppo di R, ma si sconsiglia di questa configurazione per un ambiente di produzione.

## <a name="install-machine-learning-for-sql-server"></a>Installare l'apprendimento di SQL Server

È necessario avere accesso a un'istanza di SQL Server con il supporto per R installato. Questa procedura dettagliata è stato originariamente sviluppata per SQL Server 2016 e testata su 2017, pertanto dovrebbe essere in grado di utilizzare una delle seguenti versioni di SQL Server. (Vi sono alcune piccole differenze nelle funzioni RevoScaleR tra le versioni).

+ Per SQL Server 2017 di Machine Learning Services (In-Database)
+ SQL Server 2016 R Services

Per altre informazioni, vedere [installare SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) oppure [installare SQL Server 2016 R Services](../install/sql-r-services-windows-install.md).

> [!IMPORTANT]
> Versioni di SQL Server precedenti a 2016 non supportano l'integrazione con R. Tuttavia, è possibile utilizzare il database SQL precedenti come un'origine dati ODBC.

## <a name="install-an-r-development-environment"></a>Installare un ambiente di sviluppo di R

Per questa procedura dettagliata, è consigliabile utilizzare un ambiente di sviluppo R. Di seguito sono riportati alcuni suggerimenti:

- **Strumenti R per Visual Studio** (RTVS) è un plug-in che fornisce Intellisense, debug e il supporto per Microsoft R. È possibile utilizzare con R Server e servizi di SQL Server Machine Learning. Per scaricarlo, vedere [R Tools per Visual Studio](https://www.visualstudio.com/vs/rtvs/).

- **Microsoft R Client** è uno strumento di sviluppo leggero che supporta lo sviluppo di R usando il pacchetto RevoScaleR. Per ottenerlo, vedere [Introduzione a Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client).

- **RStudio** è uno degli ambienti più diffusi per lo sviluppo di R. Per ulteriori informazioni, vedere [ https://www.rstudio.com/products/RStudio/ ](https://www.rstudio.com/products/RStudio/).

    Non è possibile completare questa esercitazione Usa un'installazione generica di RStudio o un altro ambiente; è inoltre necessario installare i pacchetti R e librerie di connettività per Microsoft R Open. Per altre informazioni, vedere [Configurare un client per l'analisi scientifica dei dati](../r/set-up-a-data-science-client.md).

- Strumenti di base di R (R.exe, RTerm.exe, RScripts.exe) vengono installati per impostazione predefinita anche quando si installa R in SQL Server o Client di R. Se non si desidera installare un IDE, è possibile utilizzare questi strumenti.

## <a name="get-permissions-on-the-sql-server-instance-and-database"></a>Ottenere le autorizzazioni per l'istanza di SQL Server e database

Per connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire gli script e caricare i dati, è necessario disporre di un account di accesso valido nel server di database.  È possibile usare un account di accesso SQL o un'autenticazione integrata di Windows. Chiedere all'amministratore di database per configurare le autorizzazioni seguenti per l'account, nel database in cui si usano r:

- Creare database, tabelle, funzioni e stored procedure
- Scrivere dati nelle tabelle
- Possibilità di eseguire script R (`GRANT EXECUTE ANY EXTERNAL SCRIPT to <user>`)

Questa procedura dettagliata, abbiamo utilizzato l'account di accesso SQL **RTestUser**. È consigliabile in genere si utilizza l'autenticazione integrata di Windows, ma utilizzando l'account di accesso SQL è più semplice per alcuni scopi dimostrativi.

## <a name="change-list"></a>Elenco delle modifiche

+ In questo esempio è stato sviluppato utilizzando SQL Server 2016 R Services. Tuttavia, modifiche di rilievo introdotte nei componenti di Microsoft R per 2016 SP1. In particolare, il _varsToDrop_ e _varsToKeep_ parametri non sono supportati per le origini dati di SQL Server. Therefre, se è stata scaricata una versione dell'esercitazione precedente a SP1, non funzionerà con le compilazioni a SP1.

+ La versione corrente dell'esempio è stata testata mediante una build di versione non definitiva di SQL Server 2017 Machine Learning Services (RC1 e RC2). In generale, quasi tutti i passaggi devono essere eseguite senza modifica tra 2016 SP1 e 2017.

## <a name="next-lesson"></a>Lezione successiva

[Preparare i dati di utilizzo di PowerShell](walkthrough-prepare-the-data.md)
