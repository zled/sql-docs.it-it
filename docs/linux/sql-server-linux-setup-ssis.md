---
title: Installare SQL Server Integration Services in Linux | Documenti Microsoft
description: In questo articolo viene descritto come installare SQL Server Integration Services (SSIS) in Linux.
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 01/09/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: d2e72c77ad5f200c07a6e71025a3461d6397032a
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34323392"
---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Installare SQL Server Integration Services (SSIS) in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Seguire i passaggi descritti in questo articolo per installare SQL Server Integration Services (`mssql-server-is`) in Linux. Per informazioni sulle funzionalità supportate in questa versione di servizi di integrazione per Linux, vedere il [note sulla versione](sql-server-linux-release-notes.md).

Installare il server di integrazione di SQL Server per la piattaforma:

- [Ubuntu](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)

## <a name="ubuntu"></a> Installare SSIS in Ubuntu
Per installare il `mssql-server-is` pacchetto in Ubuntu, seguire questi passaggi:

1. Importare le chiavi GPG archivio pubblico.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Registrare il repository Ubuntu di Microsoft SQL Server.

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

3. Eseguire i comandi seguenti per installare SQL Server Integration Services.

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server-is
   ```

4. Dopo l'installazione di Integration Services, eseguire `ssis-conf`. Per altre informazioni, vedere [configurare SSIS in Linux con ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

5. Al termine della configurazione, impostare il percorso.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Aggiornamento SSIS
Se si dispone già di `mssql-server-is` installato, è possibile aggiornare la versione più recente con il comando seguente:

```bash
sudo apt-get install mssql-server-is
```

### <a name="remove-ssis"></a>Rimuovere SSIS
Per rimuovere `mssql-server-is`, è possibile eseguire il seguente comando:
```bash
sudo apt-get remove mssql-server-is
```

## <a name="RHEL"></a> Installare SSIS in RHEL
Per installare il `mssql-server-is` pacchetto su RHEL, seguire questi passaggi:

1. Scaricare il file di configurazione di Microsoft SQL Server Red Hat repository.

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

1. Eseguire i comandi seguenti per installare SQL Server Integration Services.

   ```bash
   sudo yum install -y mssql-server-is
   ```


1. Dopo l'installazione, eseguire `ssis-conf`. Per altre informazioni, vedere [configurare SSIS in Linux con ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. Al termine della configurazione, impostare percorso.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Aggiornamento SSIS
Se si dispone già di `mssql-server-is` installato, è possibile aggiornare la versione più recente con il comando seguente:

```bash
sudo yum update mssql-server-is
```

### <a name="remove-ssis"></a>Rimuovere SSIS
Per rimuovere `mssql-server-is`, è possibile eseguire il seguente comando:
```bash
sudo yum remove mssql-server-is
```

## <a name="unattended-installation"></a>Installazione automatica
Per eseguire un'installazione automatica quando si esegue `ssis-conf setup`, eseguire le operazioni seguenti:
1.  Specificare il `-n` (Nessun prompt) opzione.
2.  Immettere i valori richiesti per l'impostazione delle variabili di ambiente.

Nell'esempio seguente effettua le operazioni seguenti:
-   Consente di installare SSIS.
-   Specifica l'edizione Developer, fornendo un valore per il `SSIS_PID` variabile di ambiente.
-   Accetta il contratto di licenza, fornendo un valore per il `ACCEPT_EULA` variabile di ambiente.
-   Esegue un'installazione automatica, specificando il `-n` (Nessun prompt) opzione.

```
sudo SSIS_PID=Developer ACCEPT_EULA=Y /opt/ssis/bin/ssis-conf -n setup 
```

### <a name="environment-variables-for-unattended-installation"></a>Variabili di ambiente per l'installazione automatica

| Variabile di ambiente | Description |
|---|---|
| **ACCEPT_EULA** | Accetta il contratto di licenza di SQL Server quando è impostato su un valore (ad esempio, `Y`).|
| **SSIS_PID** | Imposta la chiave di prodotto o edizione di SQL Server. Di seguito sono i valori possibili:<br/>Copia di valutazione<br/>Developer<br/>Express <br/>Web <br/>Standard<br/>Enterprise <br/>Un codice product key<br/><br/>Se si specifica un codice product key, il codice product key deve essere nel formato `#####-#####-#####-#####-#####`, dove `#` è una lettera o un numero.  |
| | |

## <a name="next-steps"></a>Passaggi successivi

Per eseguire pacchetti SSIS in Linux, vedere [di estrazione, trasformazione e caricare i dati per SQL Server in Linux con SSIS](sql-server-linux-migrate-ssis.md).

Per configurare impostazioni aggiuntive di SSIS in Linux, vedere [configurare SQL Server Integration Services in Linux con ssis-conf](sql-server-linux-configure-ssis.md).

## <a name="related-content-about-ssis-on-linux"></a>Contenuto correlato su SSIS in Linux
-   [Estrarre, trasformare e caricare i dati in Linux con SSIS](sql-server-linux-migrate-ssis.md)
-   [Configurare SQL Server Integration Services in Linux con ssis-conf](sql-server-linux-configure-ssis.md)
-   [Limitazioni e problemi noti per SSIS in Linux](sql-server-linux-ssis-known-issues.md)
-   [Esecuzione in Linux con cron del pacchetto di pianificazione di SQL Server Integration Services](sql-server-linux-schedule-ssis-packages.md)
