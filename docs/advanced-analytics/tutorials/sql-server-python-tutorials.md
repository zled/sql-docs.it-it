---
title: Esercitazioni di SQL Server Python | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5cafb253cea118148bd654ea770234843f742838
ms.sourcegitcommit: b1990ec4491b5a8097c3675334009cb2876673ef
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2018
ms.locfileid: "49383336"
---
# <a name="sql-server-python-tutorials"></a>Esercitazioni di SQL Server Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fornisce un elenco di esercitazioni ed esempi che illustrano l'uso di Python con SQL Server 2017. Tramite questi esempi e demo, si apprenderà:

+ Come eseguire Python da T-SQL
+ Che cosa sono i contesti di calcolo remoti e locali e come è possibile eseguire codice Python usando il computer SQL Server
+ Come eseguire il wrapping di codice Python in una stored procedure
+ Ottimizzazione del codice Python per un ambiente di produzione di SQL
+ Scenari reali per l'incorporamento nelle applicazioni di apprendimento automatico

Per informazioni sui requisiti e il programma di installazione, vedere [prerequisiti](#bkmk_Prerequisites).

## <a name="bkmk_pythontutorials"></a>Esercitazioni su Python

+ [Esecuzione di Python in T-SQL](run-python-using-t-sql.md)

   Informazioni di base di come chiamare Python in T-SQL, mediante il meccanismo di estendibilità introdotti in SQL Server 2016.

+ [Creare un modello di machine learning in Python usando revoscalepy](use-python-revoscalepy-to-create-model.md)

   In questa lezione viene illustrato come è possibile eseguire codice da un terminale Python remoto usando il contesto di calcolo di SQL Server. Verrà visualizzata una certa familiarità con gli ambienti e gli strumenti Python. Codice di esempio viene specificato che crea un modello utilizzando **rxLinMod**, dalla nuova **revoscalepy** libreria. 

+ [Analitica di Python nel Database per sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md)

    Questa procedura dettagliata end-to-end viene illustrato il processo di compilazione di una soluzione completa di Python tramite le procedure di T-SQL archiviate. Tutto il codice Python è incluso.


## <a name="python-samples"></a>Esempi di Python

Questi esempi e demo fornite dal team di sviluppo di SQL Server evidenziano che modo è possibile usare analitica incorporata in applicazioni reali.

+ [Creare un modello predittivo usando Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  Informazioni su come un noleggio di sci potrebbe usare machine learning per prevedere i noleggi futuri, che consente al piano aziendale e personale per soddisfare la domanda futura.

  > [!TIP]
  > Include ora l'assegnazione dei punteggi nativa da modelli di Python.

+ [Clienti di eseguire il clustering con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Informazioni su come usare l'algoritmo Kmeans per eseguire il clustering non supervisionato dei clienti.

## <a name="see-also"></a>Vedere anche

[Esercitazioni di R per SQL Server](sql-server-r-tutorials.md)
