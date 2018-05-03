---
title: Informazioni sul supporto SSL | Documenti Microsoft
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
ms.assetid: 073f3b9e-8edd-4815-88ea-de0655d0325e
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 12d7d92bd86cfd5851715c839f8772d4bc7ae94a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="understanding-ssl-support"></a>Informazioni sul supporto SSL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando ci si connette a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], se l'applicazione richiede la crittografia e l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è configurato per supportare la crittografia SSL, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] avvia l'handshake SSL. L'handshake consente al server e al client di negoziare la crittografia e gli algoritmi di crittografia da utilizzare per proteggere i dati. Al termine dell'handshake SSL, il client e il server possono inviare in modo protetto i dati crittografati. Durante l'handshake SSL, il server invia il proprio certificato chiave pubblica al client. L'autorità emittente di un certificato chiave pubblica è nota come Autorità di certificazione (CA). Il client è responsabile della convalida dell'attendibilità dell'Autorità di certificazione per il client stesso.  
  
 Se l'applicazione non richiede la crittografia, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] non forza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per supportare la crittografia SSL. Se il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istanza non è configurata per forzare la crittografia SSL, viene stabilita una connessione senza crittografia. Se il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istanza è configurata per forzare la crittografia SSL, il driver verrà automaticamente attivare la crittografia SSL durante l'esecuzione in linguaggio macchina virtuale (ambiente JVM correttamente configurato), o altrimenti la connessione viene terminata e il driver genererà un errore.  
  
> [!NOTE]  
>  Verificare che il valore passato a **serverName** corrisponda esattamente al nome DNS o il nome comune (CN) nell'alternativo nome soggetto (SAN) nel certificato del server per una connessione SSL riesca.  
  
> [!NOTE]  
>  Per ulteriori informazioni su come configurare SSL per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere la crittografia delle connessioni a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] argomento [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="remarks"></a>Osservazioni  
 Per consentire alle applicazioni di utilizzare la crittografia SSL, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] sono state introdotte le seguenti proprietà di connessione a partire dalla versione 1.2: **crittografare**, **trustServerCertificate**, **trustStore**, **trustStorePassword**, e **hostNameInCertificate**. Per ulteriori informazioni, vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Nella tabella seguente sono riepilogati come [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] comportamento per i possibili scenari di connessione SSL. In ogni scenario viene utilizzato un set di proprietà di connessione SSL diverso. La tabella include i valori seguenti:  
  
-   **vuoto**: "la proprietà non esiste nella stringa di connessione"  
  
-   **valore**: "la proprietà esiste nella stringa di connessione e il relativo valore è valido"  
  
-   **qualsiasi**: "Non è importante se la proprietà esiste nella stringa di connessione o il relativo valore è valido"  
  
> [!NOTE]  
>  Lo stesso comportamento si applica per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione e l'autenticazione integrata di Windows.  
  
|encrypt|trustServerCertificate|hostNameInCertificate|trustStore|trustStorePassword|Comportamento|  
|-------------|----------------------------|---------------------------|----------------|------------------------|--------------|  
|false o blank|any|any|any|any|Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] non forza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per supportare la crittografia SSL. Se il server dispone di un certificato autofirmato, tramite il driver viene avviato lo scambio del certificato SSL. Il certificato SSL non viene convalidato e vengono crittografate solo le credenziali, nel pacchetto di accesso.<br /><br /> Se il server richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL. Il certificato SSL non viene convalidato, ma viene crittografata l'intera comunicazione.|  
|true|true|any|any|any|Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richieste per utilizzare la crittografia SSL con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL. Si noti che se il **trustServerCertificate** proprietà è impostata su "true", il driver non convaliderà il certificato SSL.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.|  
|true|false o blank|vuoto|vuoto|vuoto|Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richieste per utilizzare la crittografia SSL con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver utilizzerà il **serverName** proprietà specificata nell'URL di connessione per convalidare il certificato SSL del server e si basano su regole di ricerca della factory di gestione attendibile per determinare l'archivio certificati da utilizzare.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.|  
|true|false o blank|Valore|vuoto|vuoto|Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richieste per utilizzare la crittografia SSL con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver convaliderà valore del soggetto del certificato SSL con il valore specificato per il **hostNameInCertificate** proprietà.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.|  
|true|false o blank|vuoto|Valore|Valore|Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richieste per utilizzare la crittografia SSL con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver utilizzerà il **trustStore** valore della proprietà per trovare il file trustStore del certificato e **trustStorePassword** valore della proprietà per controllare l'integrità del file trustStore.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.|  
|true|false o blank|vuoto|vuoto|Valore|Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richieste per utilizzare la crittografia SSL con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver utilizzerà il **trustStorePassword** valore della proprietà per controllare l'integrità del file trustStore predefinito.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.|  
|true|false o blank|vuoto|Valore|vuoto|Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richieste per utilizzare la crittografia SSL con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver utilizzerà il **trustStore** valore della proprietà per cercare il percorso del file trustStore.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.|  
|true|false o blank|Valore|vuoto|Valore|Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richieste per utilizzare la crittografia SSL con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver utilizzerà il **trustStorePassword** valore della proprietà per controllare l'integrità del file trustStore predefinito. Inoltre, il driver utilizzerà il **hostNameInCertificate** valore della proprietà per convalidare il certificato SSL.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.|  
|true|false o blank|Valore|Valore|vuoto|Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richieste per utilizzare la crittografia SSL con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver utilizzerà il **trustStore** valore della proprietà per cercare il percorso del file trustStore. Inoltre, il driver utilizzerà il **hostNameInCertificate** valore della proprietà per convalidare il certificato SSL.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.|  
|true|false o blank|Valore|Valore|Valore|Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richieste per utilizzare la crittografia SSL con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver utilizzerà il **trustStore** valore della proprietà per trovare il file trustStore del certificato e **trustStorePassword** valore della proprietà per controllare l'integrità del file trustStore. Inoltre, il driver utilizzerà il **hostNameInCertificate** valore della proprietà per convalidare il certificato SSL.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.|  
  
 Se la proprietà encrypt è impostata su **true**, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Usa provider di sicurezza JSSE predefinito di JVM per negoziare la crittografia SSL con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È possibile che il provider di sicurezza predefinito non supporti tutte le funzionalità necessarie per negoziare la crittografia SSL. Ad esempio, il provider di sicurezza predefinito non può supportare la dimensione della chiave pubblica RSA utilizzata nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] certificato SSL. In questo caso, è possibile che venga generato un errore dal provider di sicurezza predefinito, a causa del quale la connessione viene terminata dal driver JDBC. Per risolvere il problema, eseguire una delle operazioni seguenti:  
  
-   Configurare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] con un certificato server con una chiave pubblica RSA più piccola  
  
-   Configurare JVM per l'utilizzo di un provider di sicurezza JSSE diverso nel "\<java-home > / lib/security/java.security" file delle proprietà di sicurezza  
  
-   Utilizzare una versione di JVM diversa.  
  
## <a name="validating-server-ssl-certificate"></a>Convalida del certificato SSL del server  
 Durante l'handshake SSL, il server invia il proprio certificato chiave pubblica al client. Il driver JDBC o il client deve convalidare che il certificato del server sia stato emesso da un'Autorità di certificazione considerata attendibile dal client. Il driver richiede che il certificato del server soddisfi le condizioni seguenti:  
  
-   Il certificato è stato emesso da un'Autorità di certificazione attendibile.  
  
-   Il certificato deve essere emesso per l'autenticazione del server.  
  
-   Il certificato non è scaduto.  
  
-   Il nome comune (CN) nell'oggetto o un nome DNS nell'alternativo nome soggetto (SAN) del certificato corrisponde esattamente il **serverName** valore specificato nella stringa di connessione o, se specificato, il  **hostNameInCertificate** valore della proprietà.  
  
-   Un nome DNS può includere caratteri jolly. Ma la [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] non supporta la corrispondenza con caratteri jolly. Vale a dire, abc.com non corrisponderà a *.com, ma \*corrisponderà a COM \*. com.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo della crittografia SSL](../../connect/jdbc/using-ssl-encryption.md)   
 [Protezione delle applicazioni del driver JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
