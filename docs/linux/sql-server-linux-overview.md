---
title: Panoramica di SQL Server in Linux | Microsoft Docs
description: Questo articolo descrive come SQL Server viene eseguito in Linux e fornisce informazioni su come per altre informazioni.
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
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.openlocfilehash: 16ea8b69f1d55e5b338931f0531bdf8a2e037707
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38020139"
---
# <a name="sql-server-on-linux"></a>SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server 2017 ora viene eseguito su Linux. È lo stesso motore di database di SQL Server, con molti servizi indipendentemente dal sistema operativo e le funzionalità di simile.

## <a name="install"></a>Install

Per iniziare, installare SQL Server in Linux con una delle seguenti esercitazioni di avvio rapido:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installazione in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Esecuzione in Docker](quickstart-install-connect-docker.md)
- [Eseguire il provisioning di una macchina virtuale SQL in Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker stesso viene eseguito su più piattaforme, il che significa che è possibile eseguire l'immagine Docker in Linux, Mac e Windows.

## <a name="connect"></a>Connect

Dopo l'installazione, connettersi all'istanza di SQL Server nel computer Linux. È possibile connettersi in locale o in modalità remota e con un'ampia gamma di strumenti e driver. Le guide rapide viene illustrato come usare il [sqlcmd](sql-server-linux-setup-tools.md) lo strumento da riga di comando. Altri strumenti includono:

| Strumento | Esercitazione |
|-----|-----|
| Visual Studio Code (VS Code) | [Usare Visual Studio Code con SQL Server in Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Usare SSMS in Windows per connettersi a SQL Server in Linux](sql-server-linux-manage-ssms.md) |
| SQL Server Data Tools (SSDT) | [Usare SSDT con SQL Server in Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Esplora

In tutte le piattaforme supportate, tra cui Linux, SQL Server 2017 offre lo stesso motore di database sottostante. Così tante funzionalità e capacità funzionano nello stesso modo in Linux. In questa area della documentazione di espone alcune di queste funzionalità da una prospettiva di Linux. Chiama anche le aree che presentano requisiti specifici in Linux.

Se ha già familiarità con SQL Server, consultare il [note sulla versione](sql-server-linux-release-notes.md) per linee guida generali e i problemi noti per questa versione. Quindi esaminare [novità di SQL Server in Linux](sql-server-linux-whats-new.md) nonché [novità di SQL Server 2017 complessiva](../sql-server/what-s-new-in-sql-server-2017.md). 

> [!TIP]
> Per le risposte alle domande più frequenti, vedere la [SQL Server in Linux FAQ](sql-server-linux-faq.md).

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]