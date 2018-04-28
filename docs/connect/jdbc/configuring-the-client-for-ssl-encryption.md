---
title: Configurazione del Client per la crittografia SSL | Documenti Microsoft
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
ms.topic: article
ms.assetid: ae34cd1f-3569-4759-80c7-7c9b33b3e9eb
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7a046509ee94ffe0171dce0f7a1ac0e4a5187c3d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="configuring-the-client-for-ssl-encryption"></a>Configurazione del client per la crittografia SSL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] o del client per convalidare che il server sia corretto e che il certificato emesso da un'autorità di certificazione che il client considera attendibile. Per convalidare il certificato del server, è necessario che in fase di connessione venga fornito il materiale relativo all'attendibilità. L'autorità emittente del certificato del server deve inoltre essere un'Autorità di certificazione considerata attendibile dal client.  
  
 In questo argomento viene innanzitutto descritto come fornire il materiale relativo all'attendibilità nel computer client. Viene quindi descritto come importare un certificato del server nell'archivio di attendibilità del computer client quando l'istanza del certificato SSL (Secure Sockets Layer) di SQL Server viene emessa da un'Autorità di certificazione privata.  
  
 Per ulteriori informazioni sulla convalida del certificato del server, vedere la sezione Convalida certificato SSL del Server in [supporto SSL comprensione](../../connect/jdbc/understanding-ssl-support.md).  
  
## <a name="configuring-the-client-trust-store"></a>Configurazione dell'archivio di attendibilità del client  
 Convalida il certificato del server richiede che il materiale attendibile deve essere fornito al momento della connessione tramite **trustStore** e **trustStorePassword** le proprietà di connessione in modo esplicito, oppure utilizzare in modo implicito l'archivio di attendibilità predefinito di sottostante Java Virtual Machine (JVM). Per ulteriori informazioni su come impostare il **trustStore** e **trustStorePassword** proprietà in una stringa di connessione, vedere [connessione con la crittografia SSL](../../connect/jdbc/connecting-with-ssl-encryption.md).  
  
 Se il **trustStore** proprietà è non specificato o impostato su null, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] si basano sui provider di sicurezza di JVM sottostante, Java Secure Socket Extension (SunJSSE). Il provider SunJSSE fornisce TrustManager, che viene utilizzato per convalidare i certificati x. 509 restituiti da SQL Server contro il materiale relativo all'attendibilità fornito in un archivio di attendibilità predefinito.  
  
 Il TrustManager tenta di individuare il file trustStore predefinito nell'ordine di ricerca seguenti:  
  
-   Se la proprietà di sistema "javax.NET.SSL. trustStore" è definita, il TrustManager tenta di trovare il file trustStore predefinito utilizzando il nome file specificato da tale proprietà di sistema.  
  
-   Se la proprietà di sistema "javax.NET.SSL. trustStore" non è stata specificata e se il file "\<java-home >/lib/security/jssecacerts" è presente, viene utilizzato tale file.  
  
-   Se il file "\<java-home >/lib/security/cacerts" è presente, viene utilizzato tale file.  
  
 Per ulteriori informazioni, vedere la documentazione relativa all'interfaccia TrustManager SUNX509 nel sito Web Sun Microsystems.  
  
 Java Runtime Environment consente di impostare le proprietà di sistema trustStore e trustStorePassword come indicato di seguito:  
  
```  
java -Djavax.net.ssl.trustStore=C:\MyCertificates\storeName  
java -Djavax.net.ssl.trustStorePassword=storePassword  
```  
  
 In questo caso, in qualsiasi applicazione in esecuzione in questo ambiente JVM queste impostazioni vengono utilizzate come predefinite. Per ignorare le impostazioni predefinite dell'applicazione, è necessario impostare il **trustStore** e **trustStorePassword** le proprietà di connessione nella stringa di connessione o nel tipo appropriato metodo set del [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) classe.  
  
 Inoltre, è possibile configurare e gestire i file di archivio di attendibilità predefinito, ad esempio "\<java-home >/lib/security/jssecacerts" e "\<java-home >/lib/security/cacerts". A tale scopo, utilizzare l'utilità "keytool" JAVA installata con JRE (Java Runtime Environment). Per ulteriori informazioni su tale utilità, vedere la relativa documentazione nel sito Web Sun Microsystems.  
  
### <a name="importing-the-server-certificate-to-trust-store"></a>Importazione del certificato del server nell'archivio di attendibilità  
 Durante l'handshake SSL, il server invia il proprio certificato chiave pubblica al client. L'autorità emittente di un certificato chiave pubblica è nota come Autorità di certificazione (CA). Il client deve verificare che l'Autorità di certificazione sia considerata attendibile dal client stesso. Questa operazione può essere eseguita se la chiave pubblica delle Autorità di certificazione attendibili è conosciuta in anticipo. In genere, con JVM viene fornito un set predefinito di Autorità di certificazione attendibili.  
  
 Se l'istanza del certificato SSL di SQL Server viene emessa da un'Autorità di certificazione privata, è necessario aggiungere il certificato dell'Autorità di certificazione all'elenco di certificati attendibili nell'archivio di attendibilità del computer client.  
  
 A tale scopo, utilizzare l'utilità "keytool" JAVA installata con JRE (Java Runtime Environment). Nel prompt dei comandi seguente viene illustrato come utilizzare l'utilità "keytool" per importare un certificato da un file:  
  
```  
keytool -import -v -trustcacerts -alias myServer -file caCert.cer -keystore truststore.ks  
```  
  
 Nell'esempio viene utilizzato un file denominato "caCert.cer" come file di certificato. È necessario ottenere questo file di certificato dal server. Nei passaggi seguenti viene illustrato come esportare il certificato del server in un file:  
  
1.  Fare clic sul pulsante Start, scegliere Esegui e digitare MMC. MMC è l'acronimo di Microsoft Management Console.  
  
2.  In MMC aprire Certificati.  
  
3.  Espandere Personale, quindi Certificati.  
  
4.  Fare clic con il pulsante destro del mouse sul certificato del server, quindi scegliere Tutte le attività\Esporta.  
  
5.  Scegliere Avanti per passare alla pagina successiva a quella introduttiva dell'Esportazione guidata certificati.  
  
6.  Verificare che l'opzione "Non esportare la chiave privata" sia selezionata, quindi scegliere Avanti.  
  
7.  Verificare che sia selezionata l'opzione X.509 binario codificato DER (.CER) o Codificato Base 64 X.509 (.CER), quindi scegliere Avanti.  
  
8.  Immettere un nome per il file di esportazione.  
  
9. Scegliere Avanti, quindi Fine per esportare il certificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo della crittografia SSL](../../connect/jdbc/using-ssl-encryption.md)   
 [Protezione delle applicazioni del driver JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
