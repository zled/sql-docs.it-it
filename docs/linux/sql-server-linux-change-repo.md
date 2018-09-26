---
title: Configurare i repository di Linux per SQL Server 2017 e 2019 | Microsoft Docs
description: Controllare e configurare i repository del codice sorgente per 2019 di SQL Server e SQL Server 2017 in Linux. Il repository del codice sorgente riguarda la versione di SQL Server che vengono applicati durante l'installazione e aggiornamento.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/14/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 5aee3ea6a744c15afce8055d153959b8db9ac66d
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713213"
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>Configurare i repository per l'installazione e aggiornamento di SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo articolo descrive come configurare il repository corretto per gli aggiornamenti e le installazioni di SQL Server 2017 e 2019 di SQL Server in Linux.

> [!TIP]
> SQL Server 2019 CTP 2.0 è ora disponibile! Per provarla, consultare questo articolo per configurare la nuova **mssql-server-preview** repository. Quindi installare seguendo le istruzioni riportate nel [Guida all'installazione](sql-server-linux-setup.md).

## <a id="repositories"></a>Repository

Quando si installa SQL Server in Linux, è necessario configurare un repository di Microsoft. Questo repository viene usato per acquisire il pacchetto, motore di database **mssql-server**e i relativi pacchetti di SQL Server. Esistono attualmente tre repository principali:

| Archivio | nome | Description |
|---|---|---|
| **Anteprima (2017)** | **mssql-server** | Repository di SQL Server 2017 CTP e RC (sospeso). |
| **Anteprima (2019)** | **MSSQL-server-preview** | Repository della versione CTP di SQL Server 2019 and RC. |
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

| Archivio | Versione | Comando |
|---|---|---|
| **Anteprima (2019)** | 2019 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

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
| **Anteprima (2017)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **Anteprima (2019)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-preview'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

### <a name="configure-new-repository-sles"></a>Configurare il nuovo repository (SLES)
Configurare il nuovo repository da usare per gli aggiornamenti e installazioni di SQL Server. Usare uno dei comandi seguenti per configurare il repository scelto dall'utente.

| Archivio | Versione | Comando |
|---|---|---|
| **Anteprima (2019)** | 2019 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

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
| **Anteprima (2017)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |
| **Anteprima (2019)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview xenial main'` |
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

### <a name="configure-new-repository-ubuntu"></a>Configurare il nuovo repository (Ubuntu)
Configurare il nuovo repository da usare per gli aggiornamenti e installazioni di SQL Server.

1. Importare le chiavi GPG repository pubblico.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Usare uno dei comandi seguenti per configurare il repository scelto dall'utente.

   | Archivio | Versione | Comando |
   |---|---|---|
   | **Anteprima (2019)** | 2019 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"` |
   | **CU** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. Eseguire **apt-get update**.

   ```bash
   sudo apt-get update
   ```

## <a name="next-steps"></a>Passaggi successivi

Dopo aver configurato il repository corretto, è possibile procedere alla [installare](sql-server-linux-setup.md#platforms) oppure [aggiornare](sql-server-linux-setup.md#upgrade) SQL Server e i relativi pacchetti dal repository di nuovo.

> [!IMPORTANT]
> A questo punto, se si sceglie di usare uno degli articoli di installazione, ad esempio la [guide introduttive](sql-server-linux-setup.md#platforms), tenere presente che già stato configurato il repository di destinazione. Non ripetere questo passaggio nelle esercitazioni. Ciò vale soprattutto se si configura il repository GDR, perché le guide introduttive usano il repository CU.

Per altre informazioni su come installare SQL Server 2017 in Linux, vedere [informazioni aggiuntive sull'installazione per SQL Server in Linux](sql-server-linux-setup.md).