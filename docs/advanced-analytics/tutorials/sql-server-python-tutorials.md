---
title: Esercitazioni di SQL Server Python | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c99e5605dad537fddef20fbd091a61cc4e711471
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31201943"
---
# <a name="sql-server-python-tutorials"></a>Esercitazioni di SQL Server Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

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

   Questa lezione viene illustrato come è possibile eseguire codice da un terminale di Python remoto, utilizzando il contesto di calcolo di SQL Server. È necessario una certa familiarità con gli ambienti e strumenti Python. Codice di esempio viene specificato che crea un modello utilizzando **rxLinMod**, dalla nuova **revoscalepy** libreria. 

+ [Analitica Python nel Database per gli sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md)

    Questa procedura dettagliata end-to-end viene illustrato il processo di compilazione di una soluzione completa di Python utilizzando T-stored procedure SQL. Tutto il codice Python è incluso.


## <a name="python-samples"></a>Esempi di Python

Questi esempi e demo fornite dal team di sviluppo di SQL Server evidenziano modi che è possibile utilizzare analitica incorporati nelle applicazioni reali.

+ [Compilare un modello predittivo con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  Informazioni su come una società di noleggio ski potrebbe utilizzare machine learning per stimare il noleggio di futuro, che consente al piano aziendale e personale per rispondere alla domanda futura.

  > [!TIP]
  > Include ora il punteggio nativo dai modelli di Python!

+ [Clienti di eseguire il clustering con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Informazioni su come utilizzare l'algoritmo Kmeans per eseguire il clustering non supervisionato dei clienti.

## <a name="bkmk_Prerequisites"></a>Prerequisiti

Per utilizzare queste esercitazioni, è necessario disporre di SQL Server 2017 e, è necessario installare in modo esplicito e quindi abilitare la funzionalità, servizi di Machine Learning (In-Database). 

SQL Server 2017 supporta lingue R e Python, ma non è installato o abilitato per impostazione predefinita. L'esecuzione di Python richiede che il framework di estendibilità sia attivato e che si seleziona Python come lingua da installare. 

### <a name="post-installation-configuration-tips"></a>Suggerimenti relativi alla configurazione post-installazione

Dopo l'installazione di SQL Server, potrebbe essere necessario eseguire alcuni passaggi aggiuntivi per assicurarsi che comunichino Python e SQL Server:

+ Abilitare la funzionalità di esecuzione di script esterni eseguendo `sp_configure 'external scripts enabled', 1`.
+ Riavviare il server. 
+ Aprire il **servizi** pannello per verificare se è stata avviata Launchpad. 
+ Verificare che il servizio che chiama il runtime esterno disponga delle autorizzazioni necessarie. Per ulteriori informazioni, vedere [abilitare l'autenticazione implicita](../r/add-sqlrusergroup-to-database.md).
+ Aprire una porta nel firewall per SQL Server e abilitare i protocolli di rete necessari.
+ Verificare che l'account di accesso SQL o un account utente di Windows disponga delle autorizzazioni necessarie per connettersi al server, per leggere i dati e creare oggetti di database necessari dall'esempio.

Vedere questo articolo per alcuni problemi comuni: [risoluzione dei problemi di Machine Learning Services](../machine-learning-troubleshooting-faq.md)

### <a name="resource-management"></a>Gestione delle risorse

È possibile installare R sia Python nello stesso computer, ma l'esecuzione sia può richiedere notevoli risorse. Se si verificano errori di "memoria esaurita" o se l'esecuzione di processi di machine learning è che il principale utilizzo previsto di server, è possibile ridurre la quantità di memoria allocata al motore di database. Per ulteriori informazioni, vedere [la gestione e monitoraggio Python in SQL Server](../python/managing-and-monitoring-python-solutions.md).

## <a name="see-also"></a>Vedere anche

[Esercitazioni di R per SQL Server](sql-server-r-tutorials.md)
