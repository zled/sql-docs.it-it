---
title: Configurare i repository per SQL Server in Linux | Microsoft Docs
description: Controllare e configurare i repository del codice sorgente per SQL Server 2017 in Linux. Il repository del codice sorgente riguarda la versione di SQL Server che vengono applicati durante l'installazione e aggiornamento.
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
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38006083"
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>Configurare i repository per l'installazione e aggiornamento di SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo articolo descrive come configurare il repository corretto per gli aggiornamenti e le installazioni di SQL Server 2017 in Linux.

> [!IMPORTANT]
> Se è stata installata una versione CTP o una versione RC di SQL Server 2017, è necessario utilizzare i passaggi descritti in questo articolo per registrare un repository GA (General Availability) e aggiornare o reinstallare. Versioni di anteprima di SQL Server 2017 non sono supportate e scadranno.

## <a id="repositories"></a>Repository

Quando si installa SQL Server in Linux, è necessario configurare un repository di Microsoft. Questo repository viene usato per acquisire il pacchetto, motore di database **mssql-server**e i relativi pacchetti di SQL Server. Esistono attualmente tre repository principali:

| Archivio | nome | Description |
|---|---|---|
| **Anteprima** | **mssql-server** | Repository di anteprima per le versioni di SQL Server CTP e RC. Questo repository non è supportato per SQL Server 2017. |
| **CU** | **mssql-server-2017** | Repository di SQL Server 2017 Update (Cumulativo). |
| **GDR** | **mssql-server-2017-gdr** | Repository di SQL Server 2017 GDR per gli aggiornamenti critici. |

## <a id="cuversusgdr"></a> Aggiornamento cumulativo rispetto a GDR

È importante notare che esistono due tipi principali di repository per ogni distribuzione:

- **Gli aggiornamenti cumulativi (CU)**: l'aggiornamento cumulativo (CU) repository contiene i pacchetti per la versione di SQL Server base e le correzioni di bug o miglioramenti dopo tale versione. Gli aggiornamenti cumulativi sono specifici di una versione di rilascio, ad esempio SQL Server 2017. Essi vengono rilasciati cadenza regolare.

- **GDR**: GDR il repository contiene i pacchetti di base versione di SQL Server e solo per gli aggiornamenti critici e aggiornamenti della sicurezza dopo tale versione. Questi aggiornamenti vengono aggiunti anche alla versione di aggiornamento Cumulativo successiva.

Ogni versione di unità di capacità e GDR contiene il pacchetto di SQL Server completo e tutti gli aggiornamenti precedenti per il repository. L'aggiornamento da una versione GDR a una versione aggiornamento Cumulativo è supportata da modifica repository configurato per SQL Server. È anche possibile [effettuare il downgrade](sql-server-linux-setup.md#rollback) a qualsiasi versione all'interno di versione principale (ad esempio: 2017).

> [!NOTE]
> È possibile aggiornare da una versione GDR a CU rilasciare in qualsiasi momento modificando i repository. L'aggiornamento da un aggiornamento Cumulativo versione a una versione GDR non è supportata. 

## <a id="configure"></a> Configurare un repository

Le sezioni seguenti descrivono come verificare e configurare un repository per le piattaforme supportate seguenti:

- [Red Hat Enterprise Server](#rhel)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#sles)

## <a id="rhel"></a> Configurare i repository RHEL
Usare la procedura seguente per configurare i repository in Red Hat Enterprise Server (RHEL).

### <a name="check-for-previously-configured-repositories-rhel"></a>Verificare la presenza di repository configurato in precedenza (RHEL)
Prima di tutto verificare se è già stato registrato un repository di SQL Server.

1. Visualizzare i file nei **/etc/yum.repos.d** directory con il comando seguente:

   ```bash
   sudo ls /etc/yum.repos.d
   ```

2. Cercare un file che consente di configurare la directory di SQL Server, ad esempio **mssql-server.repo**.

3. Stampare il contenuto del file.

   ```bash
   sudo cat /etc/yum.repos.d/mssql-server.repo
   ```

4. Il **nome** proprietà è il repository configurato. Sarà possibile identificare la tabella nel [repository](#repositories) sezione di questo articolo.

### <a name="remove-old-repository-rhel"></a>Rimuovere i vecchi repository (RHEL)
Se necessario, rimuovere il repository precedente con il comando seguente.

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Questo comando dà per scontato che il file identificato nella sezione precedente è stato denominato **mssql-server.repo**.

### <a name="configure-new-repository-rhel"></a>Configurare il nuovo repository (RHEL)
Configurare il nuovo repository da usare per gli aggiornamenti e installazioni di SQL Server. Usare uno dei comandi seguenti per configurare il repository scelto dall'utente.

| Archivio | Comando |
|---|---|
| **CU** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

## <a id="sles"></a> Configurare i repository SLES
Usare la procedura seguente per configurare i repository in SLES.

### <a name="check-for-previously-configured-repositories-sles"></a>Verificare la presenza di repository configurato in precedenza (SLES)
Prima di tutto verificare se è già stato registrato un repository di SQL Server.

1. Uso **zypper info** per ottenere informazioni su tutti i repository configurata in precedenza.

   ```bash
   sudo zypper info mssql-server
   ```

2. Il **Repository** proprietà è il repository configurato. Sarà possibile identificare la tabella nel [repository](#repositories) sezione di questo articolo.

### <a name="remove-old-repository-sles"></a>Rimuovere i vecchi repository (SLES)
Se necessario, rimuovere il repository precedente. Usare uno dei comandi seguenti in base al tipo di repository configurato in precedenza.

| Archivio | Comando da rimuovere |
|---|---|
| **Anteprima** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

### <a name="configure-new-repository-sles"></a>Configurare il nuovo repository (SLES)
Configurare il nuovo repository da usare per gli aggiornamenti e installazioni di SQL Server. Usare uno dei comandi seguenti per configurare il repository scelto dall'utente.

| Archivio | Comando |
|---|---|
| **CU** | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

## <a id="ubuntu"></a> Configurare i repository di Ubuntu
Usare la procedura seguente per configurare i repository in Ubuntu.

### <a name="check-for-previously-configured-repositories-ubuntu"></a>Verificare la presenza di repository configurato in precedenza (Ubuntu)
Prima di tutto verificare se è già stato registrato un repository di SQL Server.

1. Visualizzare il contenuto del **/etc/apt/sources.list** file.

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Esaminare l'URL del pacchetto mssql-server. Sarà possibile identificare la tabella nel [repository](#repositories) sezione di questo articolo.

### <a name="remove-old-repository-ubuntu"></a>Rimuovere i vecchi repository (Ubuntu)
Se necessario, rimuovere il repository precedente. Usare uno dei comandi seguenti in base al tipo di repository configurato in precedenza.

| Archivio | Comando da rimuovere |
|---|---|
| **Anteprima** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` 
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

### <a name="configure-new-repository-ubuntu"></a>Configurare il nuovo repository (Ubuntu)
Configurare il nuovo repository da usare per gli aggiornamenti e installazioni di SQL Server.

1. Importare le chiavi GPG repository pubblico.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Usare uno dei comandi seguenti per configurare il repository scelto dall'utente.

   | Archivio | Comando |
   |---|---|
   | **CU** | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. Eseguire **apt-get update**.

   ```bash
   sudo apt-get update
   ```

## <a name="next-steps"></a>Passaggi successivi

Dopo aver configurato il repository corretto, è possibile procedere alla [installare](sql-server-linux-setup.md#platforms) oppure [aggiornare](sql-server-linux-setup.md#upgrade) SQL Server e i relativi pacchetti dal repository di nuovo.

> [!IMPORTANT]
> A questo punto, se si sceglie di usare uno degli articoli di installazione, ad esempio la [guide introduttive](sql-server-linux-setup.md#platforms), tenere presente che già stato configurato il repository di destinazione. Non ripetere questo passaggio nelle esercitazioni. Ciò vale soprattutto se si configura il repository GDR, perché le guide introduttive usano il repository CU.

Per altre informazioni su come installare SQL Server 2017 in Linux, vedere [informazioni aggiuntive sull'installazione per SQL Server in Linux](sql-server-linux-setup.md).
