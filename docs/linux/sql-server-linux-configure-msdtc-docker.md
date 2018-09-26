---
title: Come usare le transazioni distribuite con SQL Server in Docker | Microsoft Docs
description: Questo articolo illustra come usare Dprovides una procedura dettagliata per la configurazione di MSDTC in Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 3242f0d074dc3c2f33fc83de4604a20bfdcbd64a
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049406"
---
# <a name="how-to-use-distributed-transactions-with-sql-server-on-docker"></a>Come usare le transazioni distribuite con SQL Server in Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo articolo illustra come configurare SQL Server in Docker per le transazioni distribuite.

A partire da SQL Server 2019 anteprima, le immagini dei contenitori supportano il Microsoft Distributed Transaction Coordinator (MSDTC) richiesto per le transazioni distribuite. Per comprendere i requisiti di comunicazione per MSDTC, vedere [come configurare Microsoft Distributed Transaction Coordinator (MSDTC) in Linux](sql-server-linux-configure-msdtc.md). Questo articolo illustra i requisiti speciali e scenari correlati ai contenitori Docker di SQL Server.

## <a name="configuration"></a>Configurazione

Per abilitare la transazione MSDTC in contenitori di docker, è necessario impostare due nuove variabili di ambiente:

- **MSSQL_RPC_PORT**: porta TCP che servizio agente mapping endpoint RPC viene associato a ed è in ascolto su.  
- **MSSQL_DTC_TCP_PORT** la porta che il servizio MSDTC sia configurato per restare in attesa su.

### <a name="pull-and-run"></a>Eseguire il pull ed eseguire

Nell'esempio seguente viene illustrato come usare queste variabili di ambiente per eseguire il pull ed eseguire un contenitore configurato per MSDTC. In questo modo per comunicare con qualsiasi applicazione in tutti gli host.

```bash
docker run \
   -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -e 'MSSQL_RPC_PORT=13500' -e 'MSSQL_DTC_TCP_PORT=51000' \
   -p 51433:1433 -p 13500:13500 -p 51000:51000  \
   -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
```

Il comando seguente viene illustrato lo stesso comando di Docker in Windows PowerShell:

```PowerShell
docker run `
   -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -e "MSSQL_RPC_PORT=13500" -e "MSSQL_DTC_TCP_PORT=51000" `
   -p 51433:1433 -p 13500:13500 -p 51000:51000 `
   -d "mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu"
```

In questo comando, il **RPC Endpoint Mapper** servizio è stato associato alla porta 13500 e il **MSDTC** servizio è stato associato alla porta 51000 nella rete virtuale di docker. La comunicazione di TDS di SQL Server avviene sulla porta 1433 all'interno di rete virtuale di docker. Queste porte sono state esposte esternamente all'host come porta TDS 51433 e porta del RPC endpoint mapper 13500 porta MSDTC 51000.

> [!NOTE]
> L'agente mapping Endpoint RPC e la porta MSDTC non è necessario siano uguali in host e il contenitore. Pertanto, mentre la porta RPC Endpoint Mapper è stata configurata per essere 13500 sul contenitore, questo potrebbe potenzialmente mappato porta 13501 o qualsiasi altra porta disponibile nel server host.

## <a name="configure-the-firewall"></a>Configurare il firewall

Per poter comunicare con e tramite l'host, è anche necessario configurare il firewall nel server host per i contenitori. Aprire il firewall per tutte le porte che docker contenitore espone la per le comunicazioni esterne. Nell'esempio precedente, questo sarebbe porte 135 e 51433 51000. Queste sono le porte nell'host stesso e non le porte di che cui eseguono il mapping del contenitore. Pertanto, se RPC Endpoint mapper porta 51000 del contenitore è stata mappata alla porta dell'host 51001, quindi porta 51001 (non 51000) deve essere aperta nel firewall per la comunicazione con l'host.  

Nell'esempio seguente viene illustrato come creare queste regole in Ubuntu.

```bash
sudo ufw allow from any to any port 51433 proto tcp
sudo ufw allow from any to any port 51000 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

L'esempio seguente illustra come eseguire questa operazione in Red Hat Enterprise Linux (RHEL):

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=51433/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

## <a name="configure-port-routing-on-the-host"></a>Configurare il routing di porta nell'host

Se le transazioni distribuite con un server esterno per l'host fa parte il contenitore docker, quindi l'host deve configurare routing delle porte. Per altre informazioni, vedere [configurare il routing di porta](sql-server-linux-configure-msdtc.md#configure-port-routing).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su MSDTC su Linux, vedere [come configurare Microsoft Distributed Transaction Coordinator (MSDTC) in Linux](sql-server-linux-configure-msdtc.md).