---
title: "Interoperabilità di Python con SQL Server | Documenti Microsoft"
ms.custom: 
ms.date: 11/03/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: ee7187d490c8da80c66fb27156b2726e71782238
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="python-interoperability-with-sql-server"></a>Interoperabilità di Python con SQL Server

In questo argomento vengono descritti i componenti di Python che vengono installati se si abilita la funzionalità **Machine Learning Services (In-Database)** e selezionare il linguaggio Python.

## <a name="python-components"></a>Componenti di Python

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]non modifica i file eseguibili di Python. Il runtime di Python è installato in modo indipendente da strumenti di SQL e viene eseguito all'esterno del [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] processo.

La distribuzione che è associata a uno specifico [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] istanza è reperibile nella cartella associata all'istanza.

Ad esempio, se è installato Servizi di Machine Learning con l'opzione di Python nell'istanza predefinita, cercare in:

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

Installazione di SQL Server 2017 Machine Learning Services aggiunge la distribuzione Anaconda di Python. In particolare, vengono utilizzati i programmi di installazione 3 Anaconda, basato sul ramo Anaconda 4.3. Il livello previsto di Python per SQL Server 2017 è 3.5 Python.

## <a name="new-python-packages-in-this-release"></a>Nuovi pacchetti Python in questa versione

Per un elenco di pacchetti supportati dalla distribuzione Anaconda, visitare il sito di analitica Continuum: [l'elenco dei pacchetti Anaconda](https://docs.continuum.io/anaconda/pkg-docs)

Machine Learning Services in SQL Server 2017 include anche il nuovo **revoscalepy** libreria per Python.

La libreria fornisce funzionalità equivalenti a quelle del **RevoScaleR** pacchetto per R. Microsoft In altre parole, supporta la creazione di contesti di calcolo remoto, nonché i vari modelli di apprendimento scalabile di macchine, ad esempio **rxLinMod**. Per ulteriori informazioni su RevoScaleR, vedere [distribuita e l'elaborazione in parallelo con ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing).

Il [microsoftml per Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) pacchetto viene installato come parte di SQL Server Machine Learning, quando si aggiunge Python per l'installazione. Questo pacchetto contiene molti algoritmi di machine learning che sono stati ottimizzati per velocità e precisione, nonché le trasformazioni per l'utilizzo di testo e immagini in linea. Per informazioni dettagliate, vedere [mediante il pacchetto MicrosoftML con SQL Server](https://docs.microsoft.com/sql/advanced-analytics/using-the-microsoftml-package).

Microsoftml e revoscalepy sono strettamente collegate; origini dati utilizzate nella microsoftml sono definite come oggetti revoscalepy. Limitazioni di contesto nel trasferimento revoscalepy microsoftml di calcolo. In particolare, tutte le funzionalità sono disponibili per le operazioni locale, ma il passaggio a un contesto di calcolo remoto richiede RxInSqlServer.

## <a name="using-python-in-sql-server"></a>Utilizzo di Python in SQL Server

Importare il **revoscalepy** modulo in cui il codice Python e quindi chiamare funzioni del modulo, come le altre funzioni di Python.

Dati di input per Python devono essere in formato tabulare. Tutti i risultati di Python devono essere restituiti in forma di un **pandas** frame di dati.

È possibile eseguire il codice Python all'interno di T-SQL, incorporando lo script in una stored procedure.

In alternativa, eseguire il codice da un locale dell'IDE Python e includere lo script eseguito nel computer SQL Server, mediante la definizione di un contesto di calcolo remoto.

Si può lavorare con dati locali, ottenere dati da SQL Server o altre origini dati ODBC o usare il formato del file con estensione XDF per scambiare dati con altre origini, o con soluzioni R.

**Per ulteriori informazioni**

+ Funzionalità supportate: [novità revoscalepy](what-is-revoscalepy.md) 
+ Tipi di dati di Python supportati: [Python librerie e tipi di dati](python-libraries-and-data-types.md)
+ Origini dati supportate: ODBC database, SQL Server e i file con estensione XDF
+ Contesti di calcolo è supportato: locale o SQL Server

### <a name="licensing"></a>Gestione delle licenze

Come parte dell'installazione di servizi di Machine Learning con Python, è necessario consentire le condizioni di licenza GNU Public License.

## <a name="see-also"></a>Vedere anche

[Librerie e tipi di dati Python](python-libraries-and-data-types.md)
