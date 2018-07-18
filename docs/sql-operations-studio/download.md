---
title: Scaricare e installare SQL Operations Studio (preview) | Microsoft Docs
description: Scaricare e installare Microsoft SQL Operations Studio (preview) per Windows, Mac OS o Linux
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 421b22fd1489561ff04a69e23ecac15d1d52be5a
ms.sourcegitcommit: d3432a37b23b61c37092daf7519b30fc42fc0538
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270992"
---
# <a name="download-and-install-sql-operations-studio-preview"></a>Scaricare e installare SQL Operations Studio (preview)

[!INCLUDE[name-sos](../includes/name-sos.md)] è supportato in Windows, macOS e Linux.

Scaricare e installare la versione più recente, il *anteprima pubblica di giugno*:

|Piattaforma|Scarica|Data di rilascio| Versione |
|:---|:---|:---|:---|
|Windows|[Programma di installazione](https://go.microsoft.com/fwlink/?linkid=875602)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=875603)|20 giugno 2018 |0.30.6|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=875604)|20 giugno 2018 |0.30.6|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=875607)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=875606)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=875605)|20 giugno 2018 |0.30.6|

Per informazioni dettagliate sulla versione più recente, vedere le [note sulla versione](release-notes.md).

## <a name="get-sql-operations-studio-preview-for-windows"></a>Ottenere SQL Operations Studio (preview) per Windows

Questa versione di [!INCLUDE[name-sos](../includes/name-sos-short.md)] include un'installazione di Windows standard e un file ZIP: 

**Programma di installazione**

1. Scaricare ed eseguire il [programma di installazione di [!INCLUDE[name-sos](../includes/name-sos-short.md)] per Windows](https://go.microsoft.com/fwlink/?linkid=875602).
1. Avviare l'app [!INCLUDE[name-sos-short](../includes/name-sos-short.md)].


**file con estensione zip**

1. Scaricare [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] ZIP per Windows](https://go.microsoft.com/fwlink/?linkid=875603).
2. Individuare il file scaricato e decomprimerlo.
3. Eseguire `\sqlops-windows\sqlops.exe`


## <a name="get-sql-operations-studio-preview-for-macos"></a>Ottenere SQL Operations Studio (preview) per macOS

1. Scaricare [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] per macOS](https://go.microsoft.com/fwlink/?linkid=875604).
2. Per espandere il contenuto del file zip, fare doppio clic.
3. Per rendere [!INCLUDE[name-sos](../includes/name-sos-short.md)] disponibile nel *Launchpad*, trascinare *sqlops.app* sulla cartella *applicazioni*.


## <a name="get-sql-operations-studio-preview-for-linux"></a>Ottenere SQL Operations Studio (preview) per Linux

1. Scaricare [!INCLUDE[name-sos](../includes/name-sos-short.md)] per Linux usando uno dei programmi di installazione o l'archivio GZ:
    - [.deb](https://go.microsoft.com/fwlink/?linkid=875607)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=875606)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=875605)
1. Per estrarre il file e avviare [!INCLUDE[name-sos](../includes/name-sos-short.md)], aprire una nuova finestra terminale e digitare i comandi seguenti:

   **Debian installazione:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
   ```

   **RPM installazione:**
   ```bash
   cd ~
   yum install ./Downloads/sqlops-linux-<version string>.rpm

   sqlops
   ```

   **GZ installazione:**
   ```bash 
   cd ~ 
   cp ~/Downloads/sqlops-linux-<version string>.tar.gz ~ 
   tar -xvf ~/sqlops-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/sqlops-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   sqlops 
   ``` 

   > [!NOTE]
   > In Debian, Redhat e Ubuntu, potrebbero mancare alcune dipendenze. Per installarle, a seconda della versione di Linux, utilizzare i comandi seguenti:
   

   **Debian:** 
   ```bash
   sudo apt-get install libuwind8
   ```

   **Redhat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```


## <a name="uninstall-sql-operations-studio-preview"></a>Disinstallare SQL Operations Studio (preview)

Se [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] è stato installato utilizzando il programma di installazione di Windows, disinstallare nel modo comune a tutte le applicazioni di Windows.

Se[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] è stato installato con un file ZIP o altro archivio, eliminare i file.

## <a name="supported-operating-systems"></a>Sistemi operativi supportati

[!INCLUDE[name-sos](../includes/name-sos-short.md)] è supportato in Windows, macOS e Linux, sulle piattaforme seguenti:

### <a name="windows"></a>Windows
- Windows 10 (64 bit)
- Windows 8.1 (64 bit)
- Windows 8 (64 bit)
- Richiede Windows 7 (SP1) (64 bit) - [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64 bit)
- Windows Server 2012 (64 bit)
- Windows Server 2008 R2 (64 bit)

### <a name="macos"></a>macOS
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Server 7.3 di Red Hat Enterprise Linux
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="check-for-updates"></a>Verificare gli aggiornamenti
Per verificare gli aggiornamenti più recenti, scegliere l'icona dell'ingranaggio nell'angolo inferiore sinistro della finestra e fare clic su **verificare la presenza di aggiornamenti**

## <a name="next-steps"></a>Passaggi successivi

Seguire una delle guide rapide qui sotto per iniziare:
- [Connettersi ed eseguire query in SQL Server](quickstart-sql-server.md)
- [Connettersi ed eseguire query in Database SQL di Azure](quickstart-sql-database.md)
- [Connettersi ed eseguire query in Azure Data Warehouse](quickstart-sql-dw.md)

Contribuire a [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Informativa sulla Privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) e [raccolta dati di utilizzo](usage-data-collection.md).
