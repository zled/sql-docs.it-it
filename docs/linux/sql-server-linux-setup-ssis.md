---
title: Installare SQL Server Integration Services in Linux | Documenti Microsoft
description: In questo argomento viene descritto come installare SQL Server Integration Services in Linux.
author: leolimsft
ms.author: lle
manager: craigg
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: integration-services
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c3943870ec10b8430ac4819398908c5459a8b03c
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Installare SQL Server Integration Services (SSIS) in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Seguire i passaggi descritti in questo articolo per installare SQL Server Integration Services (`mssql-server-is`) in Linux. Per informazioni sulle funzionalità supportate in questa versione di servizi di integrazione per Linux, vedere il [note sulla versione](sql-server-linux-release-notes.md).

Installare il server di integrazione di SQL Server per la piattaforma:

- [Ubuntu](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)



## <a name="ubuntu"></a>Installare SSIS in Ubuntu
Per installare il `mssql-server-is` pacchetto in Ubuntu, seguire questi passaggi:


1.  Importare le chiavi GPG archivio pubblico.

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add –
    ```


2.  Registrare il repository Ubuntu di Microsoft SQL Server.

    ```bash
    curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server.list | sudo tee /etc/apt/sources.list.d/mssql-server.list
    ```


3.  Eseguire i comandi seguenti per installare SQL Server Integration Services.

    ```bash
    sudo apt-get update
    sudo apt-get install -y mssql-server-is
    ```


4.  Dopo l'installazione di Integration Services, eseguire `ssis-conf`.

    ```bash
    sudo /opt/ssis/bin/ssis-conf setup
    ```


5.  Al termine della configurazione, impostare il percorso.

    ```bash
    export PATH=/opt/ssis/bin:$PATH
    ```


Se si dispone già di `mssql-server-is` installato, è possibile aggiornare la versione più recente con il comando seguente:

```bash
sudo apt-get install mssql-server-is
```


Per rimuovere `mssql-server-is`, è possibile eseguire il seguente comando:
```bash
sudo apt-get remove msssql-server-is
```



## <a name="RHEL"></a>Installare SSIS in RHEL
Per installare il `mssql-server-is` pacchetto su RHEL, seguire questi passaggi:


1.  Passare alla modalità utente avanzato.

    ```bash
    sudo su
    ```


2.  Scaricare il file di configurazione di Microsoft SQL Server Red Hat repository.

    ```bash
    curl https://packages.microsoft.com/config/rhel/7/mssql-server.repo > /etc/yum.repos.d/mssql-server.repo
    ```


3.  Uscire dalla modalità utente avanzato.

    ```bash
    exit
    ```


4.  Eseguire i comandi seguenti per installare SQL Server Integration Services.

    ```bash
    sudo yum install -y mssql-server-is
    ```


5.  Dopo l'installazione, eseguire `ssis-conf`.

    ```bash
    sudo /opt/ssis/bin/ssis-conf setup
    ```


6.  Al termine della configurazione, impostare percorso.

    ```bash
    export PATH=/opt/ssis/bin:$PATH
    ```


Se si dispone già di `mssql-server-is` installato, è possibile aggiornare la versione più recente con il comando seguente:

```bash
sudo yum update mssql-server-is
```


Per rimuovere `mssql-server-is`, è possibile eseguire il seguente comando:
```bash
sudo yum remove msssql-server-is
```




## <a name="run-a-package"></a>Eseguire un pacchetto
Copiare il pacchetto SSIS nel computer Linux. Utilizzare quindi il comando seguente per eseguire il pacchetto.

```bash
dtexec /F <package name> /DE <protection password>
```



## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni sull'utilizzo di SSIS in Linux per estrarre, trasformare e caricare i dati, vedere [estrarre, trasformare e caricare i dati per SQL Server in Linux con SSIS](sql-server-linux-migrate-ssis.md).
