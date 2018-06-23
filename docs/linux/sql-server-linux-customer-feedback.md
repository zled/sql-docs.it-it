---
title: I suggerimenti dei clienti per SQL Server in Linux | Documenti Microsoft
description: Viene descritto come dei clienti di SQL Server vengono raccolti e configurato in Linux.
author: annashres
ms.author: anshrest
manager: craigg
ms.date: 06/22/2018
ms.topic: conceptual
ms.prod: sql
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 69a1e82544ad1566cdf9ec1937d88a8cc2a61975
ms.sourcegitcommit: 23e71a8afba194e0893f31532db0aaa29288acb2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2018
ms.locfileid: "36329506"
---
# <a name="customer-feedback-for-sql-server-on-linux"></a>Suggerimenti dei clienti per SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Per impostazione predefinita, Microsoft SQL Server raccoglie informazioni su come i clienti usano l'applicazione. In particolare, SQL Server raccoglie informazioni sull'esperienza di installazione, l'utilizzo e le prestazioni. Queste informazioni consentono a Microsoft di migliorare il prodotto per meglio soddisfare le esigenze dei clienti. Ad esempio, Microsoft raccoglie informazioni sui tipi di codici di errore riscontrati dai clienti in modo da poter correggere i bug correlati, migliorare la documentazione su come usare SQL Server e determinare se occorre aggiungere funzionalità al prodotto per offrire un'esperienza migliore ai clienti.

Questo documento fornisce informazioni dettagliate su quali tipi di informazioni vengono raccolti e su come configurare Microsoft SQL Server in Linux per l'invio che raccolti informazioni a Microsoft. SQL Server 2017 include informativa sulla privacy in cui viene indicato quali informazioni si e non raccolgono dagli utenti. Per altre informazioni, vedere la [informativa sulla privacy](http://go.microsoft.com/fwlink/?LinkID=868444).

In particolare, Microsoft non invia alcuna informazione dei tipi seguenti tramite questo meccanismo:

- Qualsiasi valore all'interno delle tabelle utente
- Credenziali di accesso o altre informazioni di autenticazione
- Informazioni personali

SQL Server 2017 raccoglie e invia sempre informazioni sull'esperienza di installazione dal processo di installazione, in modo che sia possibile individuare e correggere eventuali problemi di installazione riscontrati dai clienti. 2017 di SQL Server può essere configurato per non inviare a Microsoft tramite dati (per istanza per ogni server) **mssql-conf**. MSSQL-conf è uno script di configurazione installato con SQL Server 2017 per Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Ubuntu.

> [!NOTE]
> È possibile disabilitare l'invio di informazioni a Microsoft solo nelle versioni a pagamento di SQL Server.

## <a name="disable-customer-feedback"></a>Disabilitare i suggerimenti dei clienti

Questa opzione consente di modificare se SQL Server Invia commenti e suggerimenti a Microsoft o non. Per impostazione predefinita, questo valore è impostato su true. Per modificare il valore, eseguire i comandi seguenti:

> [!IMPORTANT]
> È possibile non disattivare i suggerimenti dei clienti gratuitamente edizioni di SQL Server Express e Developer.

### <a name="on-red-hat-suse-and-ubuntu"></a>In Ubuntu, SUSE e Red Hat

1. Eseguire lo script mssql-conf come radice con il **impostata** comando **telemetry.customerfeedback**. Nell'esempio seguente consente di disattivare i suggerimenti dei clienti, specificando **false**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. Riavviare il servizio SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>In Docker
Per disabilitare i suggerimenti dei clienti in docker, è necessario disporre Docker [rendere i dati persistenti](sql-server-linux-configure-docker.md). 

1. Aggiungere un `mssql.conf` file con le righe `[telemetry]` e `customerfeedback = false` nella directory host:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```
2. Esecuzione dell'immagine contenitore
   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
   ```
   
## <a name="local-audit-for-sql-server-on-linux-usage-feedback-collection"></a>Controllo locale per SQL Server nella raccolta di commenti e suggerimenti sull'utilizzo di Linux

Microsoft SQL Server 2017 include funzionalità abilitate per Internet che possono raccogliere e inviare a Microsoft informazioni su un computer o dispositivo ("informazioni standard sul computer"). Il componente del controllo locale della raccolta di commenti e suggerimenti sull'utilizzo di SQL Server è possibile scrivere i dati raccolti dal servizio in una cartella designata, che rappresenta i dati (log) che verranno inviati a Microsoft. Lo scopo del controllo locale è quello di consentire ai clienti di visualizzare tutti i dati che Microsoft raccoglie con questa funzionalità, per motivi di conformità alle normative o rispetto della privacy.

In SQL Server in Linux, controllo locale è configurabile a livello di istanza per il motore di Database di SQL Server. Altri componenti di SQL Server e strumenti di SQL Server non dispone di una funzione di controllo locale per la raccolta di commenti e suggerimenti di utilizzo.

### <a name="enable-local-audit"></a>Abilitare controllo locale

Questa opzione Abilita controllo locale e consente di impostare la directory in cui vengono creati i log di controllo locale.

1. Creare una directory di destinazione per i nuovi log di controllo locale. Nell'esempio seguente crea un nuovo **/tmp/controllo** directory:

   ```bash
   sudo mkdir /tmp/audit
   ```

1. Modificare il proprietario e il gruppo della directory in cui il **mssql** utente:

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

1. Eseguire lo script mssql-conf come radice con il **impostata** comando **telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

1. Riavviare il servizio SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>In Docker
Per abilitare controllo locale in docker, è necessario disporre Docker [rendere i dati persistenti](sql-server-linux-configure-docker.md). 

1. La directory di destinazione per i nuovi log di controllo locale sarà nel contenitore. Creare una directory di destinazione per i nuovi log di controllo locale nella directory host nel computer. Nell'esempio seguente crea un nuovo **/audit** directory:

   ```bash
   sudo mkdir <host directory>/audit
   ```

   
1. Aggiungere un `mssql.conf` file con le righe `[telemetry]` e `userrequestedlocalauditdirectory = <host directory>/audit` nella directory host:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```
2. Esecuzione dell'immagine contenitore
   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
   ```
   
## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su SQL Server in Linux, vedere la [Panoramica di SQL Server in Linux](sql-server-linux-overview.md).
