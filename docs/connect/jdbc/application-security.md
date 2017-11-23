---
title: Sicurezza delle applicazioni | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 940879b4-aa0f-41ce-a369-6cfc0e78e01d
caps.latest.revision: "23"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 77cfbbad8b17236b5609973095e10762e6624ba8
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="application-security"></a>Sicurezza dell'applicazione
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si utilizza il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], è importante prendere precauzioni per garantire la sicurezza dell'applicazione. Nelle sezioni seguenti vengono fornite informazioni relative alle procedure da implementare a questo scopo.  
  
## <a name="using-java-policy-permissions"></a>Utilizzo di autorizzazioni basate sui criteri Java  
 Quando si utilizza il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], è importante specificare le autorizzazioni di criteri Java necessarie che richiede il driver JDBC. Java Runtime Environment (JRE) offre un modello di sicurezza completo utilizzabile in fase di esecuzione per determinare se un thread dispone dei diritti di accesso a una risorsa. L'accesso può essere gestito grazie ai file dei criteri di sicurezza, i quali, a loro volta, sono gestiti dal distributore e dal ruolo sysadmin del contenitore. Le autorizzazioni elencate in questo argomento sono quelle che influiscono sul driver JDBC.  
  
 Di seguito è riportato un esempio di autorizzazione tipica disponibile nel file dei criteri:  
  
```  
// Example policy file entry.  
grant [signedBy <signer>,] [codeBase <code source>] {  
   permission  <class>  [<name> [, <action list>]];  
};  
```  
  
 La base di codice seguente deve essere limitata alla base del codice del driver JDBC in modo da concedere il livello minore possibile di privilegi.  
  
```  
grant codeBase "file:/install_dir/lib/-" {  
  
// Grant access to data source.  
permission java.util.PropertyPermission "java.naming.*", "read,write";  
  
// Specify which hosts can be connected to.  
permission java.net.socketPermission "host:port", "connect";  
  
// Logger permission to take advantage of logging.  
permission java.util.logging.LoggingPermission;  
  
// Grant listen/connect/accept permissions to the driver if   
// connecting to a named instance as the client driver.   
// This connects to a udp service and listens for a response.  
permission java.net.SocketPermission "*", "listen, connect, accept";   
};   
```  
  
> [!NOTE]  
>  Il codice "file:/install_dir/lib/-" fa riferimento alla directory di installazione del driver JDBC.  
  
## <a name="protecting-server-communication"></a>Protezione delle comunicazioni con il server  
 Quando si utilizza il driver JDBC per comunicare con un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database, è possibile proteggere il canale di comunicazione con Internet Protocol Security (IPSEC) o sicura Sockets Layer (SSL) o entrambi.  
  
 Il supporto SSL può essere utilizzato per fornire un livello aggiuntivo di protezione oltre a IPsec. Per ulteriori informazioni sull'utilizzo di SSL, vedere [utilizzando la crittografia SSL](../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione delle applicazioni del driver JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
