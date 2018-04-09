---
title: Scaricare e installare Microsoft SQL Operations Studio (anteprima) | Microsoft Docs
description: Scaricare e installare Microsoft SQL Operations Studio (anteprima per Windows, Mac OS o Linux)
ms.custom: tools|sos
ms.date: 03/28/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5bf4e79bc1f7092ebe95ff29079f3412306cf7b1
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2018
---
# <a name="download-and-install-sql-operations-studio-preview"></a>Scaricare e installare Studio operazioni SQL (anteprima) 


[!INCLUDE[name-sos](../includes/name-sos.md)] è supportato in Windows, macOS e Linux.

Scaricare e installare la versione più recente, ovvero *l'anteprima pubblica di febbraio*:

|Piattaforma|Scarica|Data di rilascio| Versione |
|:---|:---|:---|:---|
|Windows|[Programma di installazione](https://go.microsoft.com/fwlink/?linkid=870837)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=870838)|28 marzo 2018 |0.27.3|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=870839)|28 marzo 2018 |0.27.3|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=870842)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=870841)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=870840)|28 marzo 2018 |0.27.3|

Per informazioni dettagliate sulla versione più recente, vedere le [note sulla versione](release-notes.md).

## <a name="get-sql-operations-studio-preview-for-windows"></a>Ottenere SQL Operations Studio (anteprima) per Windows

Questa versione di [!INCLUDE[name-sos](../includes/name-sos-short.md)] include un'installazione di Windows standard e un file ZIP: 

**Programma di installazione**

1. Scaricare ed eseguire il [programma di installazione di [!INCLUDE[name-sos](../includes/name-sos-short.md)] per Windows](https://go.microsoft.com/fwlink/?linkid=870837).
1. Avviare l'app [!INCLUDE[name-sos-short](../includes/name-sos-short.md)].


**file con estensione zip**

1. Scaricare lo [ZIP di [!INCLUDE[name-sos](../includes/name-sos-short.md)] per Windows](https://go.microsoft.com/fwlink/?linkid=870838).
2. Individuare il file scaricato e decomprimerlo.
3. Eseguire `\sqlops-windows\sqlops.exe`


## <a name="get-sql-operations-studio-preview-for-macos"></a>Ottenere SQL Operations Studio (anteprima) per macOS

1. Scaricare [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] per macOS](https://go.microsoft.com/fwlink/?linkid=870839).
2. Per espandere il contenuto del file zip, fare doppio clic.
3. Per rendere [!INCLUDE[name-sos](../includes/name-sos-short.md)] disponibile nel *Launchpad*, trascinare *sqlops.app* sulla cartella *applicazioni*.


## <a name="get-sql-operations-studio-preview-for-linux"></a>Ottenere SQL Operations Studio (anteprima) per Linux

1. Scaricare [! INCLUDERE[sos nome](../includes/name-sos-short.md) per Linux usando uno dei programmi di installazione o l'archivio GZ:
    - [.deb](https://go.microsoft.com/fwlink/?linkid=870842)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=870841)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=870840)
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


## <a name="uninstall-sql-operations-studio-preview"></a>Disinstallare SQL Operations Studio (anteprima)

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
- macOS 10.13 Sierra elevata
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="check-for-updates"></a>Verificare gli aggiornamenti
Per controllare gli aggiornamenti più recenti, fare clic sull'icona a forma di ingranaggio nell'angolo inferiore sinistro della finestra e fare clic su **Controlla aggiornamenti**

## <a name="next-steps"></a>Passaggi successivi

Vedere una delle Guide rapide seguenti per iniziare:
- [Connettersi ed eseguire query in SQL Server](quickstart-sql-server.md)
- [Connettersi ed eseguire query di Database SQL di Azure](quickstart-sql-database.md)
- [Connettersi ed eseguire query in Azure Data Warehouse](quickstart-sql-dw.md)

Contribuire a [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Informativa sulla Privacy Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) e [raccolta dati di utilizzo](usage-data-collection.md).
