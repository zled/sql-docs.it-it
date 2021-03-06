---
title: Informazioni sul supporto SSL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 073f3b9e-8edd-4815-88ea-de0655d0325e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bcf632e4953232144b82ba9701c62eb1d226d127
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47697419"
---
# <a name="understanding-ssl-support"></a>Informazioni sul supporto SSL

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Se durante la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'applicazione richiede la crittografia e l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è configurata per il supporto della crittografia SSL, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] avvia l'handshake SSL. L'handshake consente al server e al client di negoziare la crittografia e gli algoritmi di crittografia da utilizzare per proteggere i dati. Al termine dell'handshake SSL, il client e il server possono inviare in modo protetto i dati crittografati. Durante l'handshake SSL, il server invia il proprio certificato chiave pubblica al client. L'autorità emittente di un certificato chiave pubblica è nota come Autorità di certificazione (CA). Il client è responsabile della convalida dell'attendibilità dell'Autorità di certificazione per il client stesso.  
  
Se l'applicazione non richiede la crittografia, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] non forza il supporto della crittografia SSL in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è configurata per la forzatura della crittografia SSL, viene stabilita una connessione senza crittografia. Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è configurata per la forzatura della crittografia SSL, il driver abilita questo tipo di crittografia automaticamente durante l'esecuzione in un ambiente Java Virtual Machine (JVM) correttamente configurato. In caso contrario, la connessione viene terminata e il driver genera un errore.  
  
> [!NOTE]  
> Perché una connessione SSL riesca, assicurarsi che il valore passato a **serverName** corrisponda esattamente al nome comune o al nome DNS nel nome soggetto alternativo (SAN, Subject Alternate Name) nel certificato del server.  
>
> Per altre informazioni su come configurare SSL per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere l'argomento Crittografia delle connessioni a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="remarks"></a>Remarks

Per consentire alle applicazioni di usare la crittografia SSL, a partire dalla versione 1.2 di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] sono state introdotte le proprietà di connessione **encrypt**, **trustServerCertificate**, **trustStore**, **trustStorePassword** e **hostNameInCertificate**. Per altre informazioni, vedere [Impostazione delle proprietà delle connessioni](../../connect/jdbc/setting-the-connection-properties.md).  
  
 La tabella seguente offre un riepilogo del comportamento della versione di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] per i possibili scenari di connessione SSL. In ogni scenario viene utilizzato un set di proprietà di connessione SSL diverso. La tabella include i valori seguenti:  
  
- **vuoto**: "la proprietà non esiste nella stringa di connessione"  
  
- **valore**: "la proprietà è presente nella stringa di connessione e il relativo valore è valido"  
  
- **qualsiasi**: "Non è importante se la proprietà è presente nella stringa di connessione o il relativo valore è valido"  
  
> [!NOTE]  
> Lo stesso comportamento si applica all'autenticazione utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e all'autenticazione integrata di Windows.  
  
| encrypt        | trustServerCertificate | hostNameInCertificate | trustStore | trustStorePassword | Comportamento                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| -------------- | ---------------------- | --------------------- | ---------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| false o blank | any                    | any                   | any        | any                | [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] non forza il supporto della crittografia SSL in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se il server dispone di un certificato autofirmato, tramite il driver viene avviato lo scambio del certificato SSL. Il certificato SSL non viene convalidato e vengono crittografate solo le credenziali, nel pacchetto di accesso.<br /><br /> Se il server richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL. Il certificato SSL non viene convalidato, ma viene crittografata l'intera comunicazione.                                                                                                                                                                                    |
| true           | true                   | any                   | any        | any                | [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richiede di usare la crittografia SSL con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL. Si noti che se la proprietà **trustServerCertificate** è impostata su "true", il driver non convalida il certificato SSL.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.                                                                                                                                                                                          |
| true           | false o blank         | vuoto                 | vuoto      | vuoto              | [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richiede di usare la crittografia SSL con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> La proprietà **serverName** specificata nell'URL di connessione viene usata dal driver per convalidare il certificato SSL del server e le regole di ricerca della factory del gestore di attendibilità vengono usate per determinare l'archivio certificati da usare.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.                                                                             |
| true           | false o blank         | Valore                 | vuoto      | vuoto              | [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richiede di usare la crittografia SSL con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver convalida il valore del soggetto del certificato SSL tramite il valore specificato per la proprietà **hostNameInCertificate**.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.                                                                                                                                                                 |
| true           | false o blank         | vuoto                 | Valore      | Valore              | [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richiede di usare la crittografia SSL con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver usa il valore della proprietà **trustStore** per cercare il file trustStore del certificato e il valore della proprietà **trustStorePassword** per controllare l'integrità del file trustStore.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.                                                                                                                |
| true           | false o blank         | vuoto                 | vuoto      | Valore              | [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richiede di usare la crittografia SSL con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver usa il valore della proprietà **trustStorePassword** per controllare l'integrità del file trustStore predefinito.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.                                                                                                                                                                                  |
| true           | false o blank         | vuoto                 | Valore      | vuoto              | [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richiede di usare la crittografia SSL con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver usa il valore della proprietà **trustStore** per cercare la posizione del file trustStore.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.                                                                                                                                                                                                 |
| true           | false o blank         | Valore                 | vuoto      | Valore              | [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richiede di usare la crittografia SSL con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver usa il valore della proprietà **trustStorePassword** per controllare l'integrità del file trustStore predefinito. Il driver, poi, usa il valore della proprietà **hostNameInCertificate** per convalidare il certificato SSL.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.                                                                   |
| true           | false o blank         | Valore                 | Valore      | vuoto              | [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richiede di usare la crittografia SSL con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver usa il valore della proprietà **trustStore** per cercare la posizione del file trustStore. Il driver, poi, usa il valore della proprietà **hostNameInCertificate** per convalidare il certificato SSL.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata.                                                                                  |
| true           | false o blank         | Valore                 | Valore      | Valore              | [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richiede di usare la crittografia SSL con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Se il server supporta la crittografia o richiede il supporto della crittografia SSL da parte del client, tramite il driver viene avviato lo scambio del certificato SSL.<br /><br /> Il driver usa il valore della proprietà **trustStore** per cercare il file trustStore del certificato e il valore della proprietà **trustStorePassword** per controllare l'integrità del file trustStore. Il driver, poi, usa il valore della proprietà **hostNameInCertificate** per convalidare il certificato SSL.<br /><br /> Se il server non è configurato per supportare la crittografia, verrà generato un errore e la connessione verrà terminata. |
  
Se la proprietà encrypt è impostata su **true**, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] usa il provider di sicurezza JSSE predefinito di JVM per negoziare la crittografia SSL con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile che il provider di sicurezza predefinito non supporti tutte le funzionalità necessarie per negoziare la crittografia SSL. Tale provider può, ad esempio, non supportare la dimensione della chiave pubblica RSA usata nel certificato SSL di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In questo caso, è possibile che venga generato un errore dal provider di sicurezza predefinito, a causa del quale la connessione viene terminata dal driver JDBC. Per risolvere il problema, eseguire una delle operazioni seguenti:  
  
- Configurare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con un certificato del server con una chiave pubblica RSA di dimensione inferiore  
  
- Configurare JVM per l'uso di un provider di sicurezza JSSE diverso nel file delle proprietà di sicurezza "\<java-home>/lib/security/java.security"  
  
- Utilizzare una versione di JVM diversa.  
  
## <a name="validating-server-ssl-certificate"></a>Convalida del certificato SSL del server  

Durante l'handshake SSL, il server invia il proprio certificato chiave pubblica al client. Il driver JDBC o il client deve convalidare che il certificato del server sia stato emesso da un'Autorità di certificazione considerata attendibile dal client. Il driver richiede che il certificato del server soddisfi le condizioni seguenti:  
  
- Il certificato è stato emesso da un'Autorità di certificazione attendibile.  
  
- Il certificato deve essere emesso per l'autenticazione del server.  
  
- Il certificato non è scaduto.  
  
- Il nome comune nell'oggetto o un nome DNS nel nome alternativo del soggetto (SAN, Subject Alternate Name) del certificato corrisponde esattamente al valore **serverName** specificato nella stringa di connessione o, se specificato, al valore della proprietà **hostNameInCertificate**.  
  
- Un nome DNS può includere caratteri jolly. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], tuttavia, non supporta la corrispondenza dei caratteri jolly. In altre parole, abc.com non corrisponderà a \*.com, ma \*.com corrisponderà a \*.com.  
  
## <a name="see-also"></a>Vedere anche

[Uso della crittografia SSL](../../connect/jdbc/using-ssl-encryption.md)

[Protezione delle applicazioni del driver JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
