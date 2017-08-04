---
title: Configurare le impostazioni di SQL Server con le variabili di ambiente | Documenti Microsoft
description: In questo argomento viene descritto come usare le variabili di ambiente per configurare impostazioni specifiche di SQL Server 2017 in Linux.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/21/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 4951f503a7b5c395f86cb6daf2ba705ca69fbd83
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Configurare le impostazioni di SQL Server con le variabili di ambiente in Linux

Per configurare SQL Server 2017 RC2 in Linux, è possibile utilizzare diverse variabili di ambiente diverso. Queste variabili vengono utilizzate in due scenari:

- Per configurare l'installazione iniziale con il `mssql-conf setup` comando.
- Per configurare un nuovo [contenitore di SQL Server in Docker](quickstart-install-connect-docker.md).

> [!TIP]
> Se è necessario configurare SQL Server dopo questi scenari di installazione, vedere [configurare SQL Server in Linux con lo strumento mssql conf](sql-server-linux-configure-mssql-conf.md).

## <a name="environment-variables"></a>Variabili di ambiente

| Variabile di ambiente | Description |
|-----|-----|
| **ACCEPT_EULA** | Accettare il contratto di licenza di SQL Server quando è impostato su un valore (ad esempio, ' Y'). |
| **MSSQL_SA_PASSWORD** | Configurare la password dell'utente amministratore. |
| **MSSQL_PID** | Impostare la chiave di prodotto o edizione di SQL Server. I valori possibili sono: Evaluation, Developer, Express, Web, Standard, Enterprise o un codice product key nel formato # # #-# # #-# # #-# # #-# # #, dove '#' è un numero o una lettera. |
| **MSSQL_LCID** | Imposta l'ID di lingua da usare per SQL Server. Ad esempio 1036 è il francese. |
| **MSSQL_COLLATION** | Imposta le regole di confronto predefinito per SQL Server. Esegue l'override il mapping predefinito degli id di lingua (LCID) per le regole di confronto. |
| **MSSQL_MEMORY_LIMIT_MB** | Imposta la quantità massima di memoria (in MB) che è possibile utilizzare SQL Server. Per impostazione predefinita è 80% della memoria fisica totale. |
| **MSSQL_TCP_PORT** | Configurare la porta TCP in ascolto di SQL Server su (valore predefinito 1433). |
| **MSSQL_IP_ADDRESS** | Impostare l'indirizzo IP. Attualmente, l'indirizzo IP deve essere IPv4 stile (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Impostare il percorso di directory di backup predefinito. |
| **MSSQL_DATA_DIR** | Passare alla directory in cui vengono creati i nuovi file di dati di SQL Server database (con estensione mdf). |
| **MSSQL_LOG_DIR** | Passare alla directory in cui vengono creati i nuovi file di log (ldf) del database di SQL Server. |
| **MSSQL_DUMP_DIR** | Passare alla directory in cui SQL Server verrà depositare il dump della memoria e altri file di risoluzione dei problemi per impostazione predefinita. |
| **MSSQL_ENABLE_HADR** | Abilitare gruppi di disponibilità. |

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
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 --cap-add SYS_PTRACE -p 1234:1234 -d microsoft/mssql-server-linux
```

Se si esegue Docker in Windows, utilizzare la sintassi seguente con le virgolette doppie:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 --cap-add SYS_PTRACE -p 1234:1234 -d microsoft/mssql-server-linux
```

## <a name="next-steps"></a>Passaggi successivi

Per altre impostazioni di SQL Server non è elencate qui, vedere [configurare SQL Server in Linux con lo strumento mssql conf](sql-server-linux-configure-mssql-conf.md).

Per ulteriori informazioni su come installare ed eseguire SQL Server in Linux, vedere [installazione di SQL Server in Linux](sql-server-linux-setup.md).

