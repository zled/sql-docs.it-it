---
title: Connessione con la crittografia SSL | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ec91fa8a-ab7e-4c1e-a05a-d7951ddf33b1
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49c6aaf771bb5335b8ba649869a4a8cf13894e82
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32832616"
---
# <a name="connecting-with-ssl-encryption"></a>Connessione tramite la crittografia SSL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Negli esempi di questo argomento viene descritto come utilizzare le proprietà della stringa di connessione che consentono alle applicazioni di utilizzare la crittografia SSL (Secure Sockets Layer) in un'applicazione Java. Per ulteriori informazioni sulla connessione nuove stringhe proprietà, ad esempio **crittografare**, **trustServerCertificate**, **trustStore**,  **trustStorePassword**, e **hostNameInCertificate**, vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Quando il **crittografare** è impostata su **true** e **trustServerCertificate** è impostata su **true**, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] non verrà convalidato il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] certificato SSL. Si tratta in genere necessario per consentire le connessioni in ambienti di test, ad esempio la posizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istanza dispone solo di un certificato autofirmato.  
  
 Esempio di codice seguente viene illustrato come impostare il **trustServerCertificate** proprietà in una stringa di connessione:  
  
```  
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true;trustServerCertificate=true";  
```  
  
 Quando il **crittografare** è impostata su **true** e **trustServerCertificate** è impostata su **false**, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] convaliderà il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] certificato SSL. La convalida del certificato del server fa parte dell'handshake SSL e assicura che il server a cui si esegue la connessione sia quello corretto. Per convalidare il certificato del server, il materiale attendibile deve essere fornito al momento della connessione tramite **trustStore** e **trustStorePassword** le proprietà di connessione in modo esplicito o tramite attendibilità predefinito di Java Virtual Machine (JVM sottostante) dell'archivio in modo implicito.  
  
 Il **trustStore** proprietà specifica il percorso (incluso il nome file) del file trustStore del certificato, che contiene l'elenco di certificati che il client considera attendibile. Il **trustStorePassword** proprietà specifica la password utilizzata per controllare l'integrità dei dati del file trustStore. Per ulteriori informazioni sull'uso di archivio di attendibilità predefinito di JVM, vedere il [configurazione del Client per la crittografia SSL](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md).  
  
 Esempio di codice seguente viene illustrato come impostare il **trustStore** e **trustStorePassword** proprietà in una stringa di connessione:  
  
```  
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword";  
```  
  
 Il Driver JDBC fornisce una proprietà aggiuntiva, **hostNameInCertificate**, che specifica il nome host del server. Il valore di questa proprietà deve corrispondere alla proprietà relativa al soggetto del certificato.  
  
 Esempio di codice seguente viene illustrato come utilizzare il **hostNameInCertificate** proprietà in una stringa di connessione:  
  
```  
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword" +  
     "hostNameInCertificate=hostName";  
```  
  
> [!NOTE]  
>  In alternativa, è possibile impostare il valore della proprietà di connessione, utilizzando i **setter** metodi forniti dal [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) classe.  
  
 Se il **crittografare** è impostata su **true** e **trustServerCertificate** è impostata su **false** e se il nome server nel stringa di connessione non corrisponde al nome del server nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] certificato SSL, verrà generato il seguente errore: il driver non è in grado di stabilire una connessione sicura a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] mediante la crittografia di livello SSL (Secure Sockets). Errore: "java.security.cert.CertificateException: Impossibile convalidare il nome del server in un certificato durante l'inizializzazione di SSL (Secure Sockets Layer)".  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo della crittografia SSL](../../connect/jdbc/using-ssl-encryption.md)   
 [Protezione delle applicazioni del driver JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
