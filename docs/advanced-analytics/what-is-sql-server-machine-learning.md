---
title: "Novità di servizi di SQL Server Machine Learning? | Microsoft Docs"
ms.date: 03/07/2018
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: 
ms.openlocfilehash: ccba60d0a3e0fe45f82215a045e53a265d6c0a92
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="what-is-sql-server-machine-learning-services"></a>Novità di servizi di SQL Server Machine Learning?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Servizi di SQL Server Machine Learning è un incorporato, predittivo analitica dati scienza motore e in grado di eseguire codice R e Python all'interno di un database di SQL Server come stored procedure, come script T-SQL che contiene istruzioni R o Python o R o Python contenenti codice T-SQL. 

La proposta di valore della chiave di servizi di Machine Learning è la potenza dei relativi pacchetti proprietari per il recapito analitica avanzate nella scalabilità e la possibilità di connettere i calcoli e l'elaborazione di dove risiedono i dati, eliminando la necessità di pull dei dati tra il rete.

Sono disponibili due opzioni per l'utilizzo di funzionalità di machine learning in SQL Server: 

+ [**SQL Server Machine Learning Services (In-Database)** ](r/sql-server-r-services.md) opera all'interno dell'istanza di motore di database, in cui il motore di calcolo è completamente integrato con il motore di database. La maggior parte delle installazioni sono questa opzione.
+ [**Machine Learning Server (Standalone) di SQL Server** ](r/r-server-standalone.md) è un'installazione non SQL. Anche se si utilizza il programma di installazione di SQL Server per installare il server, è completamente separata da SQL Server. A livello funzionale, equivale a non-SQL [Machine Learning per Windows di Microsoft Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

## <a name="r-and-python-packages"></a>Pacchetti R e Python

Il supporto per ogni lingua è tramite proprietari pacchetti Microsoft utilizzati per la creazione e al training di vario tipo, data e l'elaborazione parallela usando le risorse di sistema sottostante di punteggio.

Poiché i pacchetti proprietari si basano su distribuzioni di open source R e Python, script o codice che vengono eseguiti in SQL Server può anche chiamare le funzioni di base e utilizzare i pacchetti di terze parti compatibili con la versione di lingua disponibile in SQL Server (3.5 Python e versioni recenti di R, attualmente 3.3.3).

| L  | Python | Description |
|-----------|----------------|-------------|
| [RevoScaleR](r/revoscaler-overview.md) | [revoscalepy](python/what-is-revoscalepy.md)   | Funzioni queste librerie sono tra le più diffuse. Trasformazioni di dati e la modifica, riepilogo statistico, visualizzazione e molte forme di analisi e modellazione si trovano in queste librerie. Inoltre, le funzioni in queste librerie automaticamente distribuiscono i carichi di lavoro core disponibili per l'elaborazione parallela, con la possibilità di utilizzare blocchi di dati che vengono coordinati e gestiti dal motore di calcolo. |
| [MicrosoftML](using-the-microsoftml-package.md) | [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Leader del settore algoritmi di machine learning per immagine featurization, problemi di classificazione e altro ancora. |
| [olapR](r/how-to-create-mdx-queries-using-olapr.md) | none | Compilare o eseguire una query MDX in uno script R.
| [sqlRUtils](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md) | none | Funzioni per l'inserimento di script R in T-SQL stored procedure, la registrazione di una stored procedure con un database e l'esecuzione della stored procedure da un ambiente di sviluppo R.
| [mrsdeploy](operationalization-with-mrsdeploy.md) | none | Utilizzato principalmente in un'installazione non SQL di Machine Learning Server, ad esempio il [(Standalone) versione](r/r-server-standalone.md). Utilizzare questo pacchetto per distribuire e ospitare servizi web, creare topologie di scalabilità orizzontale con web dedicato e nodi di calcolo, passare tra le sessioni locali e remote, eseguire la diagnostica e altro ancora. Per un'installazione (In-Database), utilizzare il pacchetto in una capacità di client: ad esempio, per accedere a un servizio web in un server remoto dedicato all'esecuzione di carichi di lavoro Machine Learning Services solo. |

Portabilità del codice R e Python personalizzato è stato risolto tramite la distribuzione del pacchetto e interpreti incorporate in più prodotti. Gli stessi pacchetti forniti in SQL Server sono disponibili anche in diversi altri prodotti e servizi Microsoft, tra cui una versione non SQL denominata [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/). I client gratuiti che includono i nostri interpreti R e Pyton includono [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) e [librerie Python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter).

Sono inoltre disponibili in diverse pacchetti e interpreti [macchine virtuali di Azure](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-azure-vm-on-linux), Azure Machine Learning e servizi di Azure quali [HDInsight](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-on-azure-hdinsight). 


## <a name="use-cases"></a>Casi d'uso

**Analitica nel database**

Analisti e sviluppatori spesso dispongono di codice in esecuzione su un'istanza di SQL Server locale. Se si dispone, ad esempio SQL Server e un IDE [Visual Studio con R](https://docs.microsoft.com/visualstudio/rtvs/) o [Visual Studio con Python](https://docs.microsoft.com/visualstudio/python/installing-python-support-in-visual-studio) nello stesso computer, è possibile compilare, eseguire il training e testare i modelli in locale in entrambi i linguaggi. Accesso locale semplifica la gestione dei pacchetti: come amministratore, è possibile caricare i pacchetti di terze parti aggiuntivi utilizzando le autorizzazioni predefinite per tale ruolo.

L'approccio più comune per analitica nel database consiste nell'utilizzare [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) per eseguire script R o Python. Le esercitazioni elencate in [passaggi successivi](#next-steps) iniziare.

**Configurazioni client-server**

Da qualsiasi workstation client che ha un IDE, installare [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) o [librerie Python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)e quindi scrivere codice che inserisce l'esecuzione (detto un *il contesto di calcolo remoto*) per i dati e le operazioni a un Server SQL remoto. 

Analogamente, se si utilizza l'edizione Developer, è possibile compilare soluzioni in una workstation client utilizzando le stesse librerie e interpreti e quindi distribuire il codice di produzione su SQL Server Machine Learning Services (In-Database). 

## <a name="version-history"></a>Cronologia versioni

Servizi di SQL Server 2017 Machine Learning è la prossima generazione di SQL Server 2016 R Services migliorata per includere Python. Nella tabella seguente è un elenco completo di tutte le versioni, dall'inizio alla versione corrente. 

| Nome prodotto | Versione del motore | Data di rilascio |
|--------------|---------|--------------|
| SQL Server 2017 Machine Learning Services (In-Database) | R Server 9.2.1 <br/> Server di Python 9.2 | Ottobre 2017 |
| SQL Server 2017 Machine Learning Server (Standalone) | R Server 9.2.1 <br/> Server di Python 9.2 | Ottobre 2017 |
| SQL Server 2016 R Services (In-Database) | R Server 9.1  | 2017 luglio  |
| R Server (Standalone) di SQL Server 2016  |  R Server 9.1 | 2017 luglio |



## <a name="documentation-for-each-version"></a>Documentazione per ogni versione

Versioni recenti di documentazione di SQL Server sono indipendente dalla versione. Per SQL Server Machine Learning Services Python è disponibile solo in 2017 e versioni successive, mentre è il supporto di R in tutte le versioni. Se non specificato diversamente, si può presupporre documentazione R si applica alle versioni 2016 sia 2017.


## <a name="related-machine-learning-products"></a>Apprendimento prodotti correlato

 +  [Eseguire il provisioning di una macchina virtuale di Azure](r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)
  
  Azure marketplace include più immagini di macchine virtuali che includono Server Learning macchina o R Server. Creazione di una macchina virtuale in Microsoft Azure è il modo più rapido per ottenere lo sviluppo e la distribuzione dei modelli predittivi. Le immagini sono dotati di funzionalità per la scalabilità e la condivisione è già configurato, che rende più facile da incorporare analitica all'interno delle applicazioni e per l'integrazione con sistemi back-end.

+ [Macchina virtuale per operazioni di data science](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/)

  La versione più recente della macchina virtuale di analisi scientifica dei dati include il Machine Learning di SQL Server, e una matrice degli strumenti più comuni per machine learning, tutti preinstallato e testato. Creare Jupyter notebook, lo sviluppo di soluzioni in Julia e utilizzare le librerie abilitato GPU deep learning MXNet, CNTK e TensorFlow.

<a name="next-steps"></a>

## <a name="next-steps"></a>Passaggi successivi

**Passaggio 1:** installare e configurare il software. 

+ [Installare SQL Server 2017 Machine Learning Services (In-Database)](install/sql-machine-learning-services-windows-install.md)

**Passaggio 2:** iniziare con il codice mediante una di queste esercitazioni:

+ [Esercitazione: Esecuzione di Python in T-SQL](tutorials/run-python-using-t-sql.md)
+ [Esercitazione: Esecuzione di R in T-SQL](tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)

**Passaggio 3:** aggiungere i pacchetti R e Python Preferiti e utilizzarle insieme a pacchetti forniti da Microsoft

+ [Gestione dei pacchetti R per SQL Server](r/r-package-management-for-sql-server-r-services.md)