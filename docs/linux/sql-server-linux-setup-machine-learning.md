---
title: Installare SQL Server Machine Learning Services (R, Python, Java) in Linux | Microsoft Docs
description: Questo articolo descrive come installare SQL Server Machine Learning Services (R, Python, Java) su Ubuntu e Red Hat.
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 10/09/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8433f705b41782c61950cb74f76f694d61cd548d
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100452"
---
# <a name="install-sql-server-2019-machine-learning-services-r-python-java-on-linux"></a>Installare SQL Server 2019 Machine Learning Services (R, Python, Java) in Linux

[SQL Server Machine Learning Services](../advanced-analytics/what-is-sql-server-machine-learning.md) viene eseguito nei sistemi operativi Linux a partire da questa versione di anteprima di SQL Server 2019. Seguire i passaggi descritti in questo articolo per installare l'estensione di programmazione Java, o le estensioni di apprendimento per R e Python. 

Machine learning e le estensioni di programmazione è un componente aggiuntivo per il motore di database. Sebbene sia possibile [installare il motore di database e servizi di Machine Learning contemporaneamente](#install-all), è consigliabile installare e configurare il motore di database di SQL Server prima di tutto in modo da poter risolvere eventuali problemi prima di aggiungerne altri componenti. 

Percorso del pacchetto delle estensioni di R, Python e Java sono nei repository di origine Linux di SQL Server. Se è già configurato installare repository del codice sorgente per il motore di database, è possibile eseguire il mssql-mlservices comandi di installazione del pacchetto usando la stessa registrazione di repository.

## <a name="prerequisites"></a>Prerequisiti

+ Sistema operativo Linux deve essere [supportati da SQL Server](sql-server-linux-release-notes-2019.md#supported-platforms), in esecuzione in locale o in un contenitore Docker.

+ È necessario disporre di un'istanza del motore di Database di SQL Server 2019 nel: 

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ Per R, solo [Microsoft R Open](#mro) per i pacchetti R mssql-mlsservices. 

<a name="mro"></a>

### <a name="microsoft-r-open-mro-installation"></a>Installazione di Microsoft R Open (MRO)

Distribuzione di base di Microsoft di R è un prerequisito per l'uso di RevoScaleR, MicrosoftML e altri pacchetti R installati con i servizi di Machine Learning.

La versione richiesta è MRO 3.4.4.

Scegliere tra i due approcci seguenti per installare MRO:

+ Scaricare il file tarball MRO da MRAN, decomprimerlo ed eseguire lo script install.sh. È possibile seguire le [istruzioni di installazione su MRAN](https://mran.microsoft.com/releases/3.4.4) se si desidera che questo approccio.

+ In alternativa, registrare il **packages.microsoft.com** repository come descritto di seguito per installare i pacchetti di tre che comprendono la distribuzione MRO: microsoft-r-open-mro, microsoft-r-open-mkl, e Microsoft-r-open-foreachiterators. 

I comandi seguenti registrare il repository fornendo MRO. Post-registrazione, i comandi per installare altri pacchetti R, ad esempio mssql-mlservices-mml-r, includerà automaticamente MRO come una dipendenza del pacchetto.

#### <a name="mro-on-ubuntu"></a>MRO in Ubuntu

```bash
# Install as root
sudo su

# Optionally, if your system does not have the https apt transport option
apt-get install apt-transport-https

# Add the **azure-cli** repo to your apt sources list
AZ_REPO=$(lsb_release -cs)

echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | sudo tee /etc/apt/sources.list.d/azure-cli.list

# Set the location of the package repo the "prod" directory containing the distribution.
# This example specifies 16.04. Replace with 14.04 if you want that version
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the repo
dpkg -i packages-microsoft-prod.deb
```

#### <a name="mro-on-rhel"></a>MRO in RHEL

```bash
# Import the Microsoft repository key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Create local `azure-cli` repository
sudo sh -c 'echo -e "[azure-cli]\nname=Azure CLI\nbaseurl=https://packages.microsoft.com/yumrepos/azure-cli\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/azure-cli.repo'

# Set the location of the package repo at the "prod" directory
# The following command is for version 7.x
# For 6.x, replace 7 with 6 to get that version
rpm -Uvh https://packages.microsoft.com/config/rhel/7/packages-microsoft-prod.rpm
```
#### <a name="mro-on-suse"></a>MRO in SUSE

```bash
# Install as root
sudo su

# Set the location of the package repo at the "prod" directory containing the distribution
# This example is for SLES12, the only supported version of SUSE in Machine Learning Server
zypper ar -f https://packages.microsoft.com/sles/12/prod packages-microsoft-com

# Update packages on your system:
zypper update
```

## <a name="package-list"></a>Elenco dei pacchetti

In un dispositivo connesso a internet, i pacchetti vengono scaricati e installati indipendentemente dal motore di database mediante il programma di installazione del pacchetto per ogni sistema operativo. La tabella seguente descrive tutti i pacchetti disponibili, ma per le installazioni connesso a internet, è sufficiente *uno* pacchetto R o Python per ottenere una specifica combinazione di funzionalità.

| Nome pacchetto | Si applica a | Description |
|--------------|----------|-------------|
|MSSQL-server-extensibility  | All | Framework di estendibilità utilizzato per eseguire codice R, Python o Java. |
|MSSQL-server-extensibility-java | Java | Estensione di Java per il caricamento di un ambiente di esecuzione di Java. Non esistono altre librerie o pacchetti per Java. |
| Microsoft-openmpi  | Python, R | Interfaccia utilizzata dalle librerie Revo * per la parallelizzazione in Linux di passaggio dei messaggi. |
| [Microsoft-r-open *](#mro) | R | Distribuzione open source di R, è costituito da tre pacchetti. |
| MSSQL-mlservices-python | Python | Distribuzione di open source di Python e Anaconda. |
|MSSQL-mlservices-mlm-py  | Python | Installazione completa. Fornisce revoscalepy, microsoftml, pre-training di modelli per l'analisi del sentiment definizione delle funzionalità e il testo di immagine.| 
|MSSQL-mlservices-mml-py  | Python | Installazione parziale. Fornisce revoscalepy, microsoftml. <br/>Esclude i modelli con training preliminare. | 
|MSSQL-mlservices-package-py  | Python | Installazione parziale. Fornisce revoscalepy. <br/>Esclude microsoftml e modelli con training preliminare. | 
|MSSQL-mlservices-mlm-r  | R | Installazione completa. Fornisce RevoScaleR, MicrosoftML, sqlRUtils, olapR, pre-training di modelli per l'analisi del sentiment definizione delle funzionalità e il testo di immagine.| 
|MSSQL-mlservices-mml-r  | R | Installazione parziale. Fornisce RevoScaleR, MicrosoftML, sqlRUtils, olapR. <br/>Esclude i modelli con training preliminare.  |
|MSSQL-mlservices pacchetti r  | R | Installazione parziale. Fornisce RevoScaleR, sqlRUtils, olapR. <br/>Esclude MicrosoftML e modelli con training preliminare. | 

<a name="RHEL"></a>

## <a name="rhel-commands"></a>Comandi RHEL

Installare qualunque *uno* pacchetto R e gli eventuali *uno* pacchetto Python e Java se si desidera che tale funzionalità. Ogni pacchetto R e Python include un'aggregazione di funzionalità. Scegliere il pacchetto che fornisce il set di funzionalità che è necessario. I pacchetti dipendenti vengono inclusi automaticamente.

> [!Tip]
> Se possibile, eseguire `yum clean all` per aggiornare i pacchetti nel sistema prima dell'installazione.

### <a name="example-1----full-installation"></a>Esempio 1: installazione completa 

Include open source R e Python, il framework di estendibilità, microsoft-openmpi, le estensioni (R, Python, Java), con librerie di machine learning e i modelli con training preliminare per R e Python. Per R e Python, se si desidera che un elemento tra completi e minimi di installazione - ad esempio librerie di machine learning, ma senza i modelli con training preliminare - sostituire `mssql-mlservices-mml-r-9.4.5*` e `mssql-mlservices-mml-py-9.4.5*` invece.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.5* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.5*
sudo yum install mssql-mlservices-mlm-r-9.4.5* 
sudo yum install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Esempio 2: installazione minima 

Include librerie open source R e Python, il framework di estendibilità, microsoft-openmpi, core Revo * per R e Python, Java extension. Esclude i modelli con training preliminare e librerie di machine learning per R e Python. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.5* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.5*
sudo yum install mssql-mlservices-packages-r-9.4.5*
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

## <a name="ubuntu-commands"></a>Comandi di Ubuntu

Installare qualunque *uno* pacchetto R e gli eventuali *uno* pacchetto Python e Java se si desidera che tale funzionalità. Ogni pacchetto R e Python include un'aggregazione di funzionalità. Scegliere il pacchetto che fornisce il set di funzionalità che è necessario. I pacchetti dipendenti vengono inclusi automaticamente.

> [!Tip]
> Se possibile, eseguire `apt-get update` per aggiornare i pacchetti nel sistema prima dell'installazione. Inoltre, alcune immagini docker di Ubuntu potrebbero non avere l'opzione di apt trasporto https. Per installarlo, usare `apt-get install apt-transport-https`.

<!---
### Prerequisite for 18.04

Running mssql-mlservices R libraries on Ubuntu 18.04 requires **libpng12** from the Linux Kernel archives. This package is no longer included in the standard distribution and must be installed manually. To get this library, run the following commands:

```bash
wget https://mirrors.kernel.org/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.54-1ubuntu1_amd64.deb
dpkg -i libpng12-0_1.2.54-1ubuntu1_amd64.deb
```--->

### <a name="example-1----full-installation"></a>Esempio 1: installazione completa 

Include open source R e Python, il framework di estendibilità, microsoft-openmpi, le estensioni (R, Python, Java), con librerie di machine learning e i modelli con training preliminare per R e Python. R e Python, se si desidera che un elemento tra completi e minimi di installazione - ad esempio librerie di machine learning, ma senza i modelli con training preliminare - sostituire mssql-mlservices-mml-r e mssql-mlservices-mml-py.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
sudo apt-get install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Esempio 2: installazione minima 

Include librerie open source R e Python, il framework di estendibilità, microsoft-openmpi, core Revo * per R e Python, Java extension. Esclude i modelli con training preliminare e librerie di machine learning per R e Python. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java
# No aasterisk
sudo apt-get install mssql-mlservices-packages-py
sudo apt-get install mssql-mlservices-packages-r
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

## <a name="suse-commands"></a>Comandi SUSE

Installare qualunque *uno* pacchetto R e gli eventuali *uno* pacchetto Python e Java se si desidera che tale funzionalità. Ogni pacchetto R e Python include un'aggregazione di funzionalità. Scegliere il pacchetto che fornisce il set di funzionalità che è necessario. I pacchetti dipendenti vengono inclusi automaticamente. 

### <a name="example-1----full-installation"></a>Esempio 1: installazione completa 

Include open source R e Python, il framework di estendibilità, microsoft-openmpi, le estensioni (R, Python, Java), con librerie di machine learning e i modelli con training preliminare per R e Python. Per R e Python, se si desidera che un elemento tra completi e minimi di installazione - ad esempio librerie di machine learning, ma senza i modelli con training preliminare - sostituire `mssql-mlservices-mml-r-9.4.5*` e `mssql-mlservices-mml-py-9.4.5*` invece.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.5* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.5*
sudo zypper install mssql-mlservices-mlm-r-9.4.5* 
sudo zypper install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Esempio 2: installazione minima 

Include librerie open source R e Python, il framework di estendibilità, microsoft-openmpi, core Revo * per R e Python, Java extension. Esclude i modelli con training preliminare e librerie di machine learning per R e Python. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.5* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.5*
sudo zypper install mssql-mlservices-packages-r-9.4.5*
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>Configurazione di post-installazione (obbligatorio)

Configurazione aggiuntiva viene eseguito principalmente tramita il [lo strumento mssql-conf](sql-server-linux-configure-mssql-conf.md).


1. Aggiungere l'account utente mssql utilizzato per eseguire il servizio Launchpad di SQL Server.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

2. Accettare il contratto di licenza di R e Python open source. Esistono diversi modi per eseguire questa operazione. Se in precedenza accettati licenza di SQL Server e si siano aggiungendo a questo punto le estensioni R o Python, il comando seguente è il tuo consenso delle condizioni:

  ```bash
  # Run as SUDO or root
  # Use set + EULA 
    sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y
  ```

  Un flusso di lavoro alternativo è che, se non si ha ancora accettato il motore di database di SQL Server contratto di licenza, il programma di installazione rileva mssql-mlservices pacchetti e istruzioni per l'accettazione delle condizioni di licenza quando `mssql-conf setup` viene eseguito. Per altre informazioni sui parametri di condizioni di licenza, vedere [configurare SQL Server con lo strumento mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

3. Riavviare il servizio Launchpad di SQL Server e istanza del motore di database.

  ```bash
  systemctl restart mssql-launchpadd

  systemctl restart mssql-server.service
  ```

4. Abilitare l'esecuzione di script esterni in SQL Server Management Studio o un altro strumento che esegue Transact-SQL. 

  ```bash
  EXEC sp_configure 'external scripts enabled', 1 
  RECONFIGURE WITH OVERRIDE 
  ```

## <a name="verify-installation"></a>Verificare l'installazione

Librerie di R (MicrosoftML, RevoScaleR e ad altri utenti) sono reperibile in `/opt/mssql/mlservices/libraries/RServer`.

Le librerie Python (microsoftml e revoscalepy) sono reperibile in `/opt/mssql/mlservices/libraries/PythonServer`.

Con uno strumento di query di SQL Server, eseguire il comando SQL seguente per testare l'esecuzione di R in SQL Server. Se non viene eseguito lo script, provare a riavviare il servizio, `sudo systemctl restart mssql-server`.

```r
EXEC sp_execute_external_script   
@language =N'R', 
@script=N' 
OutputDataSet <- InputDataSet', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```
 
Eseguire il comando SQL seguente per testare l'esecuzione di Python in SQL Server. 
 
```python
EXEC sp_execute_external_script  
@language =N'Python', 
@script=N' 
OutputDataSet = InputDataSet; 
', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```

<a name="install-all"></a>

## <a name="chained-installation"></a>Installazione concatenato

È possibile installare e configurare il motore di database e servizi di Machine Learning in una procedura mediante l'aggiunta di pacchetti R, Python o Java e i parametri in un comando che installa il motore di database. 

L'esempio seguente è una figura "modello" di un'installazione del pacchetto combinato aspetto usando Gestione pacchetti Yum. Installa il motore di database e aggiunge l'estensione del linguaggio Java, che effettua il pull del pacchetto di framework di estendibilità come dipendenza.

```bash
sudo yum install -y mssql-server mssql-server-extensibility-java 
```

Un esempio espanso con tutte le estensioni (Java, Python, R) è simile alla seguente:

```bash
sudo yum install -y mssql-server mssql-server-extensibility-java mssql-mlservices-packages-r-9.4.5* mssql-mlservices-packages-py-9.4.5*
```

Fatta eccezione per i prerequisiti di R, tutti i pacchetti usati in questo esempio si trovano nello stesso percorso. Aggiunta di R è necessario che si [registrare il repository dei pacchetti r-microsoft-open](#mro) come un passaggio aggiuntivo per ottenere MRO. MRO è un prerequisito per l'estensibilità di R. In un computer connesso a internet, MRO è recuperato e installato automaticamente come parte dell'estensione di R, supponendo che entrambi i repository è stato configurato.

Dopo l'installazione, ricordarsi di usare lo strumento mssql-conf per configurare l'intera installazione e accettare i contratti di licenza. Non accettata EULA per i componenti di R e Python open source viene rilevate automaticamente e viene richiesto di accettare le condizioni, con le condizioni di licenza per SQL Server.

```bash
sudo /opt/mssql/bin/mssql-conf setup MSSQL_PID=Developer 
```

## <a name="unattended-installation"></a>Installazione automatica

Usando il [installazione automatica](https://docs.microsoft.com/sql/linux/sql-server-linux-setup?view=sql-server-2017#unattended) per il motore di Database, aggiungere i pacchetti per mssql-mlservices ed EULA.

È importante ricordare che il programma di installazione o lo strumento mssql-conf richiesta per l'accettazione di contratto di licenza. Se è già configurato il motore di database di SQL Server e accettato le condizioni di licenza, usare uno dei parametri mlservices specifiche condizioni di licenza per le distribuzioni di R e Python open source:

```bash
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml
```

Tutte le possibili permutazioni di accettazione del contratto sono documentate in [configurare SQL Server in Linux con lo strumento mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

## <a name="offline-installation"></a>Installazione offline

Seguire le [installazione Offline](sql-server-linux-setup.md#offline) istruzioni per la procedura di installazione dei pacchetti. Trovare il sito di download e quindi scaricare pacchetti specifici usando l'elenco dei pacchetti riportato di seguito.

> [!Tip]
> Molti degli strumenti di gestione pacchetti forniscono comandi utili per determinano le dipendenze dei pacchetti. Per yum, usare `sudo yum deplist [package]`. Per Ubuntu, utilizzare `sudo apt-get install --reinstall --download-only [package name]` seguita da `dpkg -I [package name].deb`.


#### <a name="download-site"></a>Sito di download

È possibile scaricare i pacchetti da [ https://packages.microsoft.com/ ](https://packages.microsoft.com/). Tutti i pacchetti mlservices per R, Python e Java sono collocati insieme ai pacchetti di motore di database. Versione di base per i pacchetti mlservices è 9.4.5. I pacchetti micrososoft-r-open sono in una cartella diversa.

#### <a name="rhel7-paths"></a>Percorsi RHEL/7

|||
|--|----|
| MSSQL/mlservices pacchetti | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |
| pacchetti r-Microsoft-open | [https://packages.microsoft.com/rhel/7/prod/](https://packages.microsoft.com/rhel/7/prod/) | 


#### <a name="ubuntu1604-paths"></a>Percorsi/Ubuntu 16.04

|||
|--|----|
| MSSQL/mlservices pacchetti | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |
| pacchetti r-Microsoft-open | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/) | 

#### <a name="sles12-paths"></a>Percorsi SLES 12

|||
|--|----|
| MSSQL/mlservices pacchetti | [ https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |
| pacchetti r-Microsoft-open | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

#### <a name="package-list"></a>Elenco dei pacchetti

A seconda le estensioni che si desidera utilizzare, scaricare i pacchetti necessari per una lingua specifica. I nomi file esatti includono informazioni sulla piattaforma, ma i nomi di file riportato di seguito devono essere sufficientemente vicine per determinare i file da ottenere.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000

# R
microsoft-openmpi-3.0.0
microsoft-r-open-foreachiterators-3.4.4
microsoft-r-open-mkl-3.4.4
microsoft-r-open-mro-3.4.4
mssql-mlservices-packages-r-9.4.5
mssql-mlservices-mlm-r-9.4.5
mssql-mlservices-mml-r-9.4.5

# Python
microsoft-openmpi-3.0.0
mssql-mlservices-python-9.4.5
mssql-mlservices-packages-py-9.4.5
mssql-mlservices-mlm-py-9.4.5
mssql-mlservices-mml-py-9.4.5 
```

## <a name="add-more-rpython-packages"></a>Aggiunta di altri pacchetti R o Python 
 
È possibile installare altri pacchetti R e Python e utilizzarli nello script che esegue SQL Server 2019.

### <a name="r-packages"></a>Pacchetti R 
 
1. Avviare una sessione R.

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R 
   ```

2. Installare un pacchetto R chiamato [glue](https://mran.microsoft.com/package/glue) per testare l'installazione del pacchetto.

   ```r
   # install.packages("glue",lib="/opt/mssql/mlservices/libraries/RServer") 
   ```
   In alternativa, è possibile installare un pacchetto R dalla riga di comando 

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R CMD INSTALL -l /opt/mssql/mlservices/libraries/RServer glue_1.1.1.tar.gz 
   ```

3. Importare il pacchetto R in [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

   ```r
   EXEC sp_execute_external_script  
   @language = N'R', 
   @script = N'library(glue)' 
   ```

### <a name="python-packages"></a>Pacchetti Python 
 
1. Installare un pacchetto di Python denominato [httpie](https://httpie.org/) tramite pip. 

   ```python
   # sudo /opt/mssql/mlservices/bin/python/python -m pip install httpie 
   ``` 

2. Importare il pacchetto di Python nelle [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
 
   ```python
   EXEC sp_execute_external_script  
   @language = N'Python',  
   @script = N'import httpie' 
   ```

## <a name="limitations-in-ctp-20"></a>Limitazioni nella versione CTP 2.0

In questa versione CTP presenti le limitazioni seguenti.

+ L'autenticazione implicita non è attualmente disponibile in servizi di Machine Learning in Linux a questo punto, il che significa che non è possibile connettersi al server da uno script in corso di R o Python per accedere a dati o altre risorse. 

+ [CREATE EXTERNAL LIBRARY](../t-sql/statements/create-external-library-transact-sql.md) (per l'archiviazione dei pacchetti R nel database) non è attualmente disponibile in Linux e non supporta Python.  

### <a name="resource-governance"></a>Governance delle risorse

È disponibile la parità tra Linux e Windows per [governance delle risorse](../t-sql/statements/create-external-resource-pool-transact-sql.md) per il pool di risorse esterne, ma le statistiche per [sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) dispone attualmente unità di misura diversa in Linux. Le unità vengono allineati in una versione CTP successiva.
 
| Nome colonna   | Description | Valore in Linux | 
|---------------|--------------|---------------|
|peak_memory_kb | La quantità massima di memoria utilizzata per il pool di risorse. | In Linux, questa statistica è originata dal sottosistema di memoria Cgroup, dove il valore è memory.max_usage_in_bytes |
|write_io_count | Totale scrittura generati dalla reimpostazione delle statistiche di Resource Governor. | In Linux, questa statistica è originata dal sottosistema di blkio Cgroup, dove il valore della riga di scrittura è blkio.throttle.io_serviced | 
|read_io_count | Il totale di lettura generati dalla reimpostazione delle statistiche di Resource Governor. | In Linux, questa statistica è originata dal sottosistema di blkio Cgroup, in cui valore della riga di lettura è blkio.throttle.io_serviced | 
|total_cpu_kernel_ms | CPU utente kernel tempo totale espresso in millisecondi, reimpostazione delle statistiche di Resource Governor. | In Linux, questa statistica è originata dal sottosistema di cpuacct Cgroup, dove il valore nella riga dell'utente è cpuacct.stat |  
|total_cpu_user_ms | Tempo cumulativo della CPU di un utente espresso in millisecondi, reimpostazione delle statistiche di Resource Governor.| In Linux, questa statistica è originata dal sottosistema di cpuacct Cgroup, dove il valore per il valore di riga del sistema è cpuacct.stat | 
|active_processes_count | Il numero di processi esterni in esecuzione al momento della richiesta.| In Linux, questa statistica è originata dal sottosistema dei PID GGroups, dove il valore è pids.current | 

## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori di R possono iniziare a usare alcuni semplici esempi e informazioni di base del funzionamento di R con SQL Server. Per il passaggio successivo, vedere i collegamenti seguenti:

+ [Esercitazione: Eseguire R in T-SQL](../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Esercitazione: Nel database analitica per gli sviluppatori di R](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Gli sviluppatori di Python è possono imparare a usare Python con SQL Server seguendo queste esercitazioni:

+ [Esercitazione: Eseguire Python in T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Esercitazione: Nel database analitica per sviluppatori Python](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Per visualizzare esempi di machine learning basate su scenari reali, vedere [di Machine learning esercitazioni](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).
