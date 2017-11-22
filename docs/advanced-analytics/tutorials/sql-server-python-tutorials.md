---
title: Esercitazioni di SQL Server Python | Documenti Microsoft
ms.custom: SQL2016_New_Updated
ms.date: 09/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2017
dev_langs: Python
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: 70b2ada0c6b2cade444af1f7dde67f0adfd90b35
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-python-tutorials"></a>Esercitazioni di SQL Server Python

Questo articolo fornisce un elenco di esercitazioni ed esempi che illustrano l'utilizzo di Python con SQL Server 2017. Attraverso questi esempi e demo, si apprenderà:

+ Come eseguire Python da T-SQL
+ Che cosa sono i contesti di calcolo remoti e locali, e come è possibile eseguire il codice Python utilizzando il computer SQL Server
+ Come eseguire il wrapping di codice Python in una stored procedure
+ Ottimizzazione del codice Python per un ambiente di produzione di SQL
+ Scenari reali per l'incorporamento di apprendimento nelle applicazioni

Per informazioni sui requisiti e il programma di installazione, vedere [prerequisiti](#bkmk_Prerequisites).

## <a name="bkmk_pythontutorials"></a>Esercitazioni di Python

+ [Python in esecuzione in T-SQL](run-python-using-t-sql.md)

   Le informazioni di base di come chiamare Python in T-SQL, mediante il meccanismo di extensibility proposto per volta ha in SQL Server 2016.

+ [Creare un modello di machine learning in Python mediante revoscalepy](use-python-revoscalepy-to-create-model.md)

   Si creerà un modello utilizzando **rxLinMod**, dalla nuova **revoscalepy** libreria. Si verrà avvia il codice da un terminale di Python remoto, ma la modellazione avrà luogo nel contesto di calcolo di SQL Server.

+ [Analitica Python nel Database per gli sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md)

  NUOVO! Creare una soluzione completa di Python utilizzando T-stored procedure SQL. Tutto il codice Python è incluso.

+ [Distribuire e utilizzare un modello di Python](..\python\publish-consume-python-code.md)

  Informazioni su come distribuire un modello di Python usando la versione più recente di Microsoft Machine Learning Server.

## <a name="python-samples"></a>Esempi di Python

Questi esempi e demo fornite dal team di sviluppo di SQL Server evidenziano modi che è possibile utilizzare analitica incorporati nelle applicazioni reali.

+ [Compilare un modello predittivo con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  Informazioni su come una società di noleggio ski potrebbe utilizzare machine learning per stimare il noleggio di futuro, che consente al piano aziendale e personale per rispondere alla domanda futura.

  > [!TIP]
  > Include ora il punteggio nativo dai modelli di Python!

+ [Clienti di eseguire il clustering con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Informazioni su come utilizzare l'algoritmo Kmeans per eseguire il clustering non supervisionato dei clienti.

## <a name="bkmk_Prerequisites"></a>Prerequisiti

Per utilizzare queste esercitazioni, è necessario avere installato SQL Server 2017 Machine Learning Services (In-Database). SQL Server 2017 supporta R o Python. Tuttavia, è necessario installare il framework di estendibilità che supporta l'apprendimento e selezionare Python come lingua da installare. È possibile installare R sia Python nello stesso computer.

> [!NOTE]
>
> Supporto per Python è una nuova funzionalità di SQL Server 2017 e richiede la versione CTP 2.0 o versione successiva. Anche se la funzionalità è preliminare e non è supportato per gli ambienti di produzione, la invitiamo a provarlo e inviare commenti e suggerimenti.

**SQL Server 2017**

Dopo l'installazione di SQL Server, non dimenticare questi passaggi importanti:

+ Abilitare la funzionalità di esecuzione di script esterni eseguendo `sp_configure 'external scripts enabled', 1`.
+ Riavviare il server.
+ Verificare che il servizio che chiama il runtime esterno disponga delle autorizzazioni necessarie.
+ Verificare che l'account di accesso SQL o un account utente di Windows disponga delle autorizzazioni necessarie per connettersi al server, per leggere i dati e creare oggetti di database necessari dall'esempio.

Se si verificano problemi, vedere questo articolo per alcuni problemi comuni: [risoluzione dei problemi di Machine Learning Services](../machine-learning-troubleshooting-faq.md)

## <a name="see-also"></a>Vedere anche

[Esercitazioni di R per SQL Server](sql-server-r-tutorials.md)
