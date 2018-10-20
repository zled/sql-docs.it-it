---
title: Esercitazione per analitica nel database con R e SQL Server Machine Learning | Microsoft Docs
description: Esercitazione che illustra come incorporare R in SQL Server stored procedure e funzioni T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 651e529bf0aa4cd4b4fab7e292e570dbb78e89d5
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461887"
---
# <a name="tutorial-learn-in-database-analytics-using-r-in-sql-server"></a>: Esercitazione analitica nel database con R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa esercitazione per programmatori SQL indicazioni ottenere esperienza pratica con il linguaggio R per compilare e distribuire una soluzione di machine learning eseguendo il wrapping di codice R nelle stored procedure.

Questa esercitazione Usa un noto set di dati pubblico, basata corse in taxi di New York City. Per rendere più rapido eseguire il codice di esempio, è stato creato un campione rappresentativo di % 1 dei dati. Si userà i dati per compilare un modello di classificazione binaria che consente di prevedere se una corsa specifica è tassista riceverà una Mancia o No, in base alle colonne come ora del giorno, distanza e località di partenza.

> [!NOTE]
> 
> La stessa soluzione è disponibile in Python. SQL Server 2017 è obbligatorio. Vedere [analitica nel database per sviluppatori Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>Panoramica

Il processo di compilazione in genere una soluzione end-to-end è costituito da acquisizione e pulizia dei dati, esplorazione dei dati e progettazione di funzionalità, training del modello e l'ottimizzazione e infine distribuzione del modello nell'ambiente di produzione. Sviluppo e test del codice effettivo è opportuno usare un ambiente di sviluppo dedicato. Per R, che potrebbe indicare RStudio o [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)].

Dopo la creazione della soluzione, tuttavia è possibile distribuirla facilmente a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando le stored procedure di [!INCLUDE[tsql](../../includes/tsql-md.md)] nell'ambiente familiare di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

- [Configurare il database dei Taxi di NYC](demo-data-nyctaxi-in-sql.md)

- [Lezione 1: Esplorare e visualizzare la forma dei dati e la distribuzione tramite la chiamata di funzioni R nelle stored procedure](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Lezione 2: Creare funzionalità di dati con R in T-SQL, funzioni](sqldev-create-data-features-using-t-sql.md)
  
- [Lezione 3: Eseguire il training e salvataggio di un modello R tramite stored procedure e funzioni](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Lezione 4: Codice incapsulamento R in una stored procedure per l'operazionalizzazione](../tutorials/sqldev-operationalize-the-model.md). 
  Dopo aver salvato il modello per il database, chiamare il modello per la stima da [!INCLUDE[tsql](../../includes/tsql-md.md)] usando le stored procedure.

## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione presuppone la conoscenza delle operazioni di base dei database, ad esempio la creazione di tabelle e database, l'importazione di dati e la scrittura di query SQL. Presuppone che una conoscenza di R. Di conseguenza, viene fornito tutto il codice R. Un programmatore SQL esperto può usare uno script di PowerShell fornito, i dati di esempio su GitHub, e [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per completare questo esempio. 

Prima di iniziare l'esercitazione:

- Verificare disporre di un'istanza configurata di [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) oppure [SQL Server 2017 Machine Learning Services con abilitato R](../install/sql-machine-learning-services-windows-install.md#verify-installation). È inoltre [confermare di avere le librerie R](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).
- L'account di accesso usato per questa esercitazione è necessario disporre delle autorizzazioni per creare i database e altri oggetti, per caricare i dati, selezionano i dati ed eseguono stored procedure.

> [!NOTE]
> È consigliabile effettuare **non** usare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per scrivere o testare il codice R. Se il codice che viene incorporato in una stored procedure è presenti eventuali problemi, le informazioni restituite dalla stored procedure sono in genere sufficienti per comprendere la causa dell'errore.
> 
> Per eseguire il debug, è consigliabile usare uno strumento, ad esempio [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)], o RStudio. Gli script R contenuti in questa esercitazione sono già stati sviluppati e sottoposti a debug usando gli strumenti tradizionali di R.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Configurare il database dei Taxi di NYC](demo-data-nyctaxi-in-sql.md)