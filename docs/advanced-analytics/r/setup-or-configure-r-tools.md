---
title: Strumenti di R inclusi con l'installazione di SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 8178f4a1347ef58fd7ee143fbe843e3525ac4cf0
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="r-tools-included-with-sql-server-setup"></a>Strumenti di R inclusi con l'installazione di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Quando si installa R con SQL Server, si ottengono gli stessi strumenti R che vengono installati con qualsiasi **base** installazione di R, ad esempio RGui, Rterm e così via. Tecnicamente, si disporrebbe tutti gli strumenti che necessari per sviluppare e testare il codice R.

In questo argomento sono elencati gli strumenti inclusi con l'installazione.

> [!TIP]
> 
> In genere è più facile eseguire il debug e testare il codice R usando un ambiente di sviluppo dedicato. Sono disponibili più semplice eseguire il codice R in SQL Server, se il testing in anticipo in uno strumento esterno, in modo che è possibile leggere i messaggi di errore dettagliato e il debug della soluzione.
> 
> Vedere l'articolo per un elenco di strumenti gratuiti che è possibile utilizzare per lo sviluppo di soluzioni R e come configurarli per l'utilizzo di SQL Server: [configurare un client di analisi scientifica dei dati](set-up-a-data-science-client.md)

**Si applica a:** SQL Server 2016 R Services (In-Database) e Microsoft R Server (Standalone); SQL Server 2017 Machine Learning Services (In-Database) e Machine Learning Server (Standalone)

## <a name="r-tools-included-with-installation"></a>Strumenti di R inclusi con l'installazione

Sono inclusi i seguenti strumenti standard di R in un *installazione di base* di R e pertanto vengono installati per impostazione predefinita.

+ **RTerm**: un terminale della riga di comando per l'esecuzione di script R

+ **RGui.exe**: semplice editor interattivo per R. Gli argomenti della riga di comando sono gli stessi di RGui.exe e RTerm.

+ **RScript**: strumento da riga di comando per l'esecuzione di script R in modalità batch.

Per individuare questi strumenti, determinare la raccolta di R che è stata installata quando si configura SQL Server o della macchina autonoma funzionalità di apprendimento. Ad esempio, in un'installazione predefinita, gli strumenti di R si trovano in queste cartelle:

+ SQL Server 2016 R Services: `~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`
+ Microsoft R Server autonomo:`~\Program Files\Microsoft R\R_SERVER\bin\x64`
+ SQL Server 2017 Machine Learning Services:`~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`
+ Machine Learning Server (Standalone):`~\Program Files\Microsoft\ML Server\R_SERVER\bin\x64`

Per assistenza con gli strumenti di R, aprire semplicemente **RGui**, fare clic su **Guida**e selezionare una delle opzioni.

## <a name="introducing-microsoft-r-client"></a>Introduzione a Microsoft R Client

Microsoft R è un download gratuito che consente di accedere ai pacchetti RevoScaleR per il processo di sviluppo. Installando il Client R, è possibile creare soluzioni R che possono essere eseguite in tutti i contesti di calcolo supportati, tra cui analitica nel database di SQL Server e R distribuite in Hadoop, Spark o Linux con Server di Machine Learning.

Se è già stato installato un ambiente di sviluppo R diverso, ad esempio RStudio, assicurarsi di riconfigurare l'ambiente per usare le librerie e file eseguibili forniti dal Client di Microsoft R. In questo modo è possibile utilizzare tutte le funzionalità del pacchetto RevoScaleR, anche se le prestazioni sarà limitata.

Per ulteriori informazioni, vedere [che cos'è Microsoft R Client?](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)
