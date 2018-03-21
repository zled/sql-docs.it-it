---
title: Prerequisiti per la procedura dettagliata dell'analisi scientifica dei dati per SQL Server e R | Documenti Microsoft
ms.date: 11/10/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 0b0582b8-8843-4787-94a8-2e28bdc04fb2
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 35738101548f3b0790131c8106bb37e482cc7316
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="prerequisites-for-the-data-science-walkthrough-for-sql-server-and-r"></a>Prerequisiti per la procedura dettagliata dell'analisi scientifica dei dati per SQL Server e R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Si consiglia di seguire questa procedura dettagliata su un computer portatile o un altro computer con le librerie di Microsoft R installate. È necessario essere in grado di connettersi, nella stessa rete, a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer con servizi di machine learning e il linguaggio R abilitato.

È possibile eseguire la procedura dettagliata in un computer che includa entrambi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un ambiente di sviluppo di R, ma si sconsiglia di questa configurazione per un ambiente di produzione.

## <a name="install-machine-learning-for-sql-server"></a>Apprendimento di installazione per SQL Server

È necessario avere accesso a un'istanza di SQL Server con il supporto per R installato. Questa procedura dettagliata è stato originariamente sviluppata per SQL Server 2016 e testata su 2017, pertanto dovrebbe essere in grado di utilizzare una delle seguenti versioni di SQL Server. (Esistono alcune piccole differenze delle funzioni RevoScaleR tra le versioni.)

+ Per SQL Server 2017 di Machine Learning Services (In-Database)
+ SQL Server 2016 R Services

Per altre informazioni, vedere [installare SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) oppure [installare SQL Server 2016 R Services](../install/sql-r-services-windows-install.md).

> [!IMPORTANT]
> Versioni di SQL Server precedenti rispetto a 2016 non supportano l'integrazione con R. Tuttavia, è possibile utilizzare i database SQL precedente come un'origine dati ODBC.

## <a name="install-an-r-development-environment"></a>Installare un ambiente di sviluppo di R

Questa procedura dettagliata, è consigliabile utilizzare un ambiente di sviluppo R. Di seguito sono riportati alcuni suggerimenti:

- **Strumenti R per Visual Studio** (RTVS) è un plug-in che fornisce Intellisense, debug e il supporto per Microsoft R. È possibile utilizzare con R Server e servizi di SQL Server Machine Learning. Per scaricarlo, vedere [R Tools per Visual Studio](https://www.visualstudio.com/vs/rtvs/).

- **Microsoft R Client** è uno strumento di sviluppo leggero che supporta lo sviluppo di R usando il pacchetto RevoScaleR. Per ottenerlo, vedere [Introduzione a Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client).

- **RStudio** è uno degli ambienti più diffusi per lo sviluppo di R. Per ulteriori informazioni, vedere [ https://www.rstudio.com/products/RStudio/ ](https://www.rstudio.com/products/RStudio/).

    Non è possibile completare questa esercitazione Usa un'installazione generica di RStudio o un altro ambiente; è inoltre necessario installare i pacchetti R e librerie di connettività per Microsoft R Open. Per altre informazioni, vedere [Configurare un client per l'analisi scientifica dei dati](../r/set-up-a-data-science-client.md).

- Strumenti di base di R (R.exe, RTerm.exe, RScripts.exe) vengono installati per impostazione predefinita anche quando si installa R in SQL Server o Client di R. Se non si desidera installare un IDE, è possibile utilizzare questi strumenti.

## <a name="get-permissions-on-the-sql-server-instance-and-database"></a>Ottenere le autorizzazioni per l'istanza di SQL Server e database

Per connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire gli script e caricare i dati, è necessario un account di accesso valido nel server di database.  È possibile usare un account di accesso SQL o un'autenticazione integrata di Windows. Chiedere all'amministratore del database per configurare le seguenti autorizzazioni per l'account, nel database in cui si usano r:

- Creare database, tabelle, funzioni e stored procedure
- Scrivere dati nelle tabelle
- Possibilità di eseguire script R (`GRANT EXECUTE ANY EXTERNAL SCRIPT to <user>`)

Questa procedura dettagliata, è stata usata l'account di accesso SQL **RTestUser**. In genere è consigliabile che si utilizza l'autenticazione integrata di Windows, ma l'account di accesso di SQL è più semplice per alcune finalità demo.

## <a name="change-list"></a>Elenco delle modifiche

+ In questo esempio è stato originariamente sviluppato utilizzando SQL Server 2016 R Services. Tuttavia, modifiche di rilievo introdotte nei componenti di Microsoft R per 2016 SP1. In particolare, il _varsToDrop_ e _varsToKeep_ parametri non erano supportati per le origini dati di SQL Server. Therefre, se è stata scaricata una versione dell'esercitazione precedente a SP1, non funzionerà più con le compilazioni a SP1.

+ La versione corrente dell'esempio è stata testata mediante una build di versione non definitiva di SQL Server 2017 Machine Learning Services (RC1 e RC2). In generale, quasi tutti i passaggi devono essere eseguite senza modifica tra 2016 SP1 e 2017.

## <a name="next-lesson"></a>Lezione successiva

[Preparare i dati di utilizzo di PowerShell](/walkthrough-prepare-the-data.md)
