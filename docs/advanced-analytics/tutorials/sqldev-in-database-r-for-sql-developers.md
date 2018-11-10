---
title: Esercitazione per analitica nel database con R e SQL Server Machine Learning | Microsoft Docs
description: Informazioni su come incorporare il codice lingua nella stored procedure SQL Server e funzioni T-SQL di programmazione R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 80c4d39e87984b022340079be4d944ed6ad963e3
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030648"
---
# <a name="tutorial-in-database-r-analytics-for-sql-developers"></a>: Esercitazione Analitica di R In-Database per sviluppatori SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa esercitazione per programmatori SQL indicazioni, informazioni sull'integrazione di R tramite la creazione e distribuzione di un computer basato su R imparando a usare soluzioni una [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) database in SQL Server. 

Questa esercitazione presenta funzioni R usate in un flusso di lavoro di modellazione dati. Passaggi includono l'esplorazione dei dati, creazione e training di un modello di classificazione binaria e la distribuzione del modello. Si userà i dati di esempio dei Taxi di New York City e Commission Limosine, e il modello che si compilerà consente di stimare se una corsa è probabile che risulterà in un suggerimento basato sull'ora del giorno, distanza percorsa e località di partenza. Tutto il codice R usato in questa esercitazione viene eseguito il wrapping nelle stored procedure da creare ed eseguire in Management Studio.


> [!NOTE]
> 
> Questa esercitazione è disponibile in R e Python. Per la versione di Python, vedere [analitica nel database per sviluppatori Python](../tutorials/sqldev-in-database-python-for-sql-developers.md).

## <a name="overview"></a>Panoramica

Il processo di creazione di una soluzione di apprendimento è complessa può includere più strumenti e il coordinamento di esperti in materia in diverse fasi:

+ acquisizione e pulizia dei dati
+ esaminando i dati e creazione di funzionalità utili per la modellazione
+ set di training e il modello di ottimizzazione
+ distribuzione nell'ambiente di produzione

Sviluppo e test del codice effettivo è opportuno usare un ambiente di sviluppo dedicato. Tuttavia, dopo che lo script è stato testato completamente, è possibile distribuire facilmente venga [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure nell'ambiente familiare di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Se si ha familiarità con R i programmatori SQL o è uno sviluppatore di R per SQL, questa esercitazione in più parti illustra un tipico flusso di lavoro di svolgere analitica nel database con R e SQL Server. 

- [Lezione 1: Esplorare e visualizzare la forma dei dati e la distribuzione tramite la chiamata di funzioni R nelle stored procedure](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Lezione 2: Creare funzionalità di dati con R in T-SQL, funzioni](sqldev-create-data-features-using-t-sql.md)
  
- [Lezione 3: Eseguire il training e salvataggio di un modello R tramite stored procedure e funzioni](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Lezione 4: Stimare i possibili risultati usando un modello R in una stored procedure](../tutorials/sqldev-operationalize-the-model.md)

Dopo aver salvato il modello al database, chiamare il modello per le stime da [!INCLUDE[tsql](../../includes/tsql-md.md)] utilizzando stored procedure.

## <a name="prerequisites"></a>Prerequisiti

Tutte le attività possono essere eseguite usando [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Questa esercitazione presuppone la conoscenza delle operazioni di base dei database, ad esempio la creazione di tabelle e database, l'importazione di dati e la scrittura di query SQL. Presuppone che una conoscenza di R. Di conseguenza, viene fornito tutto il codice R. 

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) o [servizi SQL Server 2017 Machine Learning con R abilitata](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Librerie di R](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location)

+ [Autorizzazioni](../security/user-permission.md)

+ [Database di esempio dei Taxi di NYC](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Configurare il database dei Taxi di NYC](demo-data-nyctaxi-in-sql.md)