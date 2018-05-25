---
title: Crittografia delle connessioni a SQL Server in Linux | Documenti Microsoft
description: Questo articolo descrive la crittografia delle connessioni a SQL Server in Linux.
author: tmullaney
ms.date: 01/30/2018
ms.author: meetb
manager: craigg
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
helpviewer_keywords:
- Linux, encrypted connections
ms.openlocfilehash: f7b1dd57af300fc3e3fa61e469646211536b4653
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
---
# <a name="encrypting-connections-to-sql-server-on-linux"></a>Crittografia delle connessioni a SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in Linux può usare Transport Layer Security (TLS) per crittografare i dati trasmessi attraverso una rete tra un'applicazione client e un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] supporta gli stessi protocolli TLS in Windows e Linux: TLS 1.0, 1.1 e 1.2. Tuttavia, i passaggi per configurare TLS sono specifici del sistema operativo in cui [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è in esecuzione.  

## <a name="requirements-for-certificates"></a>Requisiti per i certificati 
Prima di iniziare, è necessario assicurarsi che i certificati di rispettare i requisiti seguenti:
- Ora di sistema corrente deve essere successiva alla proprietà del certificato valido dalla proprietà del certificato e prima valido.
- Il certificato deve essere destinato all'autenticazione del server. Ciò richiede che la proprietà utilizzo chiavi avanzato del certificato per specificare l'autenticazione Server (1.3.6.1.5.5.7.3.1).
- Tramite l'opzione KeySpec di AT_KEYEXCHANGE, è necessario creare il certificato. In genere, proprietà di utilizzo della chiave del certificato (KEY_USAGE) include anche la crittografia chiave (CERT_KEY_ENCIPHERMENT_KEY_USAGE).
- La proprietà Subject del certificato deve indicare che il nome comune (CN) è lo stesso come il nome host o nome di dominio completo (FQDN) del computer server. Nota: i certificati con caratteri jolly sono supportati. 

## <a name="overview"></a>Panoramica
TLS è utilizzato per crittografare le connessioni da un'applicazione client [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Quando è configurato correttamente, TLS fornisce privacy e l'integrità dei dati per le comunicazioni tra client e il server.  Le connessioni TLS possono essere avviato dal client o server avviato. 


## <a name="client-initiated-encryption"></a>Crittografia iniziata dal client 
- **Generare certificato** (/CN deve corrispondere il nome di dominio completo di host di SQL Server)

> [!NOTE]
> Per questo esempio viene usato un certificato autofirmato, questo non deve essere utilizzato per gli scenari di produzione. È consigliabile utilizzare i certificati della CA. 

        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **Configurare SQL Server**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssqlfqdn.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssqlfqdn.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 0 

- **Registrare il certificato nel computer client (Windows, Linux o Mac OS)**

    -   Se si utilizza certificato CA firmato, è necessario copiare il certificato di autorità di certificazione (CA) anziché il certificato utente nel computer client. 
    -   Se si utilizza il certificato autofirmato, è sufficiente copiare il file PEM nelle cartelle seguenti corrispondente alla distribuzione ed eseguire i comandi per abilitare il 
        - **Ubuntu**: il certificato di copia al ```/usr/share/ca-certificates/``` Rinomina estensione CRT usare i certificati ca dpkg reconfigure per abilitarlo come autorità di certificazione del certificato. 
        - **RHEL**: il certificato di copia al ```/etc/pki/ca-trust/source/anchors/``` utilizzare ```update-ca-trust``` per abilitarlo come autorità di certificazione del certificato.
        - **SUSE**: il certificato di copia al ```/usr/share/pki/trust/anchors/``` utilizzare ```update-ca-certificates``` per abilitarlo come autorità di certificazione del certificato.
        - **Windows**: Importa il file con estensione PEM come un certificato in utente corrente -> attendibile l'autorità di certificazione radice -> certificati
        - **macOS**: 
           - Copiare il certificato ```/usr/local/etc/openssl/certs```
           - Eseguire il comando seguente per ottenere il valore hash: ```/usr/local/Cellar/openssql/1.0.2l/openssql x509 -hash -in mssql.pem -noout```
           - Rinominare il certificato come valore. Esempio: ```mv mssql.pem dc2dd900.0```. Verificare che sia dc2dd900.0 in ```/usr/local/etc/openssl/certs```
    
-   **Esempi di stringhe di connessione** 

    - **[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]**   
  ![Finestra di dialogo connessione SQL Server Management Studio](media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png "finestra di dialogo connessione SQL Server Management Studio")  
  
    - **SQLCMD** 

            sqlcmd  -S <sqlhostname> -N -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=True; TrustServerCertificate=False;" 
    - **ODBC** 

            "Encrypt=Yes; TrustServerCertificate=no;" 
    - **JDBC** 
    
            "encrypt=true; trustServerCertificate=false;" 

## <a name="server-initiated-encryption"></a>Crittografia avviata dal server 

- **Generare certificato** (/CN deve corrispondere il nome di dominio completo di host di SQL Server)
        
        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **Configurare SQL Server**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssqlfqdn.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssqlfqdn.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 1 
        
-   **Esempi di stringhe di connessione** 

    - **SQLCMD**

            sqlcmd  -S <sqlhostname> -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=False; TrustServerCertificate=False;" 
    - **ODBC** 

            "Encrypt=no; TrustServerCertificate=no;"  
    - **JDBC** 
    
            "encrypt=false; trustServerCertificate=false;" 
            
> [!NOTE]
> Impostare **TrustServerCertificate** su True se il client non è possibile connettersi all'autorità di certificazione per convalidare l'autenticità del certificato

## <a name="common-connection-errors"></a>Errori di connessione comuni  

|Messaggio di errore |Fix |
|--- |--- |
|La catena di certificati è stato emesso da un'autorità di cui non è attendibile.  |Questo errore si verifica quando i client sono in grado di verificare la firma sul certificato presentato dal Server SQL durante l'handshake TLS. Verificare che il client considera attendibile uno di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] certificato direttamente oppure l'autorità di certificazione che ha firmato il certificato di SQL Server. |
|Il nome dell'entità di destinazione non è corretto.  |Assicurarsi che il campo nome comune nel certificato di SQL Server corrisponda al nome di server specificato nella stringa di connessione del client. |  
|Una connessione esistente chiusa forzatamente dall'host remoto. |Questo errore può verificarsi quando il client non supporta la versione del protocollo TLS richiesta da SQL Server. Ad esempio, se [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è configurato per richiedere TLS 1.2, assicurarsi che i client supportano anche il protocollo TLS 1.2. |
| | |   
