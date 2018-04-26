---
title: Configurare le impostazioni di SQL Server con le variabili di ambiente | Documenti Microsoft
description: In questo articolo viene descritto come usare le variabili di ambiente per configurare impostazioni specifiche di SQL Server 2017 in Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: On Demand
ms.openlocfilehash: 393b70d354cdbbb2626fe7f99cdf2c3240b08208
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Configurare le impostazioni di SQL Server con le variabili di ambiente in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Per configurare SQL Server 2017 in Linux, è possibile utilizzare diverse variabili di ambiente diverso. Queste variabili vengono utilizzate in due scenari:

- Per configurare l'installazione iniziale con il `mssql-conf setup` comando.
- Per configurare un nuovo [contenitore di SQL Server in Docker](quickstart-install-connect-docker.md).

> [!TIP]
> Se è necessario configurare SQL Server dopo questi scenari di installazione, vedere [configurare SQL Server in Linux con lo strumento mssql conf](sql-server-linux-configure-mssql-conf.md).

## <a name="environment-variables"></a>Variabili di ambiente

| Variabile di ambiente | Description |
|-----|-----|
| **ACCEPT_EULA** | Accettare il contratto di licenza di SQL Server quando è impostato su un valore (ad esempio, ' Y'). |
| **MSSQL_SA_PASSWORD** | Configurare la password dell'utente amministratore. |
| **MSSQL_PID** | Impostare la chiave di prodotto o edizione di SQL Server. I valori possibili includono: </br></br>**Copia di valutazione**</br>**Developer**</br>**Express**</br>**Web**</br>**Standard**</br>**Enterprise**</br>**Un codice product key**</br></br>Se si specifica un codice product key, deve essere nel formato # # #-# # #-# # #-# # #-# # #, dove '#' è un numero o una lettera.|
| **MSSQL_LCID** | Imposta l'ID di lingua da usare per SQL Server. Ad esempio 1036 è il francese. |
| **MSSQL_COLLATION** | Imposta le regole di confronto predefinito per SQL Server. Esegue l'override il mapping predefinito degli id di lingua (LCID) per le regole di confronto. |
| **MSSQL_MEMORY_LIMIT_MB** | Imposta la quantità massima di memoria (in MB) che è possibile utilizzare SQL Server. Per impostazione predefinita è 80% della memoria fisica totale. |
| **MSSQL_TCP_PORT** | Configurare la porta TCP in ascolto di SQL Server su (valore predefinito 1433). |
| **MSSQL_IP_ADDRESS** | Impostare l'indirizzo IP. Attualmente, l'indirizzo IP deve essere IPv4 stile (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Impostare il percorso di directory di backup predefinito. |
| **MSSQL_DATA_DIR** | Passare alla directory in cui vengono creati i nuovi file di dati di SQL Server database (con estensione mdf). |
| **MSSQL_LOG_DIR** | Passare alla directory in cui vengono creati i nuovi file di log (ldf) del database di SQL Server. |
| **MSSQL_DUMP_DIR** | Passare alla directory in cui SQL Server verrà depositare il dump della memoria e altri file di risoluzione dei problemi per impostazione predefinita. |
| **MSSQL_ENABLE_HADR** | Abilitare il gruppo di disponibilità. Ad esempio, '1' è abilitata, e '0' è disabilitato |
| **MSSQL_AGENT_ENABLED** | Abilitare SQL Server Agent. Ad esempio, è abilitato 'true' e 'false' è disabilitata. Per impostazione predefinita, l'agente è disabilitato.  |
| **MSSQL_MASTER_DATA_FILE** | Imposta il percorso del file di dati del database master. |
| **MSSQL_MASTER_LOG_FILE** | Imposta il percorso del file di log database master. |
| **MSSQL_ERROR_LOG_FILE** | Imposta il percorso dei file di log degli errori. |


## <a name="example-initial-setup"></a>Esempio: la configurazione iniziale

Questo esempio viene eseguito `mssql-conf setup` con configurato le variabili di ambiente. Vengono specificate le variabili di ambiente seguenti:

- **ACCEPT_EULA** accetta il contratto di licenza.
- **MSSSQL_PID** specifica liberamente con licenza Developer Edition di SQL Server per non di produzione.
- **MSSQL_SA_PASSWORD** imposta una password complessa.
- **MSSQL_TCP_PORT** imposta la porta TCP di SQL Server è in ascolto al 1234.

```bash
sudo ACCEPT_EULA='Y' MSSQL_PID='Developer' MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' MSSQL_TCP_PORT=1234 /opt/mssql/bin/mssql-conf setup
```

## <a name="example-docker"></a>Esempio: Docker

Questo comando di docker esempio Usa le seguenti variabili di ambiente per creare un nuovo contenitore 2017 di SQL Server:

- **ACCEPT_EULA** accetta il contratto di licenza.
- **MSSSQL_PID** specifica liberamente con licenza Developer Edition di SQL Server per non di produzione.
- **MSSQL_SA_PASSWORD** imposta una password complessa.
- **MSSQL_TCP_PORT** imposta la porta TCP di SQL Server è in ascolto al 1234. Ciò significa che invece di mapping la porta 1433 (valore predefinito) a una porta di host, la porta TCP personalizzata deve essere mappata con il `-p 1234:1234` comando in questo esempio.

Se si eseguono Docker su Linux/macOS, utilizzare la sintassi seguente con le virgolette singole:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d microsoft/mssql-server-linux:2017-latest
```

Se si esegue Docker in Windows, utilizzare la sintassi seguente con le virgolette doppie:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d microsoft/mssql-server-linux:2017-latest
```

> [!NOTE]
> Il processo di esecuzione delle edizioni di produzione nei contenitori è leggermente diverso. Per altre informazioni, vedere [Run production container images](sql-server-linux-configure-docker.md#production) (Eseguire immagini del contenitore di produzione).

## <a name="next-steps"></a>Passaggi successivi

Per altre impostazioni di SQL Server non è elencate qui, vedere [configurare SQL Server in Linux con lo strumento mssql conf](sql-server-linux-configure-mssql-conf.md).

Per ulteriori informazioni su come installare ed eseguire SQL Server in Linux, vedere [installazione di SQL Server in Linux](sql-server-linux-setup.md).
