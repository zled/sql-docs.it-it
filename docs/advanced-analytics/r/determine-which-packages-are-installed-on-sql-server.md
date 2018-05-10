---
title: Ottenere informazioni sul pacchetto di Python e R in SQL Server Machine Learning | Documenti Microsoft
description: Determinare la versione del pacchetto R, Python, verificare l'installazione e ottenere un elenco dei pacchetti installati in SQL Server R Services o servizi di Machine Learning.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/08/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3295bbdbb00c73c9aaa37dcb15d35121b82454bb
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2018
---
#  <a name="get-r-and-python-package-information-on-sql-server-machine-learning"></a>Ottenere informazioni sul pacchetto di Python e R in SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Se si sono installati più ambienti Python o utilizzano più strumenti di R, è facile da installare un pacchetto per la libreria non corretta o l'ambiente e non sarà possibile trovarlo in un secondo momento. Questo articolo fornisce le query e al materiale sussidiario utile per la versione del pacchetto determininga e per elencare i pacchetti che vengono installati nell'ambiente di SQL Server corrente.

## <a name="verify-the-current-default-library"></a>Verificare la libreria predefinita corrente

Per **R** in SQL Server, eseguire l'istruzione seguente per verificare la libreria predefinita per l'istanza corrente:

```sql
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Per **Python** in SQL Server, eseguire l'istruzione seguente per verificare la libreria predefinita per l'istanza corrente:

```sql
EXEC sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

## <a name="generate-a-package-list-using-a-stored-procedure"></a>Generare un elenco dei pacchetti tramite una stored procedure

Sono disponibili più modi che è possibile ottenere un elenco completo dei pacchetti installati. Uno dei vantaggi dell'esecuzione di comandi dell'elenco di pacchetti da sp_execute_external_script è che si è certi di ottenere i pacchetti installati nella libreria di istanza.

### <a name="r"></a>L

Nell'esempio seguente viene utilizzata la funzione di R `installed.packages()` in un [!INCLUDE [tsql](..\..\includes\tsql-md.md)] stored procedure per ottenere una matrice di pacchetti che sono stati installati nella libreria R_SERVICES per l'istanza corrente. Per evitare l'analisi dei campi nel file DESCRIPTION, viene restituito solo il nome.

```SQL
EXECUTE sp_execute_external_script
@language=N'R'
,@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
NameOnly <- packagematrix[,1];
OutputDataSet <- as.data.frame(NameOnly);'
, @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250) ))
```

Per ulteriori informazioni su facoltativo e campi predefiniti per il campo della descrizione del pacchetto R, vedere [ https://cran.r-project.org ](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

### <a name="python"></a>Python

Il `pip` modulo viene installato per impostazione predefinita e supporta molte operazioni per i pacchetti di elenco installato, oltre a quelli supportati da Python standard. È possibile eseguire `pip` da un Python prompt dei comandi, naturalmente, ma è inoltre possibile chiamare alcune funzioni pip da `sp_execute_external_script`.

```sql
execute sp_execute_external_script 
@language = N'Python', 
@script = N'
import pip
import pandas as pd
installed_packages = pip.get_installed_distributions()
installed_packages_list = sorted(["%s==%s" % (i.key, i.version)
     for i in installed_packages])
df = pd.DataFrame(installed_packages_list)
OutputDataSet = df
'
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

Quando si esegue `pip` dalla riga di comando, sono disponibili molte altre funzioni utili: `pip list` Ottiene tutti i pacchetti che sono installati, mentre `pip freeze` Elenca i pacchetti installati da `pip`e non vengono elencati i pacchetti pip stesso dipende. È inoltre possibile utilizzare `pip freeze` per generare un file di dipendenza.

## <a name="verify-whether-a-package-is-installed-with-an-instance"></a>Verificare se un pacchetto viene installato con un'istanza

Se si è installato un pacchetto e si desidera assicurarsi che sia disponibile per una particolare istanza di SQL Server, è possibile eseguire la seguente chiamata di stored procedure per caricare il pacchetto e restituire solo i messaggi.

### <a name="r"></a>L

In questo esempio cerca e carica la libreria RevoScaleR, se disponibile.

```sql
EXEC sp_execute_external_script  @language =N'R',
@script=N'require("RevoScaleR")'
GO
```

+ Se il pacchetto viene trovato, viene restituito un messaggio: "Comandi vengano eseguiti correttamente."

+ Se è Impossibile trovare o caricare il pacchetto, si verifica un errore che contiene il testo: "non è presente alcun pacchetto chiamato 'MissingPackageName'"

### <a name="python"></a>Python

Il controllo equivalente per Python può essere eseguito da Python della shell, utilizzando `conda` o `pip` comandi. In alternativa, è possibile eseguire questa istruzione in una stored procedure:

```sql
exec sp_execute_external_script
       @language = N'Python'
       , @script = N'
import pip
import pkg_resources
pckg_name = "revoscalepy"
pckgs = pandas.DataFrame([(i.key) for i in pip.get_installed_distributions()], columns = ["key"])
installed_pckg = pckgs.query(''key == @pckg_name'')
print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")'
```

## <a name="view-installed-packages-using-a-utility-or-ide"></a>Visualizzare i pacchetti installati utilizzando un'utilità o IDE

La maggior parte degli strumenti di sviluppo forniscono un Visualizzatore oggetti o un elenco di pacchetti che vengono installati o caricati nell'ambiente di lavoro corrente o. In questa sezione vengono forniti alcuni suggerimenti brevi utilizzando i comuni strumenti di R o Python.

### <a name="r-tools"></a>Strumenti di R

Esistono diversi modi per ottenere un elenco di pacchetti installati o caricati tramite l'utilità di R. 

+ Da un'utilità R locale, utilizzare una funzione R di base, ad esempio `installed.packages()`, incluso nel `utils` pacchetto. Per ottenere un elenco che è preciso per un'istanza, è necessario specificare in modo esplicito il percorso di libreria o utilizzare gli strumenti di R associati con la libreria di istanza.

### <a name="python-tools"></a>Strumenti Python

Estensioni di Python per Visual Studio rendono molto semplice visualizzare i pacchetti installati nell'ambiente corrente o in altri ambienti virtuali elencate nell'IDE. È possibile configurare più ambienti, scegliere un ambiente da un elenco e visualizzare i pacchetti o installare i nuovi pacchetti in tale ambiente.

+ [Ambienti Python](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio)

Codice di Visual Studio è un editor gratuito che supporta Python, con diverse linters Python è disponibile. Anche se il codice di Visual Studio non fornisce un browser pacchetto simile a quello in Visual Studio, supporta la configurazione e il passaggio tra più ambienti.

+ [Python nel codice di Visual Studio](https://code.visualstudio.com/docs/languages/python)

Potrebbe essere necessari per eseguire un'ulteriore configurazione **revoscalepy** comandi da un client remoto:

+ [Installare localmente interprete e pacchetti Python personalizzati in Windows](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)

In questo blog fornisce alcuni suggerimenti utili sulla configurazione di altri ambienti di Python, tra cui PyCharm, per lavorare con **revoscalepy**.

+ [Introduzione ai servizi Web di Python con Server di Machine Learning](https://blogs.msdn.microsoft.com/mlserver/2017/12/13/getting-started-with-python-web-services-using-machine-learning-server/)

## <a name="use-functions-from-machine-learning-server"></a>Utilizzare le funzioni di Server di Machine Learning

Poiché le librerie utilizzate con l'esecuzione di SQL Server il supporto di codice da un client remoto, è possibile utilizzare queste funzioni per scoprire quali pacchetti vengono installati in un ambiente remoto.

### <a name="revoscaler"></a>RevoScaleR

Se si lavora in un client remoto e non ha accesso al server, è comunque possibile ottenere un elenco di pacchetti che vengono installati in SQL Server, tramite le funzioni RevoScaleR. Specificare il Server SQL come un contesto di calcolo, che è necessario disporre dell'autorizzazione per connettersi al server. 

+ [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) rileva che il percorso di un pacchetto nel contesto di calcolo remoto.

+ [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) Ottiene informazioni sui pacchetti installati in un contesto di calcolo.

Ad esempio, eseguire il seguente codice R per ottenere un elenco dei pacchetti disponibili nel contesto di calcolo specificato di SQL Server.

```R
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
sqlPackages
```

Nell'esempio seguente ottiene la posizione della raccolta di RevoScaleR nel contesto di calcolo locale e la versione del pacchetto.

```R
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

### <a name="revoscalepy"></a>revoscalepy

Funzioni simili a quelle per RevoScaleR non sono disponibili in questo momento. Cercare in una versione successiva di **revoscalepy**.

## <a name="get-library-location-and-version"></a>Ottenere una versione e il percorso di libreria

A volte quando si lavora con più ambienti o installazioni di R o Python, è necessario verificare che il codice che è in esecuzione viene utilizzata l'ambiente corretto per Python o l'area di lavoro corretto per R.

Ad esempio, se è stato aggiornato di machine learning componenti mediante l'associazione, il percorso alla libreria R potrebbe essere in una cartella diversa da quella predefinita. Inoltre, se si installa il Client R o un'istanza del server autonoma, potrebbe essere più librerie R nel computer in uso.

Questi esempi viene illustrato come ottenere il percorso e la versione della libreria in cui è utilizzata da SQL Server.

### <a name="r"></a>L

Questa stored procedure restituisce il percorso della libreria di istanza e la versione del pacchetto RevoScaleR utilizzato da SQL Server:

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> Il [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) funzione può essere eseguita solo nel computer di destinazione. La funzione non può restituire i percorsi di libreria per le connessioni remote.

**Risultati**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```

### <a name="python"></a>Python

Questo esempio viene restituito l'elenco delle cartelle incluse in Python `sys.path` variabile. L'elenco include la directory corrente e il percorso della libreria standard.

```sql
EXEC sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

**Risultati**

```text
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\python35.zip
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\DLLs
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Sphinx-1.5.4-py3.5.egg
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Pythonwin
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\setuptools-27.2.0-py3.5.egg
```

Per ulteriori informazioni sulla variabile `sys.path` e su come viene utilizzato per impostare il percorso di ricerca dell'interprete per i moduli, vedere il [documentazione Python](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)

