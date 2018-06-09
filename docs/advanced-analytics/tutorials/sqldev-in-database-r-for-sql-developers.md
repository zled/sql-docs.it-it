---
title: Esercitazione di analitica R incorporata per gli sviluppatori di SQL Server Machine Learning | Documenti Microsoft
description: Esercitazione che illustra come incorporare R in SQL Server funzioni e stored procedure T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3d2b77d73bb1b8f5d4c507b884d0a09f4647012b
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2018
ms.locfileid: "35250024"
---
# <a name="tutorial-embedded-r-in-stored-procedures-and-t-sql-functions"></a>Esercitazione: Incorporato R nelle stored procedure e funzioni di T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L'obiettivo di questa esercitazione è fornire ai programmatori SQL con la creazione di un di machine learning soluzioni in SQL Server. In questa esercitazione verrà illustrato come incorporare R in un'applicazione o di una soluzione di Business Intelligence eseguendo il wrapping di codice R nelle stored procedure.

> [!NOTE]
> 
> Nella stessa soluzione è disponibile in Python. SQL Server 2017 è obbligatorio. Vedere [analitica nel database per gli sviluppatori di Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>Panoramica

Il processo di creazione di una soluzione end-to-end normalmente consiste in attività di acquisizione e pulizia dei dati, esplorazione dei dati e progettazione di funzionalità, training e ottimizzazione del modello e infine distribuzione del modello nell'ambiente di produzione. Sviluppo e test del codice effettivo viene più eseguita utilizzando un ambiente di sviluppo dedicato. Per R, che potrebbe indicare RStudio o [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)].

Dopo la creazione della soluzione, tuttavia è possibile distribuirla facilmente a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando le stored procedure di [!INCLUDE[tsql](../../includes/tsql-md.md)] nell'ambiente familiare di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

In questa esercitazione si presuppone che è stato assegnato tutto il codice R necessario per la soluzione e lo stato attivo sulla compilazione e distribuzione della soluzione Usa SQL Server.

- [Lezione 1: Scaricare i dati di esempio e gli script](../tutorials/sqldev-download-the-sample-data.md)

- [Lezione 2: Configurare l'ambiente dell'esercitazione](../r/sqldev-import-data-to-sql-server-using-powershell.md)

- [Lezione 3: Esplorare e visualizzare forma dei dati e la distribuzione tramite la chiamata di funzioni R nelle stored procedure](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Lezione 4: Creare le funzionalità di dati usando R nelle funzioni di T-SQL](../tutorials/sqldev-create-data-features-using-t-sql.md)
  
- [Lezione 5: Eseguire il training e salvare un modello R tramite stored procedure e funzioni](../r/sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Lezione 6: Codice di incapsulamento R in una stored procedure per rendere operativo il](../tutorials/sqldev-operationalize-the-model.md). 
  Dopo aver salvato il modello per il database, chiamare il modello per la stima da [!INCLUDE[tsql](../../includes/tsql-md.md)] usando le stored procedure.

## <a name="scenario"></a>Scenario

Questa esercitazione viene utilizzato un noto pubblica set di dati in base a trip nei taxi New York city. Per eseguire il codice di esempio più velocemente, è stato creato un campione rappresentativo di % 1 dei dati. Utilizzare questi dati per compilare un modello di classificazione binaria che consente di stimare se un particolare trip è probabile che ottenere un suggerimento o non, in base alle colonne, ad esempio l'ora del giorno, distanza e posizione ritiro.

## <a name="requirements"></a>Requisiti

Questa esercitazione si presuppone una certa familiarità con le operazioni di database basic, ad esempio la creazione di tabelle e database, l'importazione di dati e la scrittura di query SQL. Presuppone che una conoscenza di R. Di conseguenza, tutto il codice R viene fornito. Un programmatore SQL esperto potrebbe essere possibile usare uno script di PowerShell fornito, dati di esempio in GitHub, e [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per completare questo esempio. 

Prima di iniziare l'esercitazione:

- Verificare disporre di un'istanza configurata di [R Services di SQL Server 2016](../install/sql-r-services-windows-install.md#verify-installation) oppure [servizi SQL Server 2017 Machine Learning con R abilitato](../install/sql-machine-learning-services-windows-install.md#verify-installation). Inoltre, [confermare di avere librerie R](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).
- L'account di accesso utilizzato per questa esercitazione è necessario disporre delle autorizzazioni per creare database e altri oggetti, per caricare i dati, selezionano i dati, eseguono le stored procedure.

> [!NOTE]
> È consigliabile effettuare **non** utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per scrivere o testare il codice R. Se il codice che viene incorporato in una stored procedure è presenti eventuali problemi, le informazioni che viene restituite dalla stored procedure sono in genere sufficienti per individuare la causa dell'errore.
> 
> Per il debug, si consiglia di usare uno strumento come [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)], o RStudio. Gli script R contenuti in questa esercitazione sono già stati sviluppati e sottoposti a debug usando gli strumenti tradizionali di R.

## <a name="next-lesson"></a>Lezione successiva

[Lezione 1: Scaricare i dati di esempio](../tutorials/sqldev-download-the-sample-data.md)
