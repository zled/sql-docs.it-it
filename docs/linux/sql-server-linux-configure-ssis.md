---
title: Configurare SSIS in Linux con ssis-conf | Documenti Microsoft
description: "In questo articolo viene descritto come configurare SQL Server Integration Services (SSIS) in Linux con l'utilità Configurazione di ssis."
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: d71490df718bfcb6f8ce35c7d087bac4d5961aff
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="configure-sql-server-integration-services-on-linux-with-ssis-conf"></a>Configurare SQL Server Integration Services in Linux con ssis-conf

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Eseguire il `ssis-conf` script di configurazione quando si installa SQL Server Integration Services (SSIS) per Red Hat Enterprise Linux e Ubuntu. Per ulteriori informazioni sull'installazione di SSIS, vedere [installare SQL Server Integration Services (SSIS) in Linux](sql-server-linux-setup-ssis.md).

È inoltre possibile utilizzare il `ssis-conf` utilità per configurare le proprietà seguenti:

| Command | Description |
|-------------|---------------------------------------------------------------------|
| set-edition | Impostare l'edizione di SQL Server                                       |
| Dati di telemetria   | Abilitare o disabilitare il servizio di telemetria di SQL Server Integration Services |
| installazione       | Inizializzare e configurare Microsoft SQL Server Integration Services      |
|||

## <a name="run-ssis-conf"></a>Eseguire ssis-conf

Negli esempi inclusi in questo articolo eseguire `ssis-conf` specificando il percorso completo: `/opt/ssis/bin/ssis-conf`. Se si passa a tale posizione prima di eseguire `ssis-conf`, è possibile eseguire l'utilità nel contesto della directory corrente: `./ssis-conf`.

Assicurarsi di eseguire i comandi descritti in questo articolo con i privilegi radice. Ad esempio, eseguire `sudo /opt/ssis/bin/ssis-conf setup` e non `/opt/ssis/bin/ssis-conf setup`.

Per eseguire questi comandi con istruzioni nel linguaggio di programmazione, è possibile specificare le impostazioni locali. Ad esempio, per ricevere richieste in cinese, eseguire il comando seguente: `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="use-set-edition-to-set-the-edition-of-sql-server-integration-services"></a>Set-versione utilizzata per impostare l'edizione di SQL Server Integration Services

L'edizione di SSIS è allineato con l'edizione di SQL Server.

Immettere il comando seguente: `$ sudo /opt/ssis/bin/ssis-conf set-edition`.

Dopo aver immesso il comando, verrà visualizzato il seguente messaggio:

```
Choose an edition of SQL Server:

1) Evaluation (free, no production use rights, 180-day limit)

2) Developer (free, no production use rights)

3) Express (free)

4) Web (PAID)

5) Standard (PAID)

6) Enterprise (PAID)

7) Enterprise Core (PAID)

8) I bought a license through a retail sales channel and have a product key to enter.

Details about editions can be found at https://go.microsoft.com/fwlink/?LinkId=852748&clcid=0x409.

Use of PAID editions of this software requires separate licensing through a Microsoft Volume Licensing program.

By choosing a PAID edition, you are verifying that you have the appropriate number of licenses in place to install and run this software.

Enter your edition (1-8):
```

Se si immette un valore da 1 a 7, il sistema consente di configurare un'edizione gratuita o a pagamento. Se si immette 8, l'utilità viene richiesto di immettere il codice "product key" che sono stati acquistati:

```
Enter the 25-character product key:
```

## <a name="use-telemetry-to-configure-customer-feedback"></a>Utilizzare i dati di telemetria per configurare i suggerimenti dei clienti

Il `telemetry` comando determina se SSIS Invia commenti e suggerimenti a Microsoft.

Il servizio di telemetria per edizioni gratuite (vale a dire edizioni Express, Developer ed Evaluation), è sempre abilitato. Se si dispone di un'edizione gratuita, è possibile utilizzare il `telemetry` comando per disabilitare i dati di telemetria.

Immettere il comando seguente: `$ sudo /opt/ssis/bin/ssis-conf telemetry`.

Per le edizioni a pagamento, dopo aver immesso il comando, verrà visualizzato il seguente messaggio:

```
Send feature usage data to Microsoft. Feature usage data includes information about your hardware configuration and how you use SQL Server Integration Services.

[Yes/No]:
```

Se si seleziona **Sì**, il servizio di telemetria è abilitato e avvia l'esecuzione. Il servizio viene avviato automaticamente dopo ogni avvio. Se si seleziona **n**, interrompe il servizio di telemetria che sia disabilitata.

## <a name="use-setup-to-initialize-and-set-up-microsoft-sql-server-integration-services"></a>Utilizzare il programma di installazione per inizializzare e configurare Microsoft SQL Server Integration Services

Utilizzare il `setup` comando ogni volta che si installa SSIS.

Immettere il comando seguente: `sudo /opt/ssis/bin/ssis-conf setup`.

L'utilità chiede di confermare o fornire valori per gli elementi seguenti:
-   Licenza del prodotto
-   Contratto EULA
-   Servizio di telemetria
-   La lingua utilizzata da Integration Services

Per eseguire il `setup` comando con istruzioni nel linguaggio che si preferisce, è possibile specificare le impostazioni locali. Ad esempio, per ricevere richieste in cinese, eseguire il comando seguente: `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="ssisconf-format"></a>formato SSIS.conf

Le operazioni seguenti `/var/opt/ssis/ssis.conf` file viene fornito un esempio per ogni impostazione.

Per SQL Server, è possibile modificare le impostazioni di sistema modificando i valori di `mssql.conf` file. Per SSIS, si *non è possibile* modificare le impostazioni di sistema modificando i valori di `ssis.conf` file. Il `ssis.conf` file Mostra solo i risultati dell'installazione. Se si desidera modificare le impostazioni per SSIS, è possibile eliminare il `ssis.conf` file ed eseguire il `setup` nuovo il comando.

Di seguito è riportato un esempio `ssis.conf` file. Ogni campo corrisponde al risultato di un passaggio di installazione.

```
[LICENSE]
                       
registered = Y        
                       
pid = enterprisecore  
                       
[EULA]
                       
accepteula = Y        
                       
[TELEMETRY]
                       
enabled = Y           
                       
[language]
                       
lcid = 2052
```

## <a name="related-content-about-ssis-on-linux"></a>Contenuto correlato su SSIS in Linux
-   [Estrarre, trasformare e caricare i dati in Linux con SSIS](sql-server-linux-migrate-ssis.md)
-   [Installare SQL Server Integration Services (SSIS) in Linux](sql-server-linux-setup-ssis.md)
-   [Limitazioni e problemi noti per SSIS in Linux](sql-server-linux-ssis-known-issues.md)
-   [Esecuzione in Linux con cron del pacchetto di pianificazione di SQL Server Integration Services](sql-server-linux-schedule-ssis-packages.md)
