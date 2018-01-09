---
title: Installare i nuovi pacchetti Python in SQL Server | Documenti Microsoft
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 78a76403f3212c7619afbf02577075161699fbd6
ms.sourcegitcommit: 60d0c9415630094a49d4ca9e4e18c3faa694f034
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="install-new-python-packages-on-sql-server"></a>Installare i nuovi pacchetti Python in SQL Server

In questo articolo viene descritto come installare i nuovi pacchetti Python in un'istanza di SQL Server 2017.

Viene inoltre descritto come elencare i pacchetti installati nell'ambiente corrente.

## <a name="prerequisites"></a>Prerequisites

Il processo per l'installazione di nuovi pacchetti è molto simili a quelli presenti in un ambiente standard di Python. Tuttavia, alcuni passaggi aggiuntivi sono necessari se il server non dispone di una connessione internet.

+ È necessario avere installato Servizi di Machine Learning (In-Database) con l'opzione di linguaggio Python. Per istruzioni, vedere [impostare Python Machine Learning Services](setup-python-machine-learning-services.md).

+ Per ogni istanza del server, è necessario installare una copia separata del pacchetto. Pacchetti non possono essere condivisa tra più istanze.

+ Determinare se il pacchetto che si intende utilizzare funzionerà con Python 3.5 e nell'ambiente di Windows. 

    In generale, esistono alcune limitazioni per i pacchetti che è possibile importare e utilizzare nell'ambiente di SQL Server. I problemi possibili includono pacchetti che utilizzano la funzionalità di rete è bloccata sul server o dal firewall, o con le dipendenze che non possono essere installate in un computer Windows.

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

    Ad esempio, in un computer separato, è possibile scaricare il file WHL da questo sito [https://cntk.ai/PythonWheel/CPU-Only](https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl)e quindi copiare il file `cntk-2.1-cp35-cp35m-win_amd64.whl` in una cartella locale nel computer SQL Server.

+ SQL Server 2017 Usa Python 3.5. Assicurarsi di ottenere la versione del pacchetto di Windows e una versione compatibile con Python 3.5.

Questa pagina contiene i download per più piattaforme e per più versioni di Python: [impostare CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="step-2-open-a-python-command-prompt"></a>Passaggio 2. Aprire un prompt dei comandi di Python

Individuare il percorso di libreria Python predefinito utilizzato da SQL Server. Se è stato installato più istanze, assicurarsi di individuare la cartella PYTHON_SERVICE per l'istanza in cui si desidera aggiungere il pacchetto.

Ad esempio, se Machine Learning Services è stato installato utilizzando le impostazioni predefinite e l'apprendimento è abilitato nell'istanza predefinita, il percorso sarà come segue:

    `C:\Program Files\Microsoft SQL  Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

Aprire il prompt dei comandi di Python associato all'istanza.

> [!TIP]
> È consigliabile configurare un ambiente di Python specifici di Machine Learning Server o SQL Server.

### <a name="step-3-install-the-package-using-pip"></a>Passaggio 3. Installare il pacchetto utilizzando pip

+ Se si è abituati a Python dalla riga di comando, utilizzare PIP.exe per installare i nuovi pacchetti. È possibile trovare il **pip** programma di installazione di `Scripts` sottocartella. 

    Se si verifica un errore **pip** non è riconosciuto come comando interno o esterno, è possibile aggiungere il percorso dell'eseguibile Python e la cartella degli script Python nella variabile PATH di Windows.

    Il percorso completo del **script** cartella in un'installazione predefinita è la seguente:

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Scripts`

+ Se si utilizza Visual Studio 2017 o Visual Studio 2015 con le estensioni di Python, è possibile eseguire `pip install` dal **ambienti Python** finestra. Fare clic su **pacchetti**e nella casella di testo, specificare il nome o il percorso del pacchetto da installare. Non è necessario digitare `pip install`; quindi viene inserito automaticamente automaticamente. 

    - Se il computer ha accesso a Internet, fornire il nome del pacchetto o l'URL di un pacchetto specifico e una versione. Per installare la versione di CNTK che è supportato per Windows e Python 3.5, ad esempio, è possibile specificare l'URL di download:`https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl`

    - Se il computer non ha accesso a internet, deve scaricato il file WHL in anticipo. Quindi, specificare il percorso del file locale e il nome. Ad esempio, incollare il percorso e il file per installare il file WHL scaricato dal sito seguente:`"C:\Downloads\CNTK\cntk-2.1-cp35-cp35m-win_amd64.whl"`

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

##  <a name="how-to-view-installed-packages-using-conda"></a>Come visualizzare i pacchetti installati utilizzando conda

Esistono diversi modi in cui è possibile ottenere un elenco dei pacchetti installati. Ad esempio, è possibile visualizzare i pacchetti installati nel **ambienti Python** windows di Visual Studio.

Se si utilizza la riga di comando di Python, è possibile utilizzare il **conda** package manager, che è incluso con l'ambiente Anaconda Python aggiunto dal programma di installazione di SQL Server.

Per visualizzare i pacchetti Python che sono stati installati nell'ambiente corrente, eseguire questo comando dal prompt dei comandi windows:

```python
conda list
```

Per ulteriori informazioni su **conda** e come è possibile usarlo per creare e gestire più ambienti Python, vedere [la gestione di ambienti con conda](https://conda.io/docs/user-guide/tasks/manage-environments.html).
