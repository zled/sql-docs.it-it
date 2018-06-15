---
title: Configurare repository per SQL Server in Linux | Documenti Microsoft
description: Controllare e configurare il repository di origine per 2017 di SQL Server in Linux. Repository di origine riguarda la versione di SQL Server in cui viene applicata durante l'installazione e aggiornamento.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/14/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 63cb2f56852a668bc48aa85cd31a72a2b583463b
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34323372"
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>Configurare repository per l'installazione e aggiornamento di SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questo articolo viene descritto come configurare il repository corretto per gli aggiornamenti e le installazioni di SQL Server 2017 in Linux.

> [!IMPORTANT]
> Se si è precedentemente installato una versione CTP o versione RC di SQL Server 2017, è necessario utilizzare i passaggi in questo articolo per registrare un repository GA (General Availability) e di aggiornare o reinstallare. Le versioni di anteprima di SQL Server 2017 non sono supportate e scadranno.

## <a id="repositories"></a>Repository

Quando si installa SQL Server in Linux, è necessario configurare un repository di Microsoft. Questo archivio viene usato per acquisire il pacchetto di motore di database, **mssql server**e i relativi pacchetti di SQL Server. Esistono attualmente tre repository principale:

| Archivio | Nome | Description |
|---|---|---|
| **Anteprima** | **mssql-server** | Repository di anteprima per le versioni di SQL Server CTP e RC. Questo repository non è supportato per SQL Server 2017. |
| **CU** | **mssql-server-2017** | Repository di SQL Server 2017 Cumulative Update (CU). |
| **GDR** | **mssql-server-2017-gdr** | Repository di SQL Server 2017 GDR per gli aggiornamenti critici. |

## <a id="cuversusgdr"></a> Aggiornamento cumulativo e GDR

È importante notare che esistono due tipi principali di repository per ogni distribuzione:

- **Gli aggiornamenti cumulativi (CU)**: l'aggiornamento cumulativo (CU) repository contiene i pacchetti per la versione di SQL Server base ed eventuali correzioni o miglioramenti Release. Gli aggiornamenti cumulativi sono specifici di una versione di rilascio, ad esempio SQL Server 2017. Essi vengono rilasciati a un ritmo regolare.

- **GDR**: GDR il repository contiene i pacchetti per la versione di SQL Server base solo gli aggiornamenti critici e aggiornamenti della sicurezza perché tale versione. Questi aggiornamenti vengono inoltre aggiunti alla versione di aggiornamento Cumulativo successiva.

Ogni versione CU e GDR contiene il pacchetto di SQL Server completo e tutti gli aggiornamenti precedenti per il repository. L'aggiornamento da una versione GDR a una versione aggiornamento Cumulativo è supportato modificando il repository configurato per SQL Server. È anche possibile [effettuare il downgrade](sql-server-linux-setup.md#rollback) per qualsiasi versione entro il numero di versione principale (ad esempio: 2017).

> [!NOTE]
> È possibile aggiornare da una versione GDR a CU rilasciare in qualsiasi momento modificando repository. L'aggiornamento da un pacchetto CU versione a una versione GDR non è supportata. 

## <a id="configure"></a> Configurare un repository

Le sezioni seguenti descrivono come verificare e configurare un repository per le piattaforme supportate seguenti:

- [Red Hat Enterprise Server](#rhel)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#sles)

## <a id="rhel"></a> Configurare il repository RHEL
Utilizzare la procedura seguente per configurare repository in Red Hat Enterprise Server (RHEL).

### <a name="check-for-previously-configured-repositories-rhel"></a>Verificare la presenza di repository configurate in precedenza (RHEL)
Verificare innanzitutto se è già stato registrato un repository di SQL Server.

1. Visualizzare i file di **/etc/yum.repos.d** directory con il comando seguente:

   ```bash
   sudo ls /etc/yum.repos.d
   ```

2. Cercare un file che configura la directory di SQL Server, ad esempio **mssql server.repo**.

3. Stampare il contenuto del file.

   ```bash
   sudo cat /etc/yum.repos.d/mssql-server.repo
   ```

4. Il **nome** proprietà è il repository configurato. Sarà possibile identificare con la tabella di [repository](#repositories) sezione di questo articolo.

### <a name="remove-old-repository-rhel"></a>Rimuovere il repository precedente (RHEL)
Se necessario, rimuovere il vecchio repository con il comando seguente.

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Questo comando si presuppone che il file identificato nella sezione precedente è stata **mssql server.repo**.

### <a name="configure-new-repository-rhel"></a>Configurare di nuovo repository (RHEL)
Configurare il nuovo repository da utilizzare per gli aggiornamenti e installazioni di SQL Server. Utilizzare uno dei comandi seguenti per configurare il repository di propria scelta.

| Archivio | Comando |
|---|---|
| **CU** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

## <a id="sles"></a> Configurare il repository SLES
Utilizzare la procedura seguente per configurare i repository nel SLES.

### <a name="check-for-previously-configured-repositories-sles"></a>Verificare la presenza di repository configurate in precedenza (SLES)
Verificare innanzitutto se è già stato registrato un repository di SQL Server.

1. Utilizzare **zypper info** per ottenere informazioni su qualsiasi repository configurate in precedenza.

   ```bash
   sudo zypper info mssql-server
   ```

2. Il **Repository** proprietà è il repository configurato. Sarà possibile identificare con la tabella di [repository](#repositories) sezione di questo articolo.

### <a name="remove-old-repository-sles"></a>Rimuovere il repository precedente (SLES)
Se necessario, rimuovere il repository precedente. Utilizzare uno dei comandi seguenti in base al tipo di repository configurate in precedenza.

| Archivio | Comando per rimuovere |
|---|---|
| **Anteprima** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

### <a name="configure-new-repository-sles"></a>Configurare di nuovo repository (SLES)
Configurare il nuovo repository da utilizzare per gli aggiornamenti e installazioni di SQL Server. Utilizzare uno dei comandi seguenti per configurare il repository di propria scelta.

| Archivio | Comando |
|---|---|
| **CU** | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

## <a id="ubuntu"></a> Configurare il repository di Ubuntu
Utilizzare la procedura seguente per configurare repository in Ubuntu.

### <a name="check-for-previously-configured-repositories-ubuntu"></a>Verificare la presenza di repository configurate in precedenza (Ubuntu)
Verificare innanzitutto se è già stato registrato un repository di SQL Server.

1. Visualizzare il contenuto del **/etc/apt/sources.list** file.

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Esaminare l'URL del pacchetto per mssql server. Sarà possibile identificare con la tabella di [repository](#repositories) sezione di questo articolo.

### <a name="remove-old-repository-ubuntu"></a>Rimuovere il repository precedente (Ubuntu)
Se necessario, rimuovere il repository precedente. Utilizzare uno dei comandi seguenti in base al tipo di repository configurate in precedenza.

| Archivio | Comando per rimuovere |
|---|---|
| **Anteprima** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` 
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

### <a name="configure-new-repository-ubuntu"></a>Configurare di nuovo repository (Ubuntu)
Configurare il nuovo repository da utilizzare per gli aggiornamenti e installazioni di SQL Server.

1. Importare le chiavi GPG archivio pubblico.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Utilizzare uno dei comandi seguenti per configurare il repository di propria scelta.

   | Archivio | Comando |
   |---|---|
   | **CU** | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. Eseguire **apt get aggiornamento**.

   ```bash
   sudo apt-get update
   ```

## <a name="next-steps"></a>Passaggi successivi

Dopo aver configurato il repository corretto, è possibile procedere a [installare](sql-server-linux-setup.md#platforms) o [aggiornare](sql-server-linux-setup.md#upgrade) SQL Server e i relativi pacchetti dal repository di nuovo.

> [!IMPORTANT]
> A questo punto, se si sceglie di utilizzare uno degli articoli di installazione, ad esempio il [Guide rapide](sql-server-linux-setup.md#platforms), tenere presente che sono già configurate del repository di destinazione. Non ripetere il passaggio nelle esercitazioni. Ciò vale soprattutto se si configura il repository GDR, perché la Guida introduttiva di utilizza il repository CU.

Per ulteriori informazioni su come installare SQL Server 2017 in Linux, vedere [Guida all'installazione per SQL Server in Linux](sql-server-linux-setup.md).
