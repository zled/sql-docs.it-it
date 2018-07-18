---
title: Installare i nuovi pacchetti Python in SQL Server Machine Learning | Documenti Microsoft
description: Aggiunta di nuovi pacchetti Python a SQL Server 2017 Machine Learning Services (In-Database) e Machine Learning Server (Standalone)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: fa1ed2612fb88653a7259af0675b496fac4a6723
ms.sourcegitcommit: df382099ef1562b5f2d1cd506c1170d1db64de41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/12/2018
---
# <a name="install-new-python-packages-on-sql-server"></a>Installare i nuovi pacchetti Python in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene descritto come installare i nuovi pacchetti Python in un'istanza di SQL Server 2017 Machine Learning Services. In generale, il processo per l'installazione di nuovi pacchetti è simile a quello in un ambiente standard di Python. Tuttavia, alcuni passaggi aggiuntivi sono necessari se il server non dispone di una connessione internet.

Per informazioni sulla immaginando in cui sono installati i pacchetti o i pacchetti installati, vedere [Python o R ottenere informazioni sul pacchetto](../r/determine-which-packages-are-installed-on-sql-server.md).

## <a name="prerequisites"></a>Prerequisiti

+ È necessario avere installato SQL Server 2017 Machine Learning Services (In-Database) con l'opzione di linguaggio Python. Per istruzioni, vedere [installare SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-services-windows-install.md).

+ Per ogni istanza del server, è necessario installare una copia separata del pacchetto. Pacchetti non possono essere condivisa tra più istanze.

+ Pacchetti devono essere 3.5 Python conformi ed eseguiti in Windows. 

+ Valutare se il pacchetto è una scelta ottimale per l'utilizzo nell'ambiente di SQL Server. In genere un server di database supporta più servizi e applicazioni e risorse nel file system potrebbero essere limitato, nonché le connessioni al server. In molti casi l'accesso a Internet è bloccato completamente.

    Altri problemi comuni includono l'utilizzo di funzionalità che è stata bloccata nel server o il firewall, o i pacchetti con le dipendenze che non possono essere installate in un computer Windows di rete. 

    Alcuni pacchetti Python diffusi (ad esempio pallone) eseguono attività quali lo sviluppo web che eseguono migliori in un ambiente autonomo. È consigliabile utilizzare Python nel database per attività quali l'apprendimento automatico, che richiedono l'elaborazione dei dati con utilizzo intensivo che traggono vantaggio da una stretta integrazione con il motore di database, anziché semplicemente una query sul database.

+ Accesso amministrativo al server è necessario installare i pacchetti.

## <a name="add-a-new-python-package"></a>Aggiunge un nuovo pacchetto di Python

In questo esempio si presuppone che si desidera installare un nuovo pacchetto direttamente nel computer SQL Server.

Il pacchetto installato in questo esempio è [CNTK](https://docs.microsoft.com/cognitive-toolkit/), un framework per la formazione di Microsoft che supporta la personalizzazione, set di training e la condivisione di tipi diversi di reti neurali.

> [!TIP]
> Serve aiuto per configurare gli strumenti Python? Vedere i blog:
> 
> [Introduzione a servizi Web di Python con Server di Machine Learning](https://blogs.msdn.microsoft.com/mlserver/2017/12/13/getting-started-with-python-web-services-using-machine-learning-server/)
> 
> [David Crook: Microsoft cognitivi Toolkit + Visual Studio Code](http://dacrook.com/cntk-vs-code-awesome/)

### <a name="step-1-download-the-windows-version-of-the-python-package"></a>Passaggio 1. Scaricare la versione di Windows del pacchetto Python

+ Se si siano installando i pacchetti Python in un server senza accesso a internet, è necessario scaricare il file WHL in un computer diverso e quindi copiarlo nel server.

    In un computer separato, ad esempio, è possibile scaricare il file WHL da questo sito [ https://cntk.ai/PythonWheel/CPU-Only ](https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl), quindi copiare il file `cntk-2.1-cp35-cp35m-win_amd64.whl` in una cartella locale nel computer SQL Server.

+ SQL Server 2017 Usa Python 3.5. 

> [!IMPORTANT]
> Assicurarsi che si ottiene la versione del pacchetto di Windows. Se il file termina .gz, probabilmente non è la versione corretta.

Questa pagina contiene i download per più piattaforme e per più versioni di Python: [impostare CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="step-2-open-a-python-command-prompt"></a>Passaggio 2. Aprire un prompt dei comandi di Python

Individuare il percorso di libreria Python predefinito utilizzato da SQL Server. Se è stato installato più istanze, individuare la cartella PYTHON_SERVICE per l'istanza in cui si desidera aggiungere il pacchetto.

Ad esempio, se Machine Learning Services è stato installato utilizzando le impostazioni predefinite e l'apprendimento è abilitato nell'istanza predefinita, il percorso sarà come segue:

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

Aprire il prompt dei comandi di Python associato all'istanza.

> [!TIP]
> Per future, debug e test, si potrebbe voler impostare un ambiente di Python specifiche per la libreria di istanza.

### <a name="step-3-install-the-package-using-pip"></a>Passaggio 3. Installare il pacchetto utilizzando pip

+ Se si è abituati a Python dalla riga di comando, utilizzare PIP.exe per installare i nuovi pacchetti. È possibile trovare il **pip** programma di installazione di `Scripts` sottocartella. 

  Installazione di SQL Server non aggiungere script al percorso di sistema. Se si verifica un errore `pip` non è riconosciuto come comando interno o esterno, è possibile aggiungere la cartella degli script nella variabile PATH di Windows.

  Il percorso completo del **script** cartella in un'installazione predefinita è la seguente:

    C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts

+ Se si utilizza Visual Studio 2017 o Visual Studio 2015 con le estensioni di Python, è possibile eseguire `pip install` dal **ambienti Python** finestra. Fare clic su **pacchetti**e nella casella di testo, specificare il nome o il percorso del pacchetto da installare. Non è necessario digitare `pip install`; quindi viene inserito automaticamente automaticamente. 

    - Se il computer ha accesso a Internet, fornire il nome del pacchetto o l'URL di un pacchetto specifico e una versione. 
    
    Ad esempio, per installare la versione di CNTK che è supportato per Windows e 3.5 di Python, specificare l'URL di download: `https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl`

    - Se il computer non ha accesso a internet, è necessario scaricare il file WHL prima di iniziare l'installazione. Quindi, specificare il percorso del file locale e il nome. Ad esempio, incollare il percorso e il file per installare il file WHL scaricato dal sito seguente: `"C:\Downloads\CNTK\cntk-2.1-cp35-cp35m-win_amd64.whl"`

Potrebbe essere necessario elevare le autorizzazioni per completare l'installazione.

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

## <a name="list-installed-packages-using-conda"></a>Elenco dei pacchetti installati utilizzando conda

Esistono diversi modi in cui è possibile ottenere un elenco dei pacchetti installati. Ad esempio, è possibile visualizzare i pacchetti installati nel **ambienti Python** windows di Visual Studio.

Se si utilizza la riga di comando di Python, è possibile utilizzare **Pip** o il **conda** Gestione pacchetti, incluso con l'ambiente Anaconda Python aggiunto dal programma di installazione di SQL Server.

Supponendo che la cartella degli script aggiunto alla variabile di ambiente PATH, eseguire questo comando dal prompt dei comandi dell'amministratore per elencare i pacchetti Python nell'ambiente in uso. In caso contrario, vedere [Python e R ottenere informazioni sul pacchetto](../r/determine-which-packages-are-installed-on-sql-server.md#pip-conda) dei puntatori su come eseguire gli strumenti Python in SQL Server.

```python
conda list
```

Per ulteriori informazioni su **conda** e come è possibile usarlo per creare e gestire più ambienti Python, vedere [la gestione di ambienti con conda](https://conda.io/docs/user-guide/tasks/manage-environments.html).
