---
title: Installare i nuovi pacchetti Python in SQL Server | Documenti Microsoft
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 8509556cd886f90dbac2211bc0282e8656bdc03e
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="install-new-python-packages-on-sql-server"></a>Installare i nuovi pacchetti Python in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene descritto come installare i nuovi pacchetti Python in un'istanza di SQL Server 2017.

In generale, il processo per l'installazione di nuovi pacchetti è simile a quello in un ambiente standard di Python. Tuttavia, alcuni passaggi aggiuntivi sono necessari se il server non dispone di una connessione a internet.

Per informazioni sulla immaginando in cui sono installati i pacchetti o i pacchetti installati, vedere [visualizzazione installati pacchetti R o Python](../r/determine-which-packages-are-installed-on-sql-server.md).

## <a name="prerequisites"></a>Prerequisiti

+ È necessario avere installato Servizi di Machine Learning (In-Database) con l'opzione di linguaggio Python. Per istruzioni, vedere [installare SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-services-windows-install.md).

+ Per ogni istanza del server, è necessario installare una copia separata del pacchetto. Pacchetti non possono essere condivisi tra le istanze.

+ Determinare se il pacchetto che si intende utilizzare funzionerà con Python 3.5 e nell'ambiente di Windows. 

+ Valutare se il pacchetto è una scelta ottimale per l'utilizzo nell'ambiente di SQL Server. In genere un server di database supporta più servizi e applicazioni Web e le risorse nel file system potrebbero essere limitato, nonché le connessioni al server. In molti casi l'accesso a Internet è bloccato completamente.

    Altri problemi comuni includono l'utilizzo di funzionalità che è stata bloccata nel server o da firewall o i pacchetti con le dipendenze che non possono essere installate in un computer Windows di rete. 

    Alcuni pacchetti Python diffusi (ad esempio pallone) eseguono attività quali lo sviluppo web che eseguono migliori in un ambiente autonomo. È consigliabile utilizzare Python nel database per le attività, ad esempio machine learning, che richiedono l'elaborazione di dati con utilizzo intensivo che traggono vantaggio da una stretta integrazione con il motore di database, anziché semplicemente una query del database.

+ L'accesso amministrativo al server è necessario installare i pacchetti.

## <a name="add-a-new-python-package"></a>Aggiunge un nuovo pacchetto di Python

In questo esempio si presuppone che si desidera installare un nuovo pacchetto direttamente nel computer SQL Server.

Il pacchetto installato in questo esempio viene [CNTK](https://docs.microsoft.com/cognitive-toolkit/), un framework per la formazione di Microsoft che supporta la personalizzazione, set di training e la condivisione di tipi diversi di reti neurali.

> [!TIP]
> Serve aiuto per configurare gli strumenti Python? Vedere i blog:
> 
> [Introduzione a servizi Web di Python mediante Machine Learning Server](https://blogs.msdn.microsoft.com/mlserver/2017/12/13/getting-started-with-python-web-services-using-machine-learning-server/)
> 
> [David Crook: Microsoft cognitivi Toolkit + Visual Studio Code](http://dacrook.com/cntk-vs-code-awesome/)

### <a name="step-1-download-the-windows-version-of-the-python-package"></a>Passaggio 1. Scaricare la versione di Windows del pacchetto Python

+ Se si siano installando i pacchetti Python in un server senza accesso a internet, è necessario scaricare il file WHL in un computer diverso e quindi copiarlo nel server.

    In un computer separato, ad esempio, è possibile scaricare il file WHL da questo sito [ https://cntk.ai/PythonWheel/CPU-Only ](https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl), quindi copiare il file `cntk-2.1-cp35-cp35m-win_amd64.whl` in una cartella locale nel computer SQL Server.

+ SQL Server 2017 Usa Python 3.5. 

> [!IMPORTANT]
> Assicurarsi ottenere la versione di Windows del pacchetto. Se il file termina .gz, probabilmente non è la versione corretta.

Questa pagina contiene i download per più piattaforme e per più versioni di Python: [impostare CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="step-2-open-a-python-command-prompt"></a>Passaggio 2. Aprire un prompt dei comandi di Python

Individuare il percorso di libreria Python predefinito utilizzato da SQL Server. Se è stato installato più istanze, individuare la cartella PYTHON_SERVICE per l'istanza in cui si desidera aggiungere il pacchetto.

Ad esempio, se Machine Learning Services è stato installato utilizzando le impostazioni predefinite e apprendimento automatico è abilitato nell'istanza predefinita, il percorso sarà come segue:

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

Aprire il prompt dei comandi di Python associato all'istanza.

> [!TIP]
> Per future debug e test, si potrebbe voler impostare un ambiente di Python specifiche per la libreria di istanza.

### <a name="step-3-install-the-package-using-pip"></a>Passaggio 3. Installare il pacchetto mediante pip

+ Se si è abituati a Python dalla riga di comando, utilizzare PIP.exe per installare i nuovi pacchetti. È possibile trovare il **pip** programma di installazione di `Scripts` sottocartella. 

    Se si verifica un errore `pip` non è riconosciuto come comando interno o esterno, è possibile aggiungere il percorso dell'eseguibile Python e la cartella degli script Python nella variabile PATH di Windows.

    Il percorso completo del **script** cartella in un'installazione predefinita è la seguente:

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Scripts`

+ Se si utilizza Visual Studio 2017 o Visual Studio 2015 con le estensioni di Python, è possibile eseguire `pip install` dal **gli ambienti Python** finestra. Fare clic su **pacchetti**e nella casella di testo, specificare il nome o il percorso del pacchetto da installare. Non è necessario digitare `pip install`; quindi viene inserito automaticamente automaticamente. 

    - Se il computer abbia accesso a Internet, fornire il nome del pacchetto o l'URL di un pacchetto specifico e una versione. 
    
    Ad esempio, per installare la versione di CNTK supportato per Windows e 3.5 di Python, specificare l'URL di download: `https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl`

    - Se il computer non ha accesso a internet, è necessario scaricare il file WHL prima di iniziare l'installazione. Quindi, specificare il nome e percorso del file locale. Ad esempio, incollare il percorso e il file per installare il file WHL scaricato dal sito seguente: `"C:\Downloads\CNTK\cntk-2.1-cp35-cp35m-win_amd64.whl"`

Verrà richiesto di elevare le autorizzazioni per completare l'installazione.

Durante l'installazione, è possibile visualizzare messaggi di stato nella finestra del prompt dei comandi:

```python
pip install https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
Collecting cntk==2.1 from https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
  Downloading https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl (34.1MB)
    100% |################################| 34.1MB 13kB/s
...
Installing collected packages: cntk
Successfully installed cntk-2.1
```


### <a name="step-4-load-the-package-or-its-functions-as-part-of-your-script"></a>Passaggio 4. Caricare il pacchetto o le relative funzioni come parte dello script

Quando l'installazione è stata completata, è possibile iniziare immediatamente mediante il pacchetto come descritto nel passaggio successivo.

Per esempi di apprendimento completa utilizzando CNTK, vedere queste esercitazioni: [API Python per CNTK](https://cntk.ai/pythondocs/tutorials.html)

Per utilizzare le funzioni dal pacchetto nello script, inserire lo standard `import <package_name>` istruzione nelle righe iniziale dello script:

```python
import numpy as np
import cntk as cntk
cntk._version_
```

##  <a name="how-to-view-installed-packages-using-conda"></a>Come visualizzare i pacchetti installati utilizzando conda

Esistono diversi modi in cui è possibile ottenere un elenco dei pacchetti installati. Ad esempio, è possibile visualizzare i pacchetti installati nel **gli ambienti Python** windows di Visual Studio.

Se si utilizza la riga di comando di Python, è possibile utilizzare il **conda** package manager, che è incluso con l'ambiente Anaconda Python aggiunto dal programma di installazione di SQL Server.

Per visualizzare i pacchetti Python che sono stati installati nell'ambiente corrente, eseguire questo comando dal prompt dei comandi:

```python
conda list
```

Per ulteriori informazioni **conda** e come è possibile usarlo per creare e gestire più ambienti Python, vedere [la gestione di ambienti con conda](https://conda.io/docs/user-guide/tasks/manage-environments.html).
