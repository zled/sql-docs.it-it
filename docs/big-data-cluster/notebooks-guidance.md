---
title: Come usare i notebook in fase di anteprima di SQL Server 2019 | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 989ee419406d0f69cd7bda26485d3d44cbf56550
ms.sourcegitcommit: c7d3a903eb7f410db3a0230101d24de0af17621a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2018
ms.locfileid: "48827332"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>Come usare i notebook in fase di anteprima di SQL Server 2019

Questo articolo illustra come avviare i notebook in un cluster di big data di SQL Server 2019. Viene inoltre illustrato come iniziare a creare i tuoi notebook e come inviare processi rispetto al cluster.

## <a name="prerequisites"></a>Prerequisiti

Per usare i notebook, è necessario installare i prerequisiti seguenti:

- [Un cluster di big data di SQL Server 2019](deployment-guidance.md)
- [Studio di dati di Azure](../azure-data-studio/what-is.md)
- [L'estensione di SQL Server 2019 (anteprima)](../azure-data-studio/sql-server-2019-extension.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="connect-to-the-sql-server-big-data-cluster-end-point"></a>Connettersi al punto finale di cluster di SQL Server i big Data

È possibile connettersi a diversi endpoint del cluster. È possibile connettersi al tipo di connessione di Microsoft SQL Server o per l'endpoint di cluster di SQL Server i big Data.

In Azure Data Studio (anteprima), digitare **F1** > **nuova connessione**e connettersi all'endpoint di cluster dei big data di SQL Server.

![immagine1](media/notebooks-guidance/image1.png)

## <a name="browse-hdfs"></a>Sfoglia HDFS
Dopo essersi connessi, sarà in grado di individuare la cartella HDFS. WebHDFS viene avviato quando viene completata la distribuzione, e sarà in grado **Refresh**, aggiungere **nuova Directory**, **caricare** file, e **eliminare**.

![immagine2](media/notebooks-guidance/image2.png)

Queste semplici operazioni consentono di inserire i propri dati in HDFS.

## <a name="launch-new-notebooks"></a>Avviare di nuovo notebook

Esistono diversi modi per avviare un nuovo notebook.

1. Dal Dashboard di gestione. Nella creazione di una nuova connessione, verrà visualizzato un Dashboard. Fare clic sull'attività Nuovo Notebook dal Dashboard.

  ![image3](media/notebooks-guidance/image3.png)

1. Fare clic con il pulsante destro sulla connessione HDFS/Spark e nel menu di scelta rapida è presente nuovo Notebook

![image4](media/notebooks-guidance/image4.png)

Specificare un nome del Notebook (esempio: *Test.ipynb*) e fare clic su **salvare**.

![image5](media/notebooks-guidance/image5.png)

## <a name="supported-kernels-and-attach-to-context"></a>Supportati i kernel e associare al contesto

Nel nostro installazione Notebook, sono supportati i kernel PySpark e Spark, Magic Spark che consentono agli utenti di scrivere il codice Python e Scala con Spark. È anche possibile consentire agli utenti di scegliere Python per gli scopi di sviluppo locale.

![image6](media/notebooks-guidance/image6.png)

Quando si seleziona uno di questi kernel, verrà installato tale kernel nell'ambiente virtuale e iniziare a scrivere codice nel linguaggio supportato.

| Kernel | Description
|---- |----
|Kernel PySpark| Per la scrittura di codice Python con Spark, di calcolo dal cluster.
|Kernel Spark|Per la scrittura di codice Scala con Spark, di calcolo dal cluster.
|Kernel Python|Per la scrittura di codice Python per lo sviluppo locale.

La selezione Attach-to fornisce il contesto per il Kernel da collegare. Quando si è connessi al punto finale di cluster di SQL Server i big data, la selezione predefinita Attach-to sarà tale endpoint del cluster.

![image7](media/notebooks-guidance/image7.png)

## <a name="hello-world-in-the-different-contexts"></a>HelloWorld in contesti diversi

### <a name="pyspark-kernel"></a>Kernel Pyspark

Scegliere il PySpark Kernel e nel tipo di cella nel codice seguente:

![image8](media/notebooks-guidance/image8.png)

Fare clic su Esegui e si dovrebbe vedere l'applicazione Spark in corso l'avvio e si verrà visualizzato l'output seguente:

![image9](media/notebooks-guidance/image9.png)

L'output dovrebbe essere simile all'immagine seguente.

![Image10](media/notebooks-guidance/image10.png)

### <a name="spark-kernel"></a>Kernel Spark
Aggiungere una nuova cella di codice facendo la + comando sulla barra degli strumenti del codice.

![Image11](media/notebooks-guidance/image11.png)

Scegliere il Kernel Spark nell'elenco a discesa per i kernel e nella cella digita/Incolla in 

![Image12](media/notebooks-guidance/image12.png)

Fare clic su **eseguiti** viene visualizzata l'applicazione Spark in corso l'avvio e verrà creata la sessione di Spark **spark** e verranno definite il **HelloWorld** oggetto.

Il blocco appunti dovrebbe essere simile all'immagine seguente.

![Image13](media/notebooks-guidance/image13.png)

Una volta l'oggetto si definisce quindi nel tipo di cella Notebook successivo nel codice seguente:

![Image14](media/notebooks-guidance/image14.png)

Fare clic su **eseguire** nel Notebook di menu e verrà visualizzato "Hello, world!" Nell'output.

![Image15](media/notebooks-guidance/image15.png)

### <a name="local-python-kernel"></a>Kernel python in locale
Scegliere il Kernel Python in locale e nel tipo di cella in * *

![Image16](media/notebooks-guidance/image16.png)

È consigliabile vedere l'output seguente:

![Image17](media/notebooks-guidance/image17.png)

### <a name="markdown-text"></a>Testo di markdown
Aggiungere una nuova cella di testo facendo il comando di testo nella barra degli strumenti +.

![Image18](media/notebooks-guidance/image18.png)

Fare clic sull'icona di anteprima per aggiungere il codice markdown

![Image19](media/notebooks-guidance/image19.png)

Fare clic sull'icona di anteprima per attivare/disattivare per visualizzare solo il markdown

![Image20](media/notebooks-guidance/image20.png)

## <a name="manage-packages"></a>Gestire i pacchetti
Uno degli aspetti che è stato ottimizzato per lo sviluppo Python locale era includono la possibilità di installare i pacchetti che i clienti sono necessario per i loro scenari. Per impostazione predefinita, si includono i pacchetti più comuni, ad esempio pandas, numpy e così via, ma se ci si aspetta un pacchetto che non è incluso quindi scrivere il codice seguente nella cella Notebook

```python
import <package-name>
```

Quando si esegue questo comando, si otterrà un `Module not found` errore. Se il pacchetto esiste, non si verrà visualizzato l'errore.

Se si trova un `Module not Found` errori, quindi fare clic sui **Gestisci pacchetti** per avviare il terminale con il percorso per il Virtualenv identificato. È ora possibile installare i pacchetti in locale. Usare il comando seguente per installare i pacchetti:

```
./pip install <package-name>
```

Dopo aver installato il pacchetto, sarà possibile tornare nella cella Notebook e digitare il comando seguente:

```python
import <package-name>
```

A questo punto quando si esegue la cella, non si dovrebbe accedere non è più il `Module not found` errore.

Se si desidera disinstallare un pacchetto, usare il comando seguente dal terminale:

```
./pip uninstall <package-name>
```

## <a name="next-steps"></a>Passaggi successivi

Per informazioni su come usare un notebook esistente, vedere [come gestire i notebook in Azure Data Studio](notebooks-how-to-manage.md).