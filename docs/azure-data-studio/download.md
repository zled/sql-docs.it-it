---
title: Scaricare e installare Data Studio di Azure | Microsoft Docs
description: Scaricare e installare Studio dati Azure per Windows, macOS o Linux
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 88b79feb3b04dcc7f872653b2e24a9f70c370f57
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038433"
---
# <a name="download-and-install-azure-data-studio"></a>Scaricare e installare Data Studio di Azure

[!INCLUDE[name-sos](../includes/name-sos.md)] è supportato in Windows, macOS e Linux.

Scaricare e installare la versione più recente, il *rilascio di settembre GA*:

> [!NOTE]
> Se si esegue l'aggiornamento da SQL Operations Studio e si desidera mantenere le impostazioni, tasti di scelta rapida o frammenti di codice, vedere [spostare le impostazioni utente](#move-user-settings).

|Piattaforma|Scarica|Data di rilascio| Versione |
|:---|:---|:---|:---|
|Windows|[Programma di installazione](https://go.microsoft.com/fwlink/?linkid=2024683)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2024680)|24 settembre 2018 |1,0|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2024677)|24 settembre 2018 |1,0|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=2024668)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2024672)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2024675)|24 settembre 2018 |1,0|

Per informazioni dettagliate sulla versione più recente, vedere le [note sulla versione](release-notes.md).

## <a name="get-azure-data-studio-for-windows"></a>Ottenere dati di Azure Studio per Windows

Questa versione di [!INCLUDE[name-sos](../includes/name-sos-short.md)] include un'installazione di Windows standard e un file ZIP: 

**Programma di installazione**

1. Scaricare ed eseguire il [programma di installazione di [!INCLUDE[name-sos](../includes/name-sos-short.md)] per Windows](https://go.microsoft.com/fwlink/?linkid=2024683).
1. Avviare l'app [!INCLUDE[name-sos-short](../includes/name-sos-short.md)].


**file con estensione zip**

1. Scaricare [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] ZIP per Windows](https://go.microsoft.com/fwlink/?linkid=2024680).
2. Individuare il file scaricato e decomprimerlo.
3. Eseguire `\azuredatastudio-windows\azuredatastudio.exe`


## <a name="get-azure-data-studio-for-macos"></a>Ottenere Data Studio di Azure per macOS

1. Scaricare [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] per macOS](https://go.microsoft.com/fwlink/?linkid=2024677).
2. Per espandere il contenuto del file zip, fare doppio clic.
3. Per rendere [!INCLUDE[name-sos](../includes/name-sos-short.md)] disponibile nel *Launchpad*, trascinare */Applications i dati di Azure* per i *applicazioni* cartella.


## <a name="get-azure-data-studio-for-linux"></a>Ottenere Studio dei dati di Azure per Linux

1. Scaricare [!INCLUDE[name-sos](../includes/name-sos-short.md)] per Linux usando uno dei programmi di installazione o l'archivio GZ:
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2024668)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2024672)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2024675)
1. Per estrarre il file e avviare [!INCLUDE[name-sos](../includes/name-sos-short.md)], aprire una nuova finestra del terminale e digitare i comandi seguenti:

   **Installazione di Debian:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **Installazione di RPM:**
   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **GZ installazione:**
   ```bash 
   cd ~ 
   cp ~/Downloads/azuredatastudio-linux-<version string>.tar.gz ~ 
   tar -xvf ~/azuredatastudio-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/azuredatastudio-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   azuredatastudio 
   ``` 

   > [!NOTE]
   > In Debian, Redhat e Ubuntu, potrebbero mancare alcune dipendenze. Per installarle, a seconda della versione di Linux, utilizzare i comandi seguenti:
   

   **Debian:** 
   ```bash
   sudo apt-get install libunwind8
   ```

   **RedHat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```


## <a name="uninstall-azure-data-studio"></a>Disinstallare Studio dei dati di Azure

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
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="check-for-updates"></a>Verificare gli aggiornamenti
Per verificare gli aggiornamenti più recenti, fare clic sull'icona a forma di ingranaggio nell'angolo inferiore sinistro della finestra e fare clic su **Controlla aggiornamenti**

## <a name="move-user-settings"></a>Spostare le impostazioni utente

Se si desidera spostare che le impostazioni personalizzate, tasti di scelta rapida o frammenti di codice, attenersi alla procedura seguente. Questo è importante se si esegue l'aggiornamento dalla versione di SQL Operations Studio ad Azure Data Studio.

*Se si dispone già di Studio dei dati di Azure o è stato mai installato o personalizzato di SQL Operations Studio, è possibile ignorare questa sezione.*


1. Aprire le impostazioni, scegliere l'icona dell'ingranaggio nella parte inferiore sinistra e scegliere **impostazioni.**

   ![Open-impostazioni](./media/download/open-settings.png)

2. Fare doppio clic il **delle impostazioni utente** scheda nella parte superiore e fare clic su **Visualizza in Esplora risorse**

   ![rivela-in-explorer](./media/download/reveal-in-explorer.png)

3. Copiare tutti i file in questa cartella e salvarlo in un modo facile trovare percorso nell'unità locale, come la cartella documenti.

   ![Copia-impostazioni](./media/download/copy-settings.png)

4. Nella versione nuova di Azure Data Studio, seguire i passaggi 1 e 2, quindi per passaggio 3 incollare il contenuto che è stato salvato nella cartella. È inoltre possibile copiare manualmente tramite le impostazioni, i tasti di scelta rapida o frammenti di codice nelle rispettive posizioni.


## <a name="next-steps"></a>Passaggi successivi

Seguire una delle guide rapide qui sotto per iniziare:
- [Connettersi ed eseguire query in SQL Server](quickstart-sql-server.md)
- [Connettersi ed eseguire query in Database SQL di Azure](quickstart-sql-database.md)
- [Connettersi ed eseguire query in Azure Data Warehouse](quickstart-sql-dw.md)

Contribuire a [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio) 

[Informativa sulla Privacy Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) e [raccolta dati di utilizzo](usage-data-collection.md).
