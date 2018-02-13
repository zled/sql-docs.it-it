---
title: Installazione automatica per SQL Server su Red Hat Enterprise Linux | Documenti Microsoft
description: Esempio di Script SQL Server - installazione automatica in Red Hat Enterprise Linux
author: edmacauley
ms.author: edmaca
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 67f9d71c2a5bd1f57e270c07028f6e8c0ac036a1
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="sample-unattended-sql-server-installation-script-for-red-hat-enterprise-linux"></a>Esempio: Script di installazione automatica di SQL Server per Red Hat Enterprise Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo script di esempio Bash installa 2017 di SQL Server su Red Hat Enterprise Linux (RHEL) senza input interattivo. Fornisce esempi di installazione del motore di database, gli strumenti da riga di comando di SQL Server, SQL Server Agent e vengono eseguiti i passaggi di post-installazione. Facoltativamente, è possibile installare la ricerca full-text e creare un utente amministratore.

> [!TIP]
> Se non è necessario uno script di installazione automatica, il modo più rapido per installare SQL Server consiste nel seguire il [avvio rapido per Red Hat](quickstart-install-connect-red-hat.md). Per altre informazioni sull'installazione, vedere [Guida all'installazione per SQL Server in Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Prerequisiti

- È necessario almeno 2 GB di memoria per l'esecuzione di SQL Server in Linux.
- Il file system deve essere **XFS** o **EXT4**. Altri file System, ad esempio **BTRFS**, non sono supportati.
- Per altri requisiti di sistema, vedere [requisiti di sistema per SQL Server in Linux](sql-server-linux-setup.md#system).

## <a name="sample-script"></a>Script di esempio
Salvare lo script di esempio in un file e quindi per personalizzarlo, sostituire i valori di variabile nello script. È possibile anche impostare le variabili di scripting come variabili di ambiente, come rimuoverli dal file di script.

```bash
#!/bin/bash -e

# Use the following variables to control your install:

# Password for the SA user (required)
MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>'

# Product ID of the version of SQL server you're installing
# Must be evaluation, developer, express, web, standard, enterprise, or your 25 digit product key
# Defaults to developer
MSSQL_PID='evaluation'

# Install SQL Server Agent (recommended)
SQL_INSTALL_AGENT='y'

# Install SQL Server Full Text Search (optional)
# SQL_INSTALL_FULLTEXT='y'

# Create an additional user with sysadmin privileges (optional)
# SQL_INSTALL_USER='<Username>'
# SQL_INSTALL_USER_PASSWORD='<YourStrong!Passw0rd>'

if [ -z $MSSQL_SA_PASSWORD ]
then
  echo Environment variable MSSQL_SA_PASSWORD must be set for unattended install
  exit 1
fi

echo Adding Microsoft repositories...
sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo

echo Installing SQL Server...
sudo yum install -y mssql-server

echo Running mssql-conf setup...
sudo MSSQL_SA_PASSWORD=$MSSQL_SA_PASSWORD \
     MSSQL_PID=$MSSQL_PID \
     /opt/mssql/bin/mssql-conf -n setup accept-eula

echo Installing mssql-tools and unixODBC developer...
sudo ACCEPT_EULA=Y yum install -y mssql-tools unixODBC-devel

# Add SQL Server tools to the path by default:
echo Adding SQL Server tools to your path...
echo PATH="$PATH:/opt/mssql-tools/bin" >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc

# Optional SQL Server Agent installation:
if [ ! -z $SQL_INSTALL_AGENT ]
then
  echo Installing SQL Server Agent...
  sudo yum install -y mssql-server-agent
fi

# Optional SQL Server Full Text Search installation:
if [ ! -z $SQL_INSTALL_FULLTEXT ]
then
    echo Installing SQL Server Full-Text Search...
    sudo yum install -y mssql-server-fts
fi

# Configure firewall to allow TCP port 1433:
echo Configuring firewall to allow traffic on port 1433...
sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
sudo firewall-cmd --reload

# Example of setting post-installation configuration options
# Set trace flags 1204 and 1222 for deadlock tracing:
#echo Setting trace flags...
#sudo /opt/mssql/bin/mssql-conf traceflag 1204 1222 on

# Restart SQL Server after making configuration changes:
echo Restarting SQL Server...
sudo systemctl restart mssql-server

# Connect to server and get the version:
counter=1
errstatus=1
while [ $counter -le 5 ] && [ $errstatus = 1 ]
do
  echo Waiting for SQL Server to start...
  sleep 5s
  /opt/mssql-tools/bin/sqlcmd \
    -S localhost \
    -U SA \
    -P $MSSQL_SA_PASSWORD \
    -Q "SELECT @@VERSION" 2>/dev/null
  errstatus=$?
  ((counter++))
done

# Display error if connection failed:
if [ $errstatus = 1 ]
then
  echo Cannot connect to SQL Server, installation aborted
  exit $errstatus
fi

# Optional new user creation:
if [ ! -z $SQL_INSTALL_USER ] && [ ! -z $SQL_INSTALL_USER_PASSWORD ]
then
  echo Creating user $SQL_INSTALL_USER
  /opt/mssql-tools/bin/sqlcmd \
    -S localhost \
    -U SA \
    -P $MSSQL_SA_PASSWORD \
    -Q "CREATE LOGIN [$SQL_INSTALL_USER] WITH PASSWORD=N'$SQL_INSTALL_USER_PASSWORD', DEFAULT_DATABASE=[master], CHECK_EXPIRATION=ON, CHECK_POLICY=ON; ALTER SERVER ROLE [sysadmin] ADD MEMBER [$SQL_INSTALL_USER]"
fi

echo Done!
```

## <a name="running-the-script"></a>Esecuzione dello script

Per eseguire lo script

1. Incollare l'esempio in un editor di testo e salvarlo con un nome facili da ricordare, ad esempio `install_sql.sh`.

1. Personalizzare `MSSQL_SA_PASSWORD`, `MSSQL_PID`e una delle variabili da modificare.

1. Contrassegnare lo script come file eseguibile

   ```bash
   chmod +x install_sql.sh
   ```

1. Eseguire lo script

   ```bash
   ./install_sql.sh
   ```

## <a name="understanding-the-script"></a>La comprensione dello script

La prima cosa lo script Bash è impostare alcune variabili.  Può trattarsi di variabili di scripting, come nell'esempio, o le variabili di ambiente.  La variabile ``` MSSQL_SA_PASSWORD ``` è **obbligatorio** dall'installazione di SQL Server, gli altri sono variabili personalizzate create per lo script.  Lo script di esempio esegue i passaggi seguenti:

1. Importare le chiavi pubbliche di Microsoft GPG.

1. Registrare i repository di Microsoft SQL Server e gli strumenti da riga di comando.

1. Aggiornare il repository locale

1. Installare SQL Server

1. Configurare SQL Server con il ```MSSQL_SA_PASSWORD``` e accettare automaticamente il contratto di licenza dell'utente finale.

1. Accettare il contratto di licenza dell'utente finale per gli strumenti da riga di comando di SQL Server, installarli e installare il pacchetto unixodbc-dev automaticamente.

1. Aggiungere il percorso per la facilità di utilizzo di strumenti da riga di comando di SQL Server.

1. Installare SQL Server Agent se la variabile di scripting ```SQL_INSTALL_AGENT``` , in per impostazione predefinita.

1. Se lo si desidera installare la ricerca Full-Text di SQL Server, se la variabile ```SQL_INSTALL_FULLTEXT``` è impostata.

1. Sbloccare la porta 1433 per TCP del firewall di sistema necessarie per connettersi a SQL Server da un altro sistema.

1. Facoltativamente, impostare i flag di traccia per la traccia di deadlock. (richiede rimuovendo le righe)

1. È ora installato SQL Server, per rendere operativa, riavviare il processo.

1. Verificare che SQL Server sia installato correttamente, nascondendolo eventuali messaggi di errore.

1. Creare un nuovo utente amministratore server se ```SQL_INSTALL_USER``` e ```SQL_INSTALL_USER_PASSWORD``` sono entrambe impostate.

## <a name="next-steps"></a>Passaggi successivi

Semplificare più installazioni automatiche e creare uno script Bash autonomo che consente di impostare le variabili di ambiente appropriate.  È possibile rimuovere una delle variabili, lo script di esempio utilizza e inserirli nei propri script Bash.

```bash
#!/bin/bash
export MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>'
export MSSQL_PID='evaluation'
export SQL_INSTALL_AGENT='y'
export SQL_INSTALL_USER='<Username>'
export SQL_INSTALL_USER_PASSWORD='<YourStrong!Passw0rd>'
export SQL_INSTALL_AGENT='y'
```

Eseguire lo script Bash nel modo seguente:
```bash
. ./my_script_name.sh
```

Per ulteriori informazioni su SQL Server in Linux, vedere [SQL Server in Linux Panoramica](sql-server-linux-overview.md).