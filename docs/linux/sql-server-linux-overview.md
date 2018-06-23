---
title: Panoramica di SQL Server in Linux | Documenti Microsoft
description: Questo articolo descrive le modalità di esecuzione in Linux e fornisce informazioni su come per altre informazioni in SQL Server.
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
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36311689"
---
# <a name="sql-server-on-linux"></a>SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server 2017 viene ora eseguito in Linux. È lo stesso motore di database di SQL Server, con molti servizi indipendentemente dal sistema operativo e le funzionalità di simili.

## <a name="install"></a>Install

Per iniziare, installare SQL Server in Linux con una delle seguenti esercitazioni di avvio rapido:

- [Installare su Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-docker.md)
- [Eseguire il provisioning di una macchina virtuale SQL in Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker stesso viene eseguito su più piattaforme, il che significa che è possibile eseguire l'immagine di Docker in Windows, Mac e Linux.

## <a name="connect"></a>Connect

Dopo l'installazione, connettersi all'istanza di SQL Server nel computer Linux. È possibile connettersi in locale o in modalità remota e con un'ampia gamma di strumenti e driver. La Guida introduttiva viene illustrato come utilizzare il [sqlcmd](sql-server-linux-setup-tools.md) strumento da riga di comando. Altri strumenti includono:

| Strumento | Esercitazione |
|-----|-----|
| Codice di Visual Studio (codice di Visual Studio) | [Usare il codice di Visual Studio con SQL Server in Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Utilizzare SQL Server Management Studio in Windows per connettersi a SQL Server in Linux](sql-server-linux-manage-ssms.md) |
| SQL Server Data Tools (SSDT) | [Usare SSDT con SQL Server in Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Esplora

SQL Server 2017 ha lo stesso motore di database sottostanti in tutte le piattaforme supportate, tra cui Linux. Numero così elevato e le funzionalità esistenti funzionano allo stesso modo su Linux. Questa area della documentazione espone alcune di queste funzionalità da una prospettiva di Linux. Chiama anche le aree dotato di requisiti specifici per Linux.

Se ha già familiarità con SQL Server, esaminare i [note sulla versione](sql-server-linux-release-notes.md) per le linee guida generali e i problemi noti per questa versione. Quindi esaminare [novità di SQL Server in Linux](sql-server-linux-whats-new.md) nonché [novità di SQL Server 2017 complessiva](../sql-server/what-s-new-in-sql-server-2017.md). 

> [!TIP]
> Per le risposte alle domande frequenti, vedere la [SQL Server in domande frequenti su Linux](sql-server-linux-faq.md).

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]