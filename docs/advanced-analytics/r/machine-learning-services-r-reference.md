---
title: Riferimento API per servizi di SQL Server Machine Learning | Documenti Microsoft
ms.custom: 
ms.date: 10/31/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 52261d7ebb01ca4156d067ba0f25af3cd90a64bb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="api-reference-for-sql-server-machine-learning-services"></a>Riferimento API per servizi di SQL Server Machine Learning

Questo articolo fornisce collegamenti alla documentazione di riferimento per machine learning API utilizzate da SQL Server.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

La maggior parte, SQL Server utilizza le stesse librerie R e Python disponibili in Microsoft R Server e Server di Microsoft Machine Learning. 

> [!NOTE]
> Documentazione relativa a tutte le API deriva da codice sorgente e non è stata modificata. Se si verificano errori, aggiungere un commento nella documentazione di riferimento dell'API. 

## <a name="r"></a>L

+ [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)

    Algoritmi scalabili che supportano i contesti di calcolo remoti e di più origini dati.

+ [MicrosoftML](https://docs.microsoft.com/machine-learning-serverr-reference/microsoftml/microsoftml-package)

    Apprendimento delle trasformazioni e gli algoritmi per R. richiede RevoScaleR automatico veloce e scalabile.

+ [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr)

   Legge lo schema di origini dei dati OLAP e vengono eseguite query MDX.

+ [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)

    Funzioni di supporto per la generazione di una stored procedure in formato corretto dal codice R.

+ [mrsdeploy](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)

   Funzioni per stabilire una sessione remota in un'applicazione console e per la pubblicazione e gestione di un servizio web che usa il codice R o Python.

## <a name="python"></a>Python

+ [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)

    Equivalente di Python del pacchetto RevoScaleR per il linguaggio R. Supporta le stesse origini dati e i contesti di calcolo.

+ [Microsoftml per Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)

    Equivalente di Python del MicrosoftML pacchetto per R. supporta le origini dati e i contesti di calcolo stesso e include veloce, scalabili algoritmi e le trasformazioni da Microsoft. 

## <a name="related-apis"></a>API correlate

+ [Riferimento alla funzione RevoPEMAR](https://docs.microsoft.com/machine-learning-server/r-reference/revopemar/pemar)

    Supporta lo sviluppo di algoritmi paralleli

+ [RevoUtils](https://docs.microsoft.com/machine-learning-server/r-reference/revoutils/revoutils)

    Funzioni di utilità per l'utilizzo con gli ambienti RevoScaleR

## <a name="other"></a>Altro

"Procedure" e riepiloghi specifici per l'utilizzo di queste R o le API di Python in SQL Server sono disponibili qui:

+ [Funzioni scaleR per l'utilizzo di SQL Server](scaler-functions-for-working-with-sql-server-data.md)
+ [Generare una stored procedure utilizzando sqlrutils](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
+ [Lettura dati MDX in R tramite olapR](how-to-create-mdx-queries-using-olapr.md)
