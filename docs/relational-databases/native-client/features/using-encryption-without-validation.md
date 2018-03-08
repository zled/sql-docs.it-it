---
title: Utilizzo della crittografia senza convalida | Documenti Microsoft
ms.custom: 
ms.date: 12/21/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], encryption
- cryptography [SQL Server Native Client]
- SQLNCLI, encryption
- encryption [SQL Server Native Client]
- SQL Server Native Client, encryption
ms.assetid: f4c63206-80bb-4d31-84ae-ccfcd563effa
caps.latest.revision: "18"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 943a6aa49feee1d9bbd7a8fdc59392479e104735
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="using-encryption-without-validation"></a>Utilizzo della crittografia senza convalida
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] crittografa sempre pacchetti di rete associati all'accesso. Se non è stato eseguito il provisioning di nessun certificato nel server quando viene avviato, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] genera un certificato autofirmato utilizzato per crittografare pacchetti di accesso.  

I certificati autofirmati non garantiscono protezione. L'handshake crittografato è basato su NT LAN Manager (NTLM). È consigliabile che si esegua il provisioning di un certificato verificabile in SQL Server per la connettività protetta. Sicurezza TLS (Transport Layer) è possibile proteggere solo con la convalida dei certificati.

Le applicazioni possono inoltre richiedere l'attivazione della crittografia per tutto il traffico di rete mediante le parole chiave della stringa di connessione o le proprietà di connessione. Le parole chiave sono "Encrypt" per ODBC e OLE DB quando si utilizza una stringa del provider con **IDBInitialize:: Initialize**, o "Use Encryption for Data" per ADO e OLE DB quando si utilizza una stringa di inizializzazione con **IDataInitialize** . Può anche essere configurato da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager utilizzando il **Forza crittografia protocollo** opzione e la configurazione per il client di richiedere connessioni crittografate. Per impostazione predefinita, la crittografia di tutto il traffico di rete per una connessione richiede che nel server sia stato eseguito il provisioning di un certificato. Impostando il client per considerare attendibile il certificato nel server, potrebbe diventare vulnerabile ad attacchi man-in-the-middle. Se si distribuisce un certificato verificabile sul server, assicurarsi di modificare le impostazioni del client relative al trust del certificato su FALSE.

Per informazioni sulle parole chiave di stringa di connessione, vedere [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Per abilitare la crittografia da utilizzare quando non è stato fornito un certificato sul server, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager può essere utilizzato per impostare entrambi i **Forza crittografia protocollo** e **considera attendibile certificato Server**  opzioni. In questo caso, la crittografia utilizzerà un certificato server autofirmato senza convalida se nel server non è stato eseguito il provisioning di alcun certificato verificabile.  
  
 Le applicazioni possono inoltre utilizzare la parola chiave "TrustServerCertificate" o il relativo attributo di connessione associato per garantire l'utilizzo della crittografia. Le impostazioni dell'applicazione non riducono mai il livello di sicurezza impostato dal client di Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], bensì possono potenziarlo. Ad esempio, se **Forza crittografia protocollo** non è impostata per il client, un'applicazione può richiedere la crittografia. Per garantire che la crittografia venga applicata anche quando non è stato eseguito il provisioning di un certificato server, un'applicazione può richiedere la crittografia e "TrustServerCertificate". Tuttavia, se TrustServerCertificate non è attivata nella configurazione client, è comunque necessario il provisioning di un certificato server. Nella tabella seguente vengono descritti tutti i casi:  
  
|Impostazione client Forza crittografia protocollo|Impostazione client Considera attendibile certificato server|Attributo/stringa di connessione Encrypt/Use Encryption for Data|Attributo/stringa di connessione Trust Server Certificate|Risultato|  
|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------|------------|  
|no|N/D|No (impostazione predefinita)|Ignorato|Nessuna crittografia.|  
|no|N/D|Sì|No (impostazione predefinita)|La crittografia viene applicata solo se è disponibile un certificato server verificabile; in caso contrario, il tentativo di connessione non riesce.|  
|no|N/D|Sì|Sì|La crittografia viene sempre applicata, ma può essere utilizzato un certificato server auto-firmato.|  
|Sì|no|Ignorato|Ignorato|La crittografia viene applicata solo se è disponibile un certificato server verificabile; in caso contrario, il tentativo di connessione non riesce.|  
|Sì|Sì|No (impostazione predefinita)|Ignorato|La crittografia viene sempre applicata, ma può essere utilizzato un certificato server auto-firmato.|  
|Sì|Sì|Sì|No (impostazione predefinita)|La crittografia viene applicata solo se è disponibile un certificato server verificabile; in caso contrario, il tentativo di connessione non riesce.|  
|Sì|Sì|Sì|Sì|La crittografia viene sempre applicata, ma può essere utilizzato un certificato server auto-firmato.|  
||||||

> [!CAUTION]
> Nella tabella precedente solo fornisce una Guida al comportamento di sistema in diverse configurazioni. Per una connettività sicura, verificare che il client e server di richiedere la crittografia. Verificare inoltre che il server disponga di un certificato verificabile e che il **TrustServerCertificate** impostazione sul client è impostata su FALSE.

## <a name="sql-server-native-client-ole-db-provider"></a>Provider OLE DB di SQL Server Native Client  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta la crittografia senza convalida tramite l'aggiunta di SSPROP_INIT_TRUST_SERVER_CERTIFICATE proprietà dell'origine dati l'inizializzazione, che viene implementata nel set di proprietà DBPROPSET_SQLSERVERDBINIT set. È stata inoltre aggiunta una nuova parola chiave, "TrustServerCertificate", per la stringa di connessione. Accetta i valori yes o no. Il valore predefinito è no. Quando si utilizzano i componenti del servizio, accetta i valori true o false; false è l'impostazione predefinita.  
  
 Per ulteriori informazioni sui miglioramenti apportati al set di proprietà DBPROPSET_SQLSERVERDBINIT, vedere [proprietà di inizializzazione e autorizzazione](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>Driver ODBC di SQL Server Native Client  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la crittografia senza convalida tramite aggiunte al [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) e [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) funzioni. SQL_COPT_SS_TRUST_SERVER_CERTIFICATE è stato aggiunto per accettare SQL_TRUST_SERVER_CERTIFICATE_YES o SQL_TRUST_SERVER_CERTIFICATE_NO. SQL_TRUST_SERVER_CERTIFICATE_NO è l'impostazione predefinita. È stata inoltre aggiunta una nuova parola chiave, "TrustServerCertificate", per la stringa di connessione. Accetta i valori yes o no. Il valore predefinito è "no".  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
