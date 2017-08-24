---
title: Crittografia delle connessioni a SQL Server in Linux | Documenti Microsoft
description: Questo argomento descrive la crittografia delle connessioni a SQL Server in Linux.
author: tmullaney
ms.date: 06/14/2017
ms.author: thmullan;rickbyh
manager: jhubbard
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
helpviewer_keywords:
- Linux, encrypted connections
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dfbfeee8292f3af4020185248d3d6a3fad3c71ea
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="encrypting-connections-to-sql-server-on-linux"></a>Crittografia delle connessioni a SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]in Linux possono usare Transport Layer Security (TLS) per crittografare i dati trasmessi in una rete tra un'applicazione client e un'istanza di [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]supporta gli stessi protocolli TLS in Windows e Linux: TLS 1.0, 1.1 e 1.2. Tuttavia, i passaggi per configurare TLS sono specifici del sistema operativo in cui [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] è in esecuzione.  
 
## <a name="typical-scenario"></a>Scenario tipico 
TLS è utilizzato per crittografare le connessioni da un'applicazione client [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]. Quando è configurato correttamente, TLS fornisce privacy e l'integrità dei dati per le comunicazioni tra client e il server.  
I passaggi seguenti viene descritto uno scenario tipico:  

1. Amministratore del database genera una chiave privata e un certificato (CSR) richiesta di firma. Nome comune del rappresentante del servizio deve corrispondere al nome di server che i client di specificare nella relativa stringa di connessione di SQL Server. Il nome comune è in genere il nome di dominio completo di [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] host. Per utilizzare lo stesso certificato per più server, è possibile utilizzare un carattere jolly nel nome comune (ad esempio, `"*.contoso.com"` anziché `"node1.contoso.com"`).   
2. Il rappresentante del servizio viene inviato a un'autorità di certificazione (CA) per la firma. L'autorità di certificazione deve essere considerato attendibile da tutti i computer client che si connettono a [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]. La CA restituisce un certificato firmato all'amministratore del database.   
3. Amministratore del database consente di configurare [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] per utilizzare la chiave privata e il certificato firmato per le connessioni TLS.   
4. I client specifichino `"Encrypt=True"` e `"TrustServerCertificate=False"` nelle stringhe di connessione. (I nomi di parametro specifici potrebbero essere diversi a seconda di quale driver è in uso). Client ora tentativo di crittografare le connessioni a SQL Server e verificare la validità del certificato di SQL Server per impedire attacchi man-in-the-middle.  
 
## <a name="configuring-tls-on-linux"></a>Configurazione del protocollo TLS su Linux  

Utilizzare `mssql-conf` a TLS per un'istanza di [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] su Linux. Sono supportate le seguenti opzioni:  

|Opzione |Description |
|--- |--- |
|`network.forceencryption` |Se è 1, quindi [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] forza tutte le connessioni da crittografare. Per impostazione predefinita, questa opzione è 0. |  
|`network.tlscert` |Il percorso assoluto per il certificato di file che [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] utilizza per TLS. Esempio: `/etc/ssl/certs/mssql.pem` il file del certificato deve essere accessibile dall'account mssql. Si consiglia di limitare l'accesso al file usando `chown mssql:mssql <file>; chmod 400 <file>`. |  
|`network.tlskey` |Il percorso assoluto per la chiave privata del file che [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] utilizza per TLS. Esempio: `/etc/ssl/private/mssql.key` il file del certificato deve essere accessibile dall'account mssql. Si consiglia di limitare l'accesso al file usando `chown mssql:mssql <file>; chmod 400 <file>`. | 
|`network.tlsprotocols` |Elenco delimitato da virgole di quali TLS sono consentiti i protocolli da SQL Server. [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]tenta sempre di negoziazione del protocollo consentito più attendibili. Se un client non supporta alcun protocollo consentito, [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] rifiuta il tentativo di connessione.  Per garantire la compatibilità, sono consentiti tutti i protocolli supportati per impostazione predefinita (1.2, 1.1, 1.0).  Se i client supportano TLS 1.2, si consiglia di consentire solo TLS 1.2. |  
|`network.tlsciphers` |Specifica le crittografie consentite dal [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] per TLS. Questa stringa deve essere formattata [formato di elenco di pacchetti di crittografia di OpenSSL](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html). In generale, non è necessario modificare questa opzione. <br /> Per impostazione predefinita, sono consentite le crittografie seguenti: <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |   
| | |
 
## <a name="example"></a>Esempio 
Questo esempio viene utilizzato un certificato autofirmato. Negli scenari di produzione normale, il certificato potrebbe essere firmato da un'autorità di certificazione considerata attendibile da tutti i client.  
 
### <a name="step-1-generate-private-key-and-certificate"></a>Passaggio 1: Generare certificati e chiavi private 
Aprire un comando terminal nel computer Linux in cui [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] è in esecuzione. Eseguire i comandi seguenti:  

- Generare un certificato autofirmato. Verificare che il /CN coincide con il nome di dominio completo di SQL Server host. Facoltativamente è possibile utilizzare caratteri jolly, ad esempio `'/CN=*.contoso.com'`.    
   ```  
   openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
   ```  

- Limitare l'accesso a`mssql`  
   ```  
   sudo chown mssql:mssql mssql.pem mssql.key 
   sudo chmod 400 mssql.pem mssql.key 
   ```  
 
- Spostare in directory di sistema SSL (facoltativa)  
   ```  
   sudo mv mssql.pem /etc/ssl/certs/ 
   sudo mv mssql.key /etc/ssl/private/ 
   ```  
 
### <a name="step-2-configure--includessnoversiondocsincludesssnoversion-mdmd"></a>Passaggio 2: configurare[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]  
Utilizzare `mssql-conf` configurare [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] per utilizzare il certificato e la chiave per TLS. Per una maggiore sicurezza, è anche possibile impostare TLS 1.2 come l'unico protocollo consentito e forzare tutti i client utilizzino connessioni crittografate.  

```  
sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssql.pem 
sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssql.key 
sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
sudo /opt/mssql/bin/mssql-conf set network.forceencryption 1 
```
 
### <a name="step-3-restart-includessnoversiondocsincludesssnoversion-mdmd"></a>Passaggio 3: riavviare[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] 
[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]deve essere riavviato rendere effettive le modifiche.  
`sudo systemctl restart mssql-server`  
 
### <a name="step-4-copy-self-signed-certificate-to-client-machines"></a>Passaggio 4: Copiare il certificato autofirmato per i computer client 
Poiché in questo esempio utilizza un certificato autofirmato per il [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] host, il certificato (non la chiave privata) deve essere copiato e installato come certificato radice attendibile in tutti i computer client che si connettono a [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]. Se il certificato è firmato da un'autorità di certificazione che è già considerato attendibile da tutti i client, questo passaggio non è più necessario. 
 
### <a name="step-5-connect-from-clients-using-tls"></a>Passaggio 5: Connessione dai client che utilizzano TLS 
Connettersi a [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] da un client con la crittografia attivata e `TrustServerCertificate` impostato su `False` nella stringa di connessione. Ecco alcuni esempi di come specificare questi parametri utilizzando diversi strumenti e driver. 

sqlcmd  
`sqlcmd -N -C -S mssql.contoso.com -U sa -P '<YourPassword>'`  

[!INCLUDE[ssmanstudiofull-md](../../docs/includes/ssmanstudiofull-md.md)]   
  ![Finestra di dialogo connessione SQL Server Management Studio](media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png "finestra di dialogo connessione SQL Server Management Studio")  
  
ADO.NET  
`"Encrypt=true; TrustServerCertificate=true;"`  

ODBC   
`"Encrypt=yes; TrustServerCertificate=no;"`  

JDBC  
`"encrypt=true; trustServerCertificate=false;" `

 
## <a name="common-connection-errors"></a>Errori di connessione comuni  

|Messaggio di errore |Fix |
|--- |--- |
|La catena di certificati è stato emesso da un'autorità di cui non è attendibile.  |Questo errore si verifica quando i client sono in grado di verificare la firma sul certificato presentato dal Server SQL durante l'handshake TLS. Verificare che il client considera attendibile uno di [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] certificato direttamente oppure l'autorità di certificazione che ha firmato il certificato di SQL Server. |
|Il nome dell'entità di destinazione non è corretto.  |Assicurarsi che il campo nome comune nel certificato di SQL Server corrisponda al nome di server specificato nella stringa di connessione del client. |  
|Una connessione esistente chiusa forzatamente dall'host remoto. |Questo errore può verificarsi quando il client non supporta la versione del protocollo TLS richiesta da SQL Server. Ad esempio, se [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] è configurato per richiedere TLS 1.2, assicurarsi che i client supportano anche il protocollo TLS 1.2. |
| | |   


