---
title: Note sulla versione di anteprima di SQL Server 2019 in Linux | Microsoft Docs
description: Questo articolo contiene le note sulla versione e le funzionalità supportate per l'anteprima di SQL Server 2019 in esecuzione su Linux. Note sulla versione sono incluse per la versione più recente e versioni precedenti.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: b22e52d68c1d2b10005e69e2e70c41e73c173dca
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269834"
---
# <a name="release-notes-for-sql-server-2019-preview-on-linux"></a>Note sulla versione di anteprima di SQL Server 2019 in Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md)]

Le note sulla versione seguenti si applicano all'anteprima di SQL Server 2019 in esecuzione su Linux. Questo articolo viene suddiviso in sezioni per ogni versione. Ogni versione ha un collegamento a un articolo di supporto che descrive il modifiche CU nonché collegamenti a Linux download del pacchetto.

> [!TIP]
> Per altre informazioni sulle nuove funzionalità di Linux di SQL Server 2019, vedere [nuove funzionalità di SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sqllinux).

## <a name="supported-platforms"></a>Piattaforme supportate

| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Desktop, Server e Workstation di Red Hat Enterprise Linux 7.3 o 7.4 | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server versione 12 SP2 | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-ubuntu.md) | 
| Motore docker 1.8 + per Windows, Mac o Linux | N/D | [Guida all'installazione](quickstart-install-connect-docker.md) | 

> [!TIP]
> Per altre informazioni, vedere la [requisiti di sistema](sql-server-linux-setup.md#system) per SQL Server in Linux. Per i criteri di supporto più recenti per SQL Server 2017, vedere la [dei criteri di supporto tecnico per Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Strumenti

La maggior parte degli strumenti client esistenti destinati a SQL Server possono facilmente con destinazione SQL Server in esecuzione su Linux. Alcuni strumenti potrebbero avere un requisito di versione specifico per l'uso con Linux. Per un elenco completo di strumenti di SQL Server, vedere [strumenti di SQL e le utilità per SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>Cronologia versioni

La tabella seguente elenca la cronologia delle versioni per l'anteprima di SQL Server 2019 che nelle versioni CTP.

| Versione               | Versione       | Data di rilascio |
|-----------------------|---------------|--------------|
| [CTP 2.1](#CTP21)     | 15.0.1100.94  | 2018-11-06   |
| [CTP 2.0](#CTP20)     | 15.0.1000.34  | 2018-09-24   |

## <a id="cuinstall"></a> Come installare gli aggiornamenti

Se è stato configurato il repository di anteprima (**mssql-server-preview**), quindi si otterranno i pacchetti di SQL Server CTP più recenti quando si eseguono le nuove installazioni. Se sono necessarie immagini del contenitore Docker, vedere le immagini ufficiali per [Microsoft SQL Server in Linux per il motore Docker](https://hub.docker.com/r/microsoft/mssql-server/). Per altre informazioni sulla configurazione del repository, vedere [configurare i repository per SQL Server in Linux](sql-server-linux-change-repo.md).

Se si aggiornano i pacchetti esistenti di SQL Server, eseguiti il comando di aggiornamento appropriato per ogni pacchetto ottenere l'aggiornamento Cumulativo più recente. Per istruzioni di aggiornamento specifico per ogni pacchetto, vedere le guide di installazione seguenti:

- [Installare il pacchetto di SQL Server](sql-server-linux-setup.md#upgrade)
- [Installare il pacchetto di ricerca Full-text](sql-server-linux-setup-full-text-search.md)
- [Installare SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Installare l'anteprima 2019 di SQL Server R Services di Machine Learning e supporto di Python in Linux](sql-server-linux-setup-machine-learning.md)
- [Abilitare SQL Server Agent](sql-server-linux-setup-sql-agent.md)

## <a id="CTP21"></a> CTP 2.1 (novembre 2018)

Le sezioni seguenti forniscono i percorsi dei pacchetti e problemi noti per la versione CTP 2.1 versione. Per altre informazioni sulle nuove funzionalità per Linux 2019 di SQL Server, vedere la [nuove funzionalità di SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni manuali o offline del pacchetto, è possibile scaricare i pacchetti Debian e RPM con le informazioni nella tabella seguente:

| Pacchetto | Versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto di Red Hat RPM | 15.0.1100.94-1 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[Pacchetto RPM ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[Pacchetto RPM extensibility](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Pacchetto RPM estendibilità Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Pacchetto RPM SLES | 15.0.1100.94-1 | [pacchetto RPM motore MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[Pacchetto RPM ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[Pacchetto RPM extensibility](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Pacchetto RPM estendibilità Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Pacchetto Debian Ubuntu 16.04 | 15.0.1100.94-1 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1100.94-1_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1100.94-1_amd64.deb)</br>[Pacchetto Debian ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1100.94-1_amd64.deb)</br>[Pacchetto Debian extensibility](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1100.94-1_amd64.deb)</br>[Pacchetto Debian estendibilità Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1100.94-1_amd64.deb)|

### <a name="known-issues"></a>Problemi noti

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Attualmente, MSDTC richiede le transazioni per essere non autenticato. Ad esempio, se si usa un server collegato da SQL Server in Windows per SQL Server in Linux o Usa un'applicazione client di Windows per avviare una transazione distribuita con SQL Server in Linux, MSDTC in Windows server/client sarà necessario utilizzare l'opzione "No Autenticazione obbligatoria".

## <a id="CTP20"></a> CTP 2.0 (settembre 2018)

Le sezioni seguenti forniscono i percorsi dei pacchetti e problemi noti per le versioni da CTP 2.0 versione. Per altre informazioni sulle nuove funzionalità per Linux 2019 di SQL Server, vedere la [nuove funzionalità di SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni manuali o offline del pacchetto, è possibile scaricare i pacchetti Debian e RPM con le informazioni nella tabella seguente:

| Pacchetto | Versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto di Red Hat RPM | 15.0.1000.34-2 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Pacchetto RPM ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Pacchetto RPM extensibility](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Pacchetto RPM estendibilità Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Pacchetto RPM SLES | 15.0.1000.34-2 | [pacchetto RPM motore MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Pacchetto RPM ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Pacchetto RPM extensibility](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Pacchetto RPM estendibilità Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Pacchetto Debian Ubuntu 16.04 | 15.0.1000.34-2 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1000.34-2_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1000.34-2_amd64.deb)</br>[Pacchetto Debian ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1000.34-2_amd64.deb)</br>[Pacchetto Debian extensibility](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1000.34-2_amd64.deb)</br>[Pacchetto Debian estendibilità Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1000.34-2_amd64.deb)|

### <a name="known-issues"></a>Problemi noti

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Attualmente, MSDTC richiede le transazioni per essere non autenticato. Ad esempio, se si usa un server collegato da SQL Server in Windows per SQL Server in Linux o Usa un'applicazione client di Windows per avviare una transazione distribuita con SQL Server in Linux, MSDTC in Windows server/client sarà necessario utilizzare l'opzione "No Autenticazione obbligatoria".

## <a name="next-steps"></a>Passaggi successivi

Per iniziare, vedere le guide introduttive seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installazione in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Esecuzione in Docker](quickstart-install-connect-ubuntu.md)
- [Eseguire il provisioning di una macchina virtuale SQL in Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)
- [Esecuzione e connessione - Cloud](quickstart-install-connect-clouds.md)

Per le risposte alle domande più frequenti, vedere la [SQL Server in Linux FAQ](sql-server-linux-faq.md).
