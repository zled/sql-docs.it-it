---
title: Connessione a un database SQL di Azure | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 49645b1f-39b1-4757-bda1-c51ebc375c34
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 454dbfc43af720a7c2bb8c875c0e119437dc4d92
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-an-azure-sql-database"></a>Connessione a un database SQL di Azure
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  In questo argomento vengono illustrati i problemi quando si utilizza il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] per connettersi a un [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]. Per ulteriori informazioni sulla connessione a un [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], vedere:  
  
-   [SQL Azure Database](http://go.microsoft.com/fwlink/?LinkID=202490)  
  
-   [Procedura: connettersi a SQL Azure tramite JDBC](http://msdn.microsoft.com/library/gg715284.aspx)  
  
-   [Utilizzo di SQL Azure in Java](http://msdn.microsoft.com/library/windowsazure/hh749029(VS.103).aspx)

-   [Connessione tramite autenticazione di Azure Active Directory](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md)  
  
## <a name="details"></a>Dettagli  
 Quando ci si connette a un [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], è necessario connettersi al database master per chiamare **Getcatalogs**.  
 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] non supporta la restituzione dell'intero set di cataloghi da un database utente. **SQLServerDatabaseMetaData.getCatalogs** utilizza la vista sys. Databases per ottenere i cataloghi. Fare riferimento alla trattazione delle autorizzazioni in [Sys. Databases (Database di SQL Azure)](http://go.microsoft.com/fwlink/?LinkId=217396) comprendere **Getcatalogs** comportamento su un [!INCLUDE[ssAzure](../../includes/ssazure_md.md)].  
  
 Connessioni eliminate  
 Quando ci si connette a un [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], le connessioni inattive possono essere terminate da un componente di rete (ad esempio un firewall) dopo un periodo di inattività. In questo contesto esistono due tipi di inattività:  
  
-   Inattività a livello TCP, in cui le connessioni possono essere eliminate da un certo numero di dispositivi di rete.  
  
-   Inattività in SQL Azure Gateway, in cui TCP **keepalive** messaggi potrebbero verificarsi (rendendo la connessione non inattiva da una prospettiva TCP), ma non era una query attiva in 30 minuti. In questo scenario il gateway determinerà che la connessione TDS è inattiva da 30 minuti e la terminerà.  
  
 Per evitare l'eliminazione di connessioni inattive da un componente di rete, è consigliabile impostare le seguenti impostazioni del Registro di sistema, o le relative equivalenti non Windows, nel sistema operativo in cui viene caricato il driver:  
  
|Impostazione del Registro di sistema|Valore consigliato|  
|----------------------|-----------------------|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ parametri \ KeepAliveTime|30000|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ parametri \ KeepAliveInterval|1000|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ parametri \ TcpMaxDataRetransmissions|10|  
  
 È necessario riavviare il computer affinché le impostazioni del Registro di sistema abbiano effetto.  
  
 A tale scopo, durante l'esecuzione di Windows Azure creare un'attività di avvio per aggiungere le chiavi del Registro di sistema.  Ad esempio, aggiungere l'attività di avvio al file di definizione del servizio:  
  
```  
<Startup>  
    <Task commandLine="AddKeepAlive.cmd" executionContext="elevated" taskType="simple">  
    </Task>  
</Startup>  
```  
  
 Successivamente, aggiungere il file AddKeepAlive.cmd al progetto in uso. Impostare l'impostazione "Copia nella directory di output" su Copia sempre. Di seguito è riportato un esempio di file AddKeepAlive.cmd:  
  
```  
if exist keepalive.txt goto done  
time /t > keepalive.txt  
REM Workaround for JDBC keep alive on SQL Azure  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveTime /t REG_DWORD /d 30000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveInterval /t REG_DWORD /d 1000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v TcpMaxDataRetransmissions /t REG_DWORD /d 10 >> keepalive.txt  
shutdown /r /t 1  
:done  
```  
  
 Accodamento del nome del server all'ID utente nella stringa di connessione  
 Prima della versione 4.0 del [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], durante la connessione a un [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], è necessario aggiungere il nome del server per l'ID utente nella stringa di connessione. Ad esempio, user@servername. A partire dalla versione 4.0 del [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], non è più necessario aggiungere @servername all'ID utente nella stringa di connessione.  
  
 Impostazione di hostNameInCertificate obbligatoria per l'utilizzo della crittografia  
 Quando ci si connette a un [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], è necessario specificare **hostNameInCertificate** se si specifica **crittografare = true**. (Se il nome del server nella stringa di connessione è *shortName*. *domainName*, impostare il **hostNameInCertificate** proprietà \*. *domainName*.)  
  
 Esempio:  
  
```  
jdbc:sqlserver://abcd.int.mscds.com;databaseName= myDatabase;user=myName;password=myPassword;encrypt=true;hostNameInCertificate= *.int.mscds.com;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione a SQL Server con il driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
