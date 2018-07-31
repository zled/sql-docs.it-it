---
title: Requisiti di sistema (Driver ODBC per SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- prerequisites
- system requirements
- requirements
ms.assetid: f03b7fdd-0e9d-4e74-958d-e8c87e027348
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bab69d8a2ebf405e99cc9cff7e4cdadb94d79f98
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38047484"
---
# <a name="system-requirements"></a>Requisiti di sistema
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Questo argomento elenca i requisiti per l'uso di [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] in Linux e macOS.


## <a name="microsoft-odbc-driver-13-131-and-17-for-sql-server"></a>Microsoft ODBC Driver for SQL Server versioni 13, 13.1 e 17

I driver di Linux e macOS sono disponibili solo per le versioni a 64 bit dei sistemi operativi seguenti:

|Sistema operativo|Versione del Driver supportati|
|------------------------------------|--------------------------------|
|Apple OS X 10.11 (El Capitan)|13, 13.1, 17|
|Apple macOS 10.12 (Sierra)|13, 13.1, 17|
|Apple macOS 10.13 (High Sierra)|17| 
|Debian Linux 8|13, 13.1, 17|
|Debian Linux 9|17|
|RedHat Enterprise Linux 6|13, 13.1, 17|
|RedHat Enterprise Linux 7|13, 13.1, 17|
|SuSE Linux Enterprise Server 11|13, 13.1, 17 <br /><br /> **Nota:** ODBC Driver 17 supporta solo SuSE Linux Enterprise Server 11 SP4|
|SuSE Linux Enterprise Server 12|13, 13.1, 17|
|Ubuntu Linux 14.04|13, 13.1, 17|
|Ubuntu Linux 15.10|13, 13.1|
|Ubuntu Linux 16.04|13, 13.1, 17|
|Ubuntu Linux 16.10|13, 13.1|
|Ubuntu Linux 17.10|17|

L'installazione di pacchetti per il [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 13.1 e 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] in Linux e macOS risolvere le dipendenze del driver automaticamente quando installato tramite il sistema di gestione pacchetti di distribuzione, come descritto in [ Installazione del Driver](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Microsoft ODBC Driver 11 per SQL Server  
  
-   Gestione driver UnixODBC 2.3.0 a 64 bit per SQLLEN/SQLULEN a 64 bit. Le versioni successive di Gestione driver UnixODBC a 64 bit non sono supportate con il driver ODBC in Linux. Per ulteriori informazioni, vedere [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) .  
  
-   Il driver ODBC per **Red Hat Enterprise Linux 5 (64 bit)** richiede i pacchetti seguenti e può essere scaricato da qui: [Microsoft ODBC Driver 11 for SQL Server - Red Hat Linux](http://go.microsoft.com/fwlink/?LinkId=267321)  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `e2fsprogs-libs`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   Il driver ODBC per **Red Hat Enterprise Linux 6 (64 bit)** richiede i pacchetti seguenti e può essere scaricato da qui: [Microsoft ODBC Driver 11 for SQL Server - Red Hat Linux](http://go.microsoft.com/fwlink/?LinkId=267321)  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `libuuid`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   Il driver ODBC per **SUSE Linux Enterprise 11 Service Pack 2 (64 bit)** richiede i pacchetti seguenti e può essere scaricato da qui: [Microsoft ODBC Driver 11 Preview for SQL Server - SUSE Linux](http://go.microsoft.com/fwlink/?LinkId=264916)  
    -   `glibc`  
    -   `libstdc++46`  
    -   `libgcc46`  
    -   `libuuid1`  
    -   `krb5`  
    -   `libopenssl0_9_8`  
  
## <a name="see-also"></a>Vedere anche
[Installazione di Gestione driver](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[Problemi noti in questa versione del driver](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  

[Note sulla versione](../../../connect/odbc/linux-mac/release-notes.md)  
