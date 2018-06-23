---
title: Note sulla versione di SQL Server 2017 in Linux | Documenti Microsoft
description: In questo articolo contiene le note sulla versione e alle funzionalità supportate per SQL Server 2017 in esecuzione in Linux. Note sulla versione sono inclusi per la versione più recente e le diverse versioni precedenti.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 06/20/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.openlocfilehash: 4762570a478ca6ba6dcaab5e0f7b3e2984f849cf
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312209"
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Note sulla versione di SQL Server 2017 su Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Le seguenti note sulla versione si applicano a SQL Server 2017 in esecuzione in Linux. In questo articolo viene suddiviso in sezioni per ogni versione. Il rilascio GA ha dettagliate facilità di supporto e i problemi elencati noti. Ogni versione di aggiornamento cumulativo (CU) abbia un collegamento a un articolo di supporto che descrive le modifiche CU nonché i collegamenti a Linux Scarica pacchetto.

## <a name="supported-platforms"></a>Piattaforme supportate

| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 o 7.4 Workstation desktop e Server | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-ubuntu.md) | 
| Motore docker 1.8 + su Windows, Mac o Linux | N/D | [Guida all'installazione](quickstart-install-connect-docker.md) | 

> [!TIP]
> Per altre informazioni, vedere la [requisiti di sistema](sql-server-linux-setup.md#system) for SQL Server in Linux. Per i criteri di supporto più recenti per SQL Server 2017, vedere la [criteri di supporto tecnico per Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Strumenti

La maggior parte degli strumenti client esistenti destinati a SQL Server possono facilmente destinazione SQL Server in esecuzione in Linux. Alcuni strumenti potrebbe essere necessario un requisito di versione specifico per funzionare bene con Linux. Per un elenco completo di strumenti di SQL Server, vedere [utilità per SQL Server e gli strumenti SQL](../tools/overview-sql-tools.md).

## <a name="release-history"></a>Cronologia versioni

Nella tabella seguente elenca la cronologia delle versioni per SQL Server 2017.

| Versione | Versione | Data di rilascio |
|-----|-----|-----|
| [CU8](#CU8) | 14.0.3029.16 | 2018 6 |
| [CU7](#CU7) | 14.0.3026.27 | 2018 5 |
| [CU6](#CU6) | 14.0.3025.34 | 2018 4 |
| [CU5](#CU5) | 14.0.3023.8 | 3-2018 |
| [CU4](#CU4) | 14.0.3022.28 | 2-2018 |
| [CU3](#CU3) | 14.0.3015.40 | 1-2018 |
| [CU2](#CU2) | 14.0.3008.27 | 11-2017 |
| [CU1](#CU1) | 14.0.3006.16 | 10-2017 |
| [GA](#GA) | 14.0.1000.169 | 10-2017 |

## <a id="cuinstall"></a> Come installare gli aggiornamenti cumulativi

Se è stato configurato il repository dell'aggiornamento cumulativo, si otterranno l'aggiornamento cumulativo più recente dei pacchetti di SQL Server quando si eseguono le nuove installazioni. Il repository di aggiornamento cumulativo è il valore predefinito per tutti gli articoli di installazione di pacchetti per SQL Server in Linux. Per ulteriori informazioni sulla configurazione del repository, vedere [Configura repository per SQL Server in Linux](sql-server-linux-change-repo.md).

Se si vengono aggiornare i pacchetti esistenti di SQL Server, eseguiti il comando di aggiornamento appropriato per ogni pacchetto per cui ottenere l'aggiornamento cumulativo più recente. Per istruzioni di aggiornamento specifico per ogni pacchetto, vedere le guide di installazione seguenti:

- [Installare il pacchetto di SQL Server](sql-server-linux-setup.md#upgrade)
- [Installare il pacchetto di ricerca Full-text](sql-server-linux-setup-full-text-search.md)
- [Installare SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Abilitare SQL Server Agent](sql-server-linux-setup-sql-agent.md)

## <a id="CU8"></a> CU8 (maggio 2018)

Questa è la versione di aggiornamento cumulativo 8 (CU8) di SQL Server 2017. La versione del motore di SQL Server per questa versione è 14.0.3029.16. Per informazioni sulle correzioni e miglioramenti in questa versione, vedere [ https://support.microsoft.com/en-us/help/4229789 ](https://support.microsoft.com/en-us/help/4229789).

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni manuali o non in linea il pacchetto, è possibile scaricare i pacchetti RPM e Debian con le informazioni nella tabella seguente:

| Pacchetto | Versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.3029.16-1 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm)</br>[Pacchetto SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.3029.16-1 | [pacchetto RPM motore MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.3029.16-1 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3029.16-1_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3029.16-1_amd64.deb)</br>[Pacchetto Debian ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3029.16-1_amd64.deb)<br/>[Pacchetto SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU7"></a> CU7 (maggio 2018)

Questa è la versione di aggiornamento cumulativo 7 (CU7) di SQL Server 2017. La versione del motore di SQL Server per questa versione è 14.0.3026.27. Per informazioni sulle correzioni e miglioramenti in questa versione, vedere [ https://support.microsoft.com/en-us/help/4229789 ](https://support.microsoft.com/en-us/help/4229789).

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni manuali o non in linea il pacchetto, è possibile scaricare i pacchetti RPM e Debian con le informazioni nella tabella seguente:

| Pacchetto | Versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.3026.27-2 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm)</br>[Pacchetto SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.3026.27-2 | [pacchetto RPM motore MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.3026.27-2 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3026.27-2_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3026.27-2_amd64.deb)</br>[Pacchetto Debian ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3026.27-2_amd64.deb)<br/>[Pacchetto SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU6"></a> CU6 (aprile 2018)

Questa è la versione di aggiornamento cumulativo 6 (CU6) di SQL Server 2017. La versione del motore di SQL Server per questa versione è 14.0.3025.34. Per informazioni sulle correzioni e miglioramenti in questa versione, vedere [ https://support.microsoft.com/help/4101464 ](https://support.microsoft.com/help/4101464).

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni manuali o non in linea il pacchetto, è possibile scaricare i pacchetti RPM e Debian con le informazioni nella tabella seguente:

| Pacchetto | Versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.3025.34-3 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[Pacchetto SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.3025.34-3 | [pacchetto RPM motore MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.3025.34-3 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[Pacchetto Debian ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[Pacchetto SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU5"></a> CU5 (marzo 2018)

Questa è la versione di aggiornamento cumulativo 5 per (CU5) di SQL Server 2017. La versione del motore di SQL Server per questa versione è 14.0.3023.8. Per informazioni sulle correzioni e miglioramenti in questa versione, vedere [ https://support.microsoft.com/help/4092643 ](https://support.microsoft.com/help/4092643).

### <a name="known-upgrade-issue"></a>Problema di aggiornamento noto

Quando esegue l'aggiornamento da una versione precedente a CU5, SQL Server potrebbe non avviarsi con l'errore seguente:

```
Error: 4860, Severity: 16, State: 1.
Cannot bulk load. The file "C:\Install\SqlTraceCollect.dtsx" does not exist or you don't have file access rights.
Error: 912, Severity: 21, State: 2.
Script level upgrade for database 'master' failed because upgrade step 'msdb110_upgrade.sql' encountered error 200, state
```

Per correggere l'errore, abilitare SQL Server Agent e riavviare SQL Server con i comandi seguenti:

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
sudo systemctl start mssql-server
```

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni manuali o non in linea il pacchetto, è possibile scaricare i pacchetti RPM e Debian con le informazioni nella tabella seguente:

| Pacchetto | Versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.3023.8-5 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm)</br>[Pacchetto SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.3023.8-5 | [pacchetto RPM motore MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.3023.8-5 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3023.8-5_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3023.8-5_amd64.deb)</br>[Pacchetto Debian ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3023.8-5_amd64.deb)<br/>[Pacchetto SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU4"></a> CU4 (febbraio 2018)

Questa è la versione di aggiornamento cumulativo 4 (CU4) di SQL Server 2017. La versione del motore di SQL Server per questa versione è 14.0.3022.28. Per informazioni sulle correzioni e miglioramenti in questa versione, vedere [ https://support.microsoft.com/en-us/help/4056498 ](https://support.microsoft.com/en-us/help/4056498).

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni manuali o non in linea il pacchetto, è possibile scaricare i pacchetti RPM e Debian con le informazioni nella tabella seguente:

> [!NOTE]
> A partire da CU4, SQL Server Agent non viene più installato come pacchetto separato. Viene installato con il motore di pacchetto e deve essere abilitato l'utilizzo.

| Pacchetto | Versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.3022.28-2 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm)</br>[Pacchetto SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.3022.28-2 | [pacchetto RPM motore MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.3022.28-2 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3022.28-2_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3022.28-2_amd64.deb)</br>[Pacchetto Debian ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3022.28-2_amd64.deb)<br/>[Pacchetto SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU3"></a> CU3 (gennaio 2018)

Questa è la versione di aggiornamento cumulativo 3 (CU3) di SQL Server 2017. La versione del motore di SQL Server per questa versione è 14.0.3015.40. Per informazioni sulle correzioni e miglioramenti in questa versione, vedere [ https://support.microsoft.com/en-us/help/4052987 ](https://support.microsoft.com/en-us/help/4052987).

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni manuali o non in linea il pacchetto, è possibile scaricare i pacchetti RPM e Debian con le informazioni nella tabella seguente:

| Pacchetto | Versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.3015.40-1 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Pacchetto di SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[Pacchetto SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.3015.40-1 | [pacchetto RPM motore MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Pacchetto di SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.3015.40-1 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[Pacchetto Debian ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[Pacchetto Debian di SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[Pacchetto SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU2"></a> CU2 (novembre 2017)

Questa è la versione di aggiornamento cumulativo 2 (CU2) di SQL Server 2017. La versione del motore di SQL Server per questa versione è 14.0.3008.27. Per informazioni sulle correzioni e miglioramenti in questa versione, vedere [ https://support.microsoft.com/help/4052574 ](https://support.microsoft.com/help/4052574).

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni manuali o non in linea il pacchetto, è possibile scaricare i pacchetti RPM e Debian con le informazioni nella tabella seguente:

| Pacchetto | Versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.3008.27-1 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Pacchetto di SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[Pacchetto SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.3008.27-1 | [pacchetto RPM motore MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Pacchetto di SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.3008.27-1 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[Pacchetto Debian ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[Pacchetto Debian di SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[Pacchetto SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU1"></a> CU1 (ottobre 2017)

Questa è la versione di aggiornamento cumulativo 1 (CU1) di SQL Server 2017. La versione del motore di SQL Server per questa versione è 14.0.3006.16. Per informazioni sulle correzioni e miglioramenti in questa versione, vedere [ https://support.microsoft.com/help/KB4053439 ](https://support.microsoft.com/help/4038634).

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni manuali o non in linea il pacchetto, è possibile scaricare i pacchetti RPM e Debian con le informazioni nella tabella seguente:

| Pacchetto | Versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.3006.16-3 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Pacchetto di SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[Pacchetto SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.3006.16-3 | [pacchetto RPM motore MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Pacchetto di SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.3006.16-3 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[Pacchetto Debian ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[Pacchetto Debian di SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[Pacchetto SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a> Versione GA (ottobre 2017)

Questo è il rilascio GA (General Availability) di SQL Server 2017. La versione del motore di SQL Server per questa versione è 14.0.1000.169.

### <a name="package-details"></a>Dettagli del pacchetto

Nella tabella seguente sono elencati i percorsi di download per i pacchetti RPM e Debian e i dettagli del pacchetto. Si noti che non è necessaria scaricare questi pacchetti direttamente se si utilizza la procedura nelle guide di installazione seguenti:

- [Installare il pacchetto di SQL Server](sql-server-linux-setup.md)
- [Installare il pacchetto di ricerca Full-text](sql-server-linux-setup-full-text-search.md)
- [Installare il pacchetto di SQL Server Agent](sql-server-linux-setup-sql-agent.md)
- [Installare SQL Server Integration Services](sql-server-linux-setup-ssis.md)

| Pacchetto | Versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.1000.169-2 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Pacchetto di SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[Pacchetto SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.1000.169-2 | [pacchetto RPM motore MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Pacchetto di SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.1000.169-2 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[Pacchetto Debian ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[Pacchetto Debian di SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[Pacchetto SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a name="Unsupported"></a> Servizi e funzionalità non supportate

Funzionalità e i servizi seguenti non sono disponibili in Linux al momento del rilascio di disponibilità generale. Il supporto di queste funzionalità sarà sempre abilitato nel corso del tempo.

| Area | Servizio o funzionalità non supportata |
|-----|-----|
| **Motore di database** | Replica transazionale |
| &nbsp; | Replica di tipo merge |
| &nbsp; | Estensione database |
| &nbsp; | PolyBase |
| &nbsp; | Query distribuita con connessioni 3rd party |
| &nbsp; | Server collegati alle origini di dati diverso da SQL Server |
| &nbsp; | Le stored procedure (XP_CMDSHELL e così via) estese di sistema |
| &nbsp; | Filetable, FILESTREAM |
| &nbsp; | Gli assembly CLR con il EXTERNAL_ACCESS o UNSAFE autorizzazione impostata |
| &nbsp; | Estensione pool di buffer |
| **SQL Server Agent** |  Sottosistemi: CmdExec, PowerShell, agente di lettura coda, SSIS, SSAS, SSRS |
| &nbsp; | Avvisi |
| &nbsp; | Agente di lettura log |
| &nbsp; | Change Data Capture |
| &nbsp; | Backup gestito |
| **Disponibilità elevata** | Mirroring del database  |
| **Security** | Extensible Key Management |
| &nbsp; | Autenticazione di Active Directory per i server collegati | 
| &nbsp; | Autenticazione di Active Directory per i gruppi di disponibilità (estensivi) | 
| &nbsp; | strumenti di terze parti AD 3rd (Centrify, Vintela, Powerbroker) | 
| **Services** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |
| &nbsp; | Distributed Transaction Coordinator (DTC) |

## <a name="known-issues"></a>Problemi noti

Nelle sezioni seguenti vengono descritti i problemi noti con la versione GA (General Availability) di SQL Server 2017 in Linux.

#### <a name="general"></a>Generale

- Gli aggiornamenti per il rilascio GA di SQL Server 2017 sono supportati solo da CTP 2.1 o versione successiva. 

- La lunghezza del nome host in cui SQL Server è necessario installato a 15 caratteri o meno. 

    - **Risoluzione**: modificare il nome/e così via/nome host e un valore 15 caratteri lunghi o meno.

- Manualmente viene impostata l'ora di sistema all'indietro nel tempo saranno SQL Server arrestare l'aggiornamento dell'ora di sistema interno all'interno di SQL Server.

    - **Risoluzione**: riavviare SQL Server.

- Sono supportate solo le installazioni di istanza singola.

    - **Risoluzione**: se si desidera disporre di più di un'istanza in un determinato host, è consigliabile utilizzare le macchine virtuali o i contenitori di Docker. 

- Gestione configurazione SQL Server non è possibile connettersi a SQL Server in Linux.

- La lingua predefinita del **sa** account di accesso è impostata sull'inglese.

    - **Risoluzione**: modificare la lingua del **sa** account di accesso con le **ALTER LOGIN** istruzione.

#### <a name="databases"></a>Database

- Impossibile spostare il database master con l'utilità mssql-conf. Altri database di sistema possono essere spostati con conf mssql

- Quando si ripristina un database di cui è stato eseguito il backup in SQL Server in Windows, è necessario usare il **WITH MOVE** clausola nell'istruzione Transact-SQL.

- Le transazioni distribuite che richiedono il servizio Microsoft Distributed Transaction Coordinator non sono supportate in SQL Server in esecuzione in Linux. SQL Server a SQL Server sono supportati server collegati a meno che non sono dovuti a DTC. Per altre informazioni, vedere [le transazioni distribuite che richiedono il servizio Microsoft Distributed Transaction Coordinator non sono supportate in SQL Server in esecuzione in Linux](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/).

- Determinati algoritmi (pacchetti di crittografia) per Transport Layer Security (TLS) non funzionano correttamente con SQL Server in Linux. Di conseguenza gli errori di connessione quando si tenta di connettersi a SQL Server, nonché problemi di attivazione delle connessioni tra repliche di gruppi di disponibilità elevata.

   - **Risoluzione**: modificare il **mssql.conf** script di configurazione per SQL Server in Linux per disabilitare i pacchetti di crittografia problematico, eseguendo le operazioni seguenti:

      1. Aggiungere quanto segue per /var/opt/mssql/mssql.conf.

      ```
      [network]
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. Riavviare SQL Server con il comando seguente.

      ```bash
      sudo systemctl restart mssql-server
      ```

- Database di SQL Server 2014 in Windows che utilizzano OLTP In memoria non possono essere ripristinati in SQL Server 2017 in Linux. Per ripristinare un database di SQL Server 2014 che utilizza OLTP in memoria, aggiornare i database a SQL Server 2016 o 2017 di SQL Server in Windows prima di spostarli in SQL Server in Linux tramite backup e ripristino o scollegare o collegare.

- Autorizzazione dell'utente **ADMINISTER BULK OPERATIONS** , in questo momento, non è supportata in Linux.

#### <a name="networking"></a>Funzionalità di rete

Funzionalità che coinvolgono le connessioni TCP in uscita dal processo sqlservr, ad esempio i server collegati o gruppi di disponibilità, potrebbe non funzionare se vengono soddisfatte entrambe le condizioni seguenti:

1. Il server di destinazione viene specificato come un nome host e non un indirizzo IP.

1. L'istanza di origine ha disabilitato nel kernel di IPv6. Per verificare che se il sistema con IPv6 abilitato nel kernel di, è necessario passare tutti i test seguenti:

   - `cat /proc/cmdline` verrà stampata la riga di comando di avvio del kernel corrente. L'output non deve contenere `ipv6.disable=1`.
   - Sys/proc / / net/ipv6/directory deve esistere.
   - Un programma C che chiama `socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` dovrebbe avere esito positivo - syscall deve restituire un fd! = -1 e non avere esito negativo con EAFNOSUPPORT.

L'errore esatto dipende la funzionalità. Per i server collegati, questa situazione si manifesta come un errore di timeout di accesso. Per i gruppi di disponibilità, il `ALTER AVAILABILITY GROUP JOIN` DDL per la replica secondaria avrà esito negativo dopo 5 minuti con un errore di timeout di configurazione di download.

Per risolvere questo problema, effettuare una delle operazioni seguenti:

1. Utilizzare gli indirizzi IP anziché i nomi host per specificare la destinazione della connessione TCP.

1. Abilitare il protocollo IPv6 nel kernel di rimuovendo `ipv6.disable=1` dalla riga di comando di avvio. Il modo per eseguire questa operazione varia a seconda la distribuzione di Linux e il caricatore di avvio, ad esempio grub. Se si desidera IPv6 deve essere disabilitata, è comunque possibile disabilitarlo impostando `net.ipv6.conf.all.disable_ipv6 = 1` nella `sysctl` configurazione (ad esempio `/etc/sysctl.conf`). Questo verrà comunque impedire che un indirizzo IPv6 scheda di rete del sistema, ma consentire il funzionamento delle funzionalità sqlservr.

#### <a name="network-file-system-nfs"></a>Network File System (NFS)
Se si utilizza **File System NFS (Network)** condivisioni remote nell'ambiente di produzione, tenere presente i requisiti di supporto seguenti:

- Utilizzare la versione NFS **4.2 o versioni successive**. Le versioni precedenti di NFS non supportano le funzionalità necessarie, ad esempio fallocate e la creazione di file sparse, comune a sistemi di file più recenti.
- Individuare solo i **/var/opt/mssql** le directory di montaggio NFS. Altri file, ad esempio i file binari del sistema di SQL Server, non sono supportati.
- Assicurarsi che i client NFS utilizzino l'opzione 'nolock' durante il montaggio di tale condivisione.

#### <a name="localization"></a>Localizzazione

- Se le impostazioni locali non in lingua inglese (it_IT) durante l'installazione, è necessario utilizzare la codifica UTF-8 nella sessione/terminal bash. Se si utilizza la codifica ASCII, si potrebbe essere visualizzato un errore simile al seguente:

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Se non è possibile utilizzare la codifica UTF-8, eseguire l'installazione utilizzando la variabile di ambiente MSSQL_LCID per specificare il linguaggio selezionato.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- Quando esegue l'installazione mssql-conf e l'esecuzione di un'installazione diversa dall'inglese di SQL Server, non corretto caratteri estesi vengono visualizzati dopo il testo localizzato, "Configurazione di Server SQL...". O, per le installazioni di base non latini, contiene la frase potrebbe non essere presente completamente. Contiene la frase manca deve visualizzare la stringa localizzata seguente: "il PID licenze è stato elaborato correttamente.  La nuova edizione è [\<nome\> edizione] ". Questa stringa viene restituita solo per scopi informativi e al successivo aggiornamento cumulativo di SQL Server si occuperanno per tutte le lingue. Questa operazione non influenza la corretta installazione di SQL Server in alcun modo. 

#### <a name="full-text-search"></a>Ricerca full-text

- Non tutti i filtri sono disponibili in questa versione, inclusi i filtri per i documenti di Office. Per un elenco di filtri supportati, vedere [installazione di ricerca Full-Text di SQL Server in Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- Il **mssql server è** pacchetto non è supportato in SUSE in questa versione. Poiché è attualmente supportato in Ubuntu e su Red Hat Enterprise Linux (RHEL).

- Con SSIS in Linux CTP 2.1 Aggiorna e versioni successive, i pacchetti SSIS possono usare connessioni ODBC in Linux. Questa funzionalità è stata testata con il driver ODBC di MySQL e SQL Server, ma anche dovrebbe funzionare con qualsiasi driver ODBC Unicode che osserva la specifica ODBC. In fase di progettazione, è possibile fornire un DSN o una stringa di connessione per connettersi ai dati ODBC; è inoltre possibile utilizzare l'autenticazione di Windows. Per altre informazioni, vedere la [post di blog annuncia il supporto ODBC in Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Le funzionalità seguenti non sono supportate in questa versione, quando si eseguono i pacchetti SSIS in Linux:
  - Database del catalogo SSIS
  - Esecuzione del pacchetto pianificato dall'agente SQL
  - Autenticazione di Windows
  - Componenti di terze parti
  - Change Data Capture (CDC)
  - SSIS con scalabilità orizzontale
  - Azure Feature Pack per SSIS
  - Supporto di Hadoop e HDFS
  - Microsoft Connector for SAP BW

Per un elenco di componenti SSIS predefiniti che non sono attualmente supportati o supportati con limitazioni, vedere [limitazioni e problemi noti per SSIS in Linux](sql-server-linux-ssis-known-issues.md#components).

Per ulteriori informazioni su SSIS in Linux, vedere gli articoli seguenti:
-   [Post di blog che notificano supporto SSIS per Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Installare SQL Server Integration Services (SSIS) in Linux](sql-server-linux-setup-ssis.md)
-   [Estrarre, trasformare e caricare i dati in Linux con SSIS](sql-server-linux-migrate-ssis.md)

#### <a name="-a-idssmsa-sql-server-management-studio-ssms"></a>< un id = "ssms" ></a> SQL Server Management Studio (SSMS)

Le limitazioni seguenti si applicano a SQL Server Management Studio in Windows connessi a SQL Server in Linux.

- I piani di manutenzione non sono supportati.

- Gestione dei Data Warehouse (data warehouse di gestione) e l'agente di raccolta dati in SSMS non sono supportati. 

- I componenti SSMS UI con l'autenticazione di Windows o le opzioni di registro eventi di Windows non funzionano con Linux. È comunque possibile usare queste funzionalità con altre opzioni, ad esempio account di accesso SQL. 

- Numero di file di log da mantenere non può essere modificato.

## <a name="next-steps"></a>Passaggi successivi

Per un'introduzione, vedere la Guida introduttiva di seguenti:

- [Installare su Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)
- [Eseguire il provisioning di una macchina virtuale SQL in Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)
- [Esecuzione e connessione - Cloud](quickstart-install-connect-clouds.md)

Per le risposte alle domande frequenti, vedere la [SQL Server in domande frequenti su Linux](sql-server-linux-faq.md).
