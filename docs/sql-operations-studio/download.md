---
title: Scaricare e installare Microsoft SQL operazioni Studio (anteprima) | Documenti Microsoft
description: Scaricare e installare Microsoft SQL operazioni Studio (preview per Windows, Mac OS o Linux)
ms.custom: tools|sos
ms.date: 01/17/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0621d5af62b5f5b8b694d47cf16d766215a0c819
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="download-and-install-sql-operations-studio-preview"></a>Scaricare e installare Studio operazioni SQL (anteprima)

[!INCLUDE[name-sos](../includes/name-sos.md)]viene eseguito in Windows, macOS e Linux.

Scaricare e installare la versione più recente, il *anteprima pubblica di gennaio*:

|Piattaforma|Scarica|Data di rilascio|
|:---|:---|:---|
|Windows|[Programma di installazione](https://go.microsoft.com/fwlink/?linkid=866480)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=866479)|17 gennaio 2018 |
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=866481)|17 gennaio 2018 |
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=866484)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=866483)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=866482)|17 gennaio 2018|

Per informazioni dettagliate sulla versione più recente, vedere il [note sulla versione](release-notes.md).

## <a name="get-sql-operations-studio-preview-for-windows"></a>Ottenere Studio operazioni SQL (anteprima) per Windows

Questa versione di [!INCLUDE[name-sos](../includes/name-sos-short.md)] include un'esperienza di installazione di Windows standard e un file ZIP: 

**Programma di installazione**

1. Scaricare ed eseguire il [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] programma di installazione per Windows](https://go.microsoft.com/fwlink/?linkid=866480).
1. Avviare il [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] app.


**file con estensione zip**

1. Scaricare [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] ZIP per Windows](https://go.microsoft.com/fwlink/?linkid=866479).
2. Individuare il file scaricato e decomprimerlo.
3. Eseguire `\sqlops-windows\sqlops.exe`


## <a name="get-sql-operations-studio-preview-for-macos"></a>Ottenere Studio operazioni SQL (anteprima) per macOS

1. Scaricare [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] per macOS](https://go.microsoft.com/fwlink/?linkid=866481).
2. Per espandere il contenuto del file zip, fare doppio clic.
3. Per rendere [!INCLUDE[name-sos](../includes/name-sos-short.md)] disponibile nel *Launchpad*, trascinare *sqlops.app* per il *applicazioni* cartella.


## <a name="get-sql-operations-studio-preview-for-linux"></a>Ottenere Studio operazioni SQL (anteprima) per Linux

1. Scaricare [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] per Linux](https://go.microsoft.com/fwlink/?linkid=866482).
1. Per estrarre il file e avviare [!INCLUDE[name-sos](../includes/name-sos-short.md)], aprire una nuova finestra terminale e digitare i comandi seguenti:

   ```bash
   cd ~
   cp ~/Downloads/sqlops-linux-<version string>.tar.gz ~
   tar -xvf ~/sqlops-linux-<version string>.tar.gz
   echo 'export PATH="$PATH:~/sqlops-linux-x64"' >> ~/.bashrc
   source ~/.bashrc
   sqlops
   ```

   > [!NOTE]
   > In Ubuntu e Redhat, si dispone di dipendenze mancanti. Per installare queste dipendenze a seconda della versione di Linux, utilizzare i comandi seguenti:
   
   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```

   **Redhat:** 
   ```bash
   yum install libXScrnSaver
   ```

## <a name="uninstall-sql-operations-studio-preview"></a>Disinstallare Studio operazioni SQL (anteprima)

Se è stato installato [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] utilizzando il programma di installazione di Windows, quindi disinstallare allo stesso modo rimuovere tutte le applicazioni di Windows.

Se è stato installato [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] con un file ZIP o altro archivio, quindi eliminare i file.

## <a name="supported-operating-systems"></a>Sistemi operativi supportati

[!INCLUDE[name-sos](../includes/name-sos-short.md)]viene eseguito in Windows, macOS e Linux ed è supportato sulle piattaforme seguenti:

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
- macOS 10.13 Sierra elevata
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04



## <a name="next-steps"></a>Passaggi successivi

Vedere una delle Guide rapide seguenti per iniziare:
- [Connetti & Query in SQL Server](quickstart-sql-server.md)
- [Connettersi & Query di Database SQL di Azure](quickstart-sql-database.md)
- [Connettersi & Query Azure Data Warehouse](quickstart-sql-dw.md)

Contribuire a [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Informativa sulla Privacy Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) e [raccolta dati di utilizzo](usage-data-collection.md).
