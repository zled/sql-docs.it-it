---
title: Connessione a SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data source names
- connection string keywords
- DSNs
ms.assetid: f95cdbce-e7c2-4e56-a9f7-8fa3a920a125
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b6ad6278da1a3e325356058df51238dc34018bf0
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="connecting-to-sql-server"></a>Connessione a SQL Server
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Questo argomento viene illustrato come creare una connessione a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database.  
  
## <a name="connection-properties"></a>Proprietà delle connessioni  

Vedere [DSN e parole chiave delle stringhe di connessione e gli attributi](../../../connect/odbc/dsn-connection-string-attribute.md) per tutte le parole chiave delle stringhe di connessione e gli attributi supportati nel Mac e Linux

> [!IMPORTANT]  
> Se si stabilisce una connessione a un database che usa il mirroring, ovvero dispone di un partner di failover, non specificare il nome del database nella stringa di connessione. Inviare invece un **utilizzare** *database_name* comando per la connessione al database prima di eseguire la query.  
  
Il valore passato al **Driver** parola chiave può essere uno dei seguenti:  
  
-   Il nome usato al momento dell'installazione del driver.

-   Il percorso di libreria dei driver, è stato specificato nel file ini del modello utilizzato per installare il driver.  

Per creare un DSN, creare (se necessario) e modificare il file **~/.odbc.ini** (`.odbc.ini` nella home directory) per un DSN utente accessibile solo all'utente corrente, o `/etc/odbc.ini` per un DSN di sistema (sono necessari privilegi amministrativi.) Di seguito è un file di esempio che mostra le voci necessarie minime per un DSN:  

```  
[MSSQLTest]  
Driver = ODBC Driver 13 for SQL Server  
Server = [protocol:]server[,port]  
#   
# Note:  
# Port is not a valid keyword in the odbc.ini file  
# for the Microsoft ODBC driver on Linux or macOS
#  
```  

È anche possibile specificare il protocollo e la porta per la connessione al server. Ad esempio, **Server = tcp:***servername***, 12345**. Si noti che è l'unico protocollo supportato dai driver di Linux e macOS `tcp`.

Per connettersi a un'istanza denominata su una porta statica, usare <b>Server =</b>*servername*,**numero_porta**. Connessione a una porta dinamica non è supportata.  

In alternativa, è possibile aggiungere le informazioni di DSN in un file di modello ed eseguire il comando seguente per aggiungerlo al `~/.odbc.ini` :
 - **Odbcinst -i -f -s** *template_file*  
 
È possibile verificare che il driver funzioni usando `isql` per testare la connessione oppure è possibile utilizzare questo comando:
 - **master.INFORMATION_SCHEMA.TABLES BCP out file OutFile.dat -S <server> - U <name> - P<password>**  

## <a name="using-secure-sockets-layer-ssl"></a>Uso di Secure Sockets Layer (SSL)  
È possibile utilizzare Secure Sockets Layer (SSL) per crittografare le connessioni a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. SSL protegge [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] nomi utente e password in rete. SSL verifica inoltre l'identità del server per la protezione dagli attacchi man-in-the-middle (MITM).  

L'abilitazione della crittografia aumenta la sicurezza a scapito delle prestazioni.

Per ulteriori informazioni, vedere [crittografia delle connessioni a SQL Server](http://go.microsoft.com/fwlink/?LinkId=220900) e [utilizzo della crittografia senza convalida](https://docs.microsoft.com/en-us/sql/relational-databases/native-client/features/using-encryption-without-validation).

Indipendentemente dalle impostazioni di **Encrypt** e **TrustServerCertificate**, le credenziali di accesso al server (nome utente e password) vengono sempre crittografate. La tabella seguente mostra l'effetto delle impostazioni di **Encrypt** e **TrustServerCertificate** .  

||**TrustServerCertificate=no**|**TrustServerCertificate=yes**|  
|-|-------------------------------------|------------------------------------|  
|**Encrypt=no**|Il certificato del server non viene verificato.<br /><br />I dati inviati dal client al server e viceversa non vengono crittografati.|Il certificato del server non viene verificato.<br /><br />I dati inviati dal client al server e viceversa non vengono crittografati.|  
|**Crittografare = Sì**|Il certificato del server viene verificato.<br /><br />I dati inviati dal client al server e viceversa vengono crittografati.<br /><br />Il nome (o l'indirizzo IP) in un nome comune soggetto (CN) o nome alternativo soggetto (SAN) in un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificato SSL deve corrispondere esattamente il server name (o indirizzo IP) specificato nella stringa di connessione.|Il certificato del server non viene verificato.<br /><br />I dati inviati dal client al server e viceversa vengono crittografati.|  

Per impostazione predefinita, le connessioni crittografate verificano sempre il certificato del server. Tuttavia, se ci si connette a un server che dispone di un certificato autofirmato, aggiungere il `TrustServerCertificate` opzione per ignorare il controllo il certificato nell'elenco delle autorità di certificazione attendibili:  

```  
Driver={ODBC Driver 13 for SQL Server};Server=ServerNameHere;Encrypt=YES;TrustServerCertificate=YES  
```  
  
SSL usa la libreria OpenSSL. La tabella seguente mostra le versioni minime supportate di OpenSSL e i percorsi dei file di archivio di scopi consentiti ai certificati predefiniti per ogni piattaforma:

|Piattaforma|Versione minima OpenSSL|Percorso del file di archivio di scopi consentiti ai certificati|  
|------------|---------------------------|--------------------------------------------|
|Debian 9|1.1.0|/etc/ssl/certs|
|Debian 8.71 |1.0.1|/etc/ssl/certs|
|macOS 10.13|1.0.2|/usr/local/etc/openssl/certs|
|macOS 10.12|1.0.2|/usr/local/etc/openssl/certs|
|OS X 10.11|1.0.2|/usr/local/etc/openssl/certs|
|Red Hat Enterprise Linux 7|1.0.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|
|SuSE Linux Enterprise 12 |1.0.1|/etc/ssl/certs|
|SuSE Linux Enterprise 11 |0.9.8|/etc/ssl/certs|
|Ubuntu 17.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.04 |1.0.2|/etc/ssl/certs|
  
È inoltre possibile specificare la crittografia nella stringa di connessione utilizzando il `Encrypt` opzione quando si utilizza **SQLDriverConnect** per la connessione.

## <a name="see-also"></a>Vedere anche  
[L'installazione di Microsoft ODBC Driver for SQL Server in Linux e macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)  
[Linee guida per la programmazione](../../../connect/odbc/linux-mac/programming-guidelines.md)
