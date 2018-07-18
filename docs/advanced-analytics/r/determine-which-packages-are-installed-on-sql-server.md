---
title: Ottenere informazioni sul pacchetto di Python e R in SQL Server Machine Learning | Documenti Microsoft
description: Determinare la versione del pacchetto R, Python, verificare l'installazione e ottenere un elenco dei pacchetti installati in SQL Server R Services o servizi di Machine Learning.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 85ea4658ca8b60fc24d7e4f7849de1655eab6082
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707889"
---
#  <a name="get-r-and-python-package-information"></a>Ottenere informazioni sul pacchetto R e Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

A volte quando si lavora con più ambienti o le installazioni di Python o R, è necessario verificare che il codice che è in esecuzione stia utilizzando l'ambiente previsto per l'area di lavoro corretto o Python per R. Ad esempio, se è stato eseguito l'aggiornamento di machine learning componenti tramite [associazione](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md), il percorso alla libreria R potrebbe essere in una cartella diversa da quelle predefinite. Inoltre, se si installa il Client R o un'istanza del server autonoma, potrebbe essere più librerie R nel computer in uso.

Esempi di script R e Python in questo articolo mostrano come ottenere il percorso e la versione dei pacchetti utilizzato da SQL Server.

## <a name="get-the-r-library-location"></a>Ottenere il percorso della libreria R

Per qualsiasi versione di SQL Server, eseguire l'istruzione seguente per verificare il [libreria pacchetto predefinito R](installing-and-managing-r-packages.md) per l'istanza corrente:

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Facoltativamente, è possibile utilizzare [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) nelle versioni più recenti di RevoScaleR in servizi di SQL Server 2017 Machine Learning o [R Services aggiornato R per almeno RevoScaleR 9.0.1](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). Questa stored procedure restituisce il percorso della libreria di istanza e la versione di RevoScaleR utilizzato da SQL Server:

```sql
EXECUTE sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> Il [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) funzione può essere eseguita solo nel computer locale. La funzione non può restituire i percorsi di libreria per le connessioni remote.

**Risultati**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.3.0'
```

## <a name="get-the-python-library-location"></a>Ottenere il percorso della libreria Python

Per **Python** in SQL Server 2017, eseguire l'istruzione seguente per verificare la libreria predefinita per l'istanza corrente. Questo esempio viene restituito l'elenco delle cartelle incluse in Python `sys.path` variabile. L'elenco include la directory corrente e il percorso della libreria standard.

```sql
EXECUTE sp_execute_external_script
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

## <a name="list-all-packages"></a>Elencare tutti i pacchetti

Sono disponibili più modi che è possibile ottenere un elenco completo dei pacchetti installati. Uno dei vantaggi dell'esecuzione di comandi dell'elenco di pacchetti da sp_execute_external_script è che si è certi di ottenere i pacchetti installati nella libreria di istanza.

### <a name="r"></a>R

Nell'esempio seguente viene utilizzata la funzione di R `installed.packages()` in un [!INCLUDE [tsql](..\..\includes\tsql-md.md)] stored procedure per ottenere una matrice di pacchetti che sono stati installati nella libreria R_SERVICES per l'istanza corrente. Questo script restituisce i campi nome e la versione del pacchetto nel file DESCRIPTION, viene restituito solo il nome.

```SQL
EXECUTE sp_execute_external_script
  @language=N'R',
  @script = N'str(OutputDataSet);
  packagematrix <- installed.packages();
  Name <- packagematrix[,1];
  Version <- packagematrix[,3];
  OutputDataSet <- data.frame(Name, Version);',
  @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Per ulteriori informazioni su facoltativo e campi predefiniti per il campo della descrizione del pacchetto R, vedere [ https://cran.r-project.org ](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

### <a name="python"></a>Python

Il `pip` modulo viene installato per impostazione predefinita e supporta molte operazioni per i pacchetti di elenco installato, oltre a quelli supportati da Python standard. È possibile eseguire `pip` da un Python prompt dei comandi, naturalmente, ma è inoltre possibile chiamare alcune funzioni pip da `sp_execute_external_script`.

```sql
EXECUTE sp_execute_external_script 
  @language = N'Python', 
  @script = N'
  import pip
  import pandas as pd
  installed_packages = pip.get_installed_distributions()
  installed_packages_list = sorted(["%s==%s" % (i.key, i.version)
     for i in installed_packages])
  df = pd.DataFrame(installed_packages_list)
  OutputDataSet = df'
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

Quando si esegue `pip` dalla riga di comando, sono disponibili molte altre funzioni utili: `pip list` Ottiene tutti i pacchetti che sono installati, mentre `pip freeze` Elenca i pacchetti installati da `pip`e non vengono elencati i pacchetti pip stesso dipende. È inoltre possibile utilizzare `pip freeze` per generare un file di dipendenza.

## <a name="find-a-single-package"></a>Trovare un singolo pacchetto

Se si è installato un pacchetto e si desidera assicurarsi che sia disponibile per una particolare istanza di SQL Server, è possibile eseguire la seguente chiamata di stored procedure per caricare il pacchetto e restituire solo i messaggi.

### <a name="r"></a>R

In questo esempio cerca e carica la libreria RevoScaleR, se disponibile.

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("RevoScaleR")'
GO
```

+ Se il pacchetto viene trovato, viene restituito un messaggio: "Comandi vengano eseguiti correttamente."

+ Se è Impossibile trovare o caricare il pacchetto, si verifica un errore che contiene il testo: "non è presente alcun pacchetto chiamato 'MissingPackageName'"

### <a name="python"></a>Python

Il controllo equivalente per Python può essere eseguito da Python della shell, utilizzando `conda` o `pip` comandi. In alternativa, è possibile eseguire questa istruzione in una stored procedure:

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
  import pip
  import pkg_resources
  pckg_name = "revoscalepy"
  pckgs = pandas.DataFrame([(i.key) for i in pip.get_installed_distributions()], columns = ["key"])
  installed_pckg = pckgs.query(''key == @pckg_name'')
  print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")'
```

## <a name="get-package-information-in-r-and-python-tools"></a>Ottenere informazioni sul pacchetto negli strumenti di R e Python

Tutte le istruzioni precedenti si supponga che si sta utilizzando uno strumento di SQL Server, ad esempio Management Studio (SSMS). Se si preferisce utilizzare gli strumenti di R e Python, le istruzioni seguenti illustrano come ottenere informazioni sulla libreria e pacchetto dalla riga di comando R o Python.

### <a name="r-commands"></a>Comandi di R

La libreria di istanza per R è \Programmi\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library.

Avviare gli strumenti standard di R da questi percorsi per verificare che i pacchetti dalla libreria di istanza vengono utilizzati:

+ \MSSQL14. MSSQLSERVER\R_SERVICES\bin\R.exe per un prompt dei comandi di R
+ \MSSQL14. MSSQLSERVER\R_SERVICES\bin\x64\Rgui.exe per un'app console di R

È possibile utilizzare i comandi standard di R o RevoScaleR per ottenere informazioni sul pacchetto. Il pacchetto RevoScaleR viene caricato automaticamente. 

Restituiscono informazioni sul pacchetto RevoScaleR:

    > print(Revo.version)

Restituire un elenco di tutti i pacchetti installati:

    > installed.packages()

Restituire la versione di r:

    > packageDescription("base")

### <a name="python-commands"></a>Comandi di Python

Supporto Python è solo SQL Server 2017. La libreria di istanza per Python è \Programmi\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\.

Aprire la finestra di comando di Python da questo percorso per verificare che i pacchetti dalla libreria di istanza vengono utilizzati:

+ \MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Python.exe

Aprire la Guida interattiva:

    > help()

Digitare un nome di modulo al prompt di Guida per ottenere il contenuto del pacchetto, versione e percorso del file:

    help> revoscalepy

<a name="pip-conda"></a>

### <a name="python-package-managers-pip-and-conda"></a>Gestori (Pip e Conda) del pacchetto Python

Anaconda include Python tools per la gestione dei pacchetti. A un valore predefinito è sono reperibile istanza, Pip, Conda e altri strumenti in \Programmi\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts.

Installazione di SQL Server non verranno aggiunti Pip o Conda al percorso di sistema e in un'istanza di SQL Server di produzione, mantenendo i file eseguibili non essenziali dal percorso è una procedura consigliata. Tuttavia, per gli ambienti di sviluppo e test, è possibile aggiungere la cartella degli script per la variabile di ambiente PATH sistema di eseguire sia Pip e Conda sul comando da qualsiasi posizione.

1. Passare a C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts

1. Fare doppio clic su **conda.exe** > **Esegui come amministratore**, quindi immettere `conda list` per restituire un elenco di pacchetti installati nell'ambiente corrente.

1. Analogamente, fare doppio clic su **pip.exe** > **Esegui come amministratore**, quindi immettere `pip list` per restituire le stesse informazioni. 


## <a name="next-steps"></a>Passaggi successivi

+ [Installare nuovi pacchetti R](install-additional-r-packages-on-sql-server.md)
+ [Installare nuovi pacchetti Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Esercitazioni, esempi, soluzioni](../tutorials/machine-learning-services-tutorials.md)