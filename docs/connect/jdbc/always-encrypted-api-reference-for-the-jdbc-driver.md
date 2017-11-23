---
title: Crittografia sempre attiva di riferimento sulle API per il Driver JDBC | Documenti Microsoft
ms.custom: 
ms.date: 11/10/2016
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7c0d47b3ef5dc4bb01cbc667299902aa283eb039
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Crittografia sempre attiva di riferimento sulle API per il Driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Always Encrypted consente ai client di eseguire la crittografia dei dati sensibili all'interno delle applicazioni client e non rivelare le chiavi di crittografia di SQL Server. Un driver abilitato Always Encrypted installato nel computer client fa tutto questo eseguendo automaticamente la crittografia e la decrittografia dei dati sensibili nell'applicazione client di SQL Server. Il driver esegue la crittografia dei dati in colonne riservate prima di passare i dati a SQL Server e riscrive automaticamente le query in modo da mantenere la semantica per l'applicazione. Analogamente, il driver esegue in modo trasparente la decrittografia dei dati archiviati in colonne crittografate del database contenute nei risultati della query. Per ulteriori informazioni, vedere [Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) e [uso di Always Encrypted con il Driver JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Always Encrypted è supportato solo da Microsoft JDBC Driver 6.0 o versione successiva per SQL Server con SQL Server 2016.  
  
 Esistono diverse nuove funzionalità e modifiche all'API del driver JDBC da utilizzare in applicazioni client che utilizzano Always Encrypted.  
  
 **Classe SQLServerConnection**  
  
|Nome|Descrizione|  
|----------|-----------------|  
|Nuova parola chiave della stringa di connessione:<br /><br /> columnEncryptionSetting|columnEncryptionSetting = Enabled abilita la funzionalità crittografia sempre attiva per la connessione e columnEncryptionSetting = Disabled la disabilita. I valori accettati sono Enabled/Disabled. Il valore predefinito è Disabled.|  
|Nuovi metodi:<br /><br /> pubblica setColumnEncryptionTrustedMasterKeyPaths void statico (mappa < stringa, elenco\<stringa >> trustedKeyPaths)<br /><br /> pubblica updateColumnEncryptionTrustedMasterKeyPaths void statico (elenco di server stringa\<stringa > trustedKeyPaths)<br /><br /> removeColumnEncryptionTrustedMasterKeyPaths void statico pubblico (server stringa)|Consente di aggiornare/set/rimuovere un elenco di percorsi principali attendibili per un server di database. Se durante l'elaborazione di una query dell'applicazione, il driver riceve il percorso di una chiave che non è presente nell'elenco, la query ha esito negativo. Questa proprietà fornisce un’ulteriore protezione da attacchi alla sicurezza in cui un SQL Server compromesso fornisce falsi percorsi chiavi. Questo potrebbe causare la perdita delle credenziali dell’archivio di chiavi.|  
|Nuovo metodo:<br /><br /> Mappa statica pubblica < stringa, elenco\<stringa >> getColumnEncryptionTrustedMasterKeyPaths()|Restituisce un elenco di percorsi attendibili delle chiavi per un server di database.|  
|Nuovo metodo:<br /><br /> pubblica registerColumnEncryptionKeyStoreProviders void statico (mappa\<String, SQLServerColumnEncryptionKeyStoreProvider > clientKeyStoreProviders)|Consente di registrare provider personalizzati per gli archivi delle chiavi. È un dizionario che esegue il mapping dei nomi dei provider degli archivi delle chiavi per le implementazioni del provider dell’archivio delle chiavi.<br /><br /> Per utilizzare l'archivio chiavi JVM è necessario creare un'istanza di un oggetto SQLServerColumnEncryptionJVMKeyStoreProvider con le credenziali keystore di JVM e registrarla con il driver. Il nome per questo provider deve essere 'MSSQL_JVM_KEYSTORE'.<br /><br /> Per usare l'archivio di credenziali chiave di Azure è necessario creare un'istanza di un oggetto SQLServerColumnEncryptionAzureKeyStoreProvider e registrarlo con il driver. Il nome per questo provider deve essere 'AZURE_KEY_VAULT'.|
|pubblica getSendTimeAsDatetime() booleano finale|Restituisce l'impostazione della proprietà di connessione sendTimeAsDatetime.|
|pubblica setSendTimeAsDatetime void (sendTimeAsDateTimeValue booleano)|Modifica l'impostazione della proprietà di connessione sendTimeAsDatetime.|

 **Classe SQLServerConnectionPoolProxy**
|Nome|Description|  
|----------|-----------------|  
|pubblica getSendTimeAsDatetime() booleano finale|Restituisce l'impostazione della proprietà di connessione sendTimeAsDatetime.|
|pubblica setSendTimeAsDatetime void (sendTimeAsDateTimeValue booleano)|Modifica l'impostazione della proprietà di connessione sendTimeAsDatetime.|
     
  
 **Classe SQLServerDataSource**  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica setColumnEncryptionSetting void (stringa columnEncryptionSetting)|Abilita/disabilita la funzionalità Always Encrypted per l'oggetto di origine dati.<br /><br /> Il valore predefinito è Disabled.|  
|pubblica getColumnEncryptionSetting() stringa|Recupera l'impostazione della funzionalità Always Encrypted per l'oggetto di origine dati.|
|pubblica setKeyStoreAuthentication void (stringa keyStoreAuthentication)|Imposta il nome che identifica un archivio chiavi. Solo il valore supportato è "JavaKeyStorePassword" per l'archivio di chiavi di Java identifiying.<br/><br/>Il valore predefinito è Null.|
|pubblica getKeyStoreAuthentication() stringa|Ottiene il valore dell'impostazione keyStoreAuthentication per l'oggetto origine dati.|
|pubblica setKeyStoreSecret void (stringa keyStoreSecret)|Imposta la password per il file keystore Java. Si noti che, per il provider di archivio di chiavi di Java la password per il file keystore e la chiave deve essere lo stesso. Si noti che, keyStoreAuthentication devono essere impostate con "JavaKeyStorePassword".|
|pubblica setKeyStoreLocation void (stringa keyStoreLocation)|Imposta il percorso, incluso il nome del file per il file keystore Java. Si noti che, keyStoreAuthentication devono essere impostate con "JavaKeyStorePassword".|
|pubblica getKeyStoreLocation() stringa|Recupera il keyStoreLocation per l'archivio di chiavi di Java.|
  
 **Classe SQLServerColumnEncryptionJavaKeyStoreProvider**  
  
 L'implementazione del provider dell'archivio chiavi per archivio chiavi di Java. Questa classe consente l'uso dei certificati archiviati nell'archivio Java come chiavi master della colonna.  
  
 Costruttori  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica SQLServerColumnEncryptionJavaKeyStoreProvider (keyStoreLocation String, char [] keyStoreSecret)|Provider dell'archivio chiavi per l'archivio di chiavi di Java.|  
  
 Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica byte [] decryptColumnEncryptionKey (masterKeyPath stringa, stringa encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)|Consente di effettuare la decrittografia del valore crittografato specificato di una column encryption key. Il valore crittografato deve essere crittografato utilizzando il certificato con il percorso della chiave specificato e l'algoritmo specificato.<br /><br /> **Il formato del percorso della chiave deve essere uno dei valori seguenti:**<br /><br /> Thumbprint:<certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (Esegue l'override SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey (String, String, Byte[]).)|  
|pubblica byte [] encryptColumnEncryptionKey (masterKeyPath stringa, stringa encryptionAlgorithm, byte [] plainTextColumnEncryptionKey)|Consente di eseguire la crittografia di una column encryption key utilizzando il certificato con il percorso della chiave specificato e l'algoritmo specificato.<br /><br /> **Il formato del percorso della chiave deve essere uno dei valori seguenti:**<br /><br /> Thumbprint:<certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (Esegue l'override SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey (String, String, Byte[]).)|  
|pubblica setName void (nome della stringa)|Imposta il nome di questo provider dell'archivio chiavi.|
|pubblica stringa getName (.)|Ottiene il nome di questo provider dell'archivio chiavi.|
  
 **Classe SQLServerColumnEncryptionAzureKeyVaultProvider**  
  
 L'implementazione del provider dell'archivio chiavi per insieme credenziali chiavi Azure. Questa classe consente l'utilizzo di chiavi archiviate nell'insieme di credenziali chiave di Azure come chiavi master della colonna.  
  
 Costruttori  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica SQLServerColumnEncryptionAzureKeyVaultProvider (SQLServerKeyVaultAuthenticationCallback authenticationCallback, ExecutorService executorService)|Provider dell'archivio chiavi per insieme credenziali chiavi Azure.  È necessario fornire un'implementazione per l'interfaccia SQLServerKeyVaultAuthenticationCallback recuperare un token di accesso per la chiave nell'insieme di credenziali chiave di Azure.|  
  
 Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica byte [] decryptColumnEncryptionKey (masterKeyPath stringa, stringa encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)|Consente di effettuare la decrittografia del valore crittografato specificato di una column encryption key. Il valore dovrebbe essere crittografato usando la chiave di colonna specificato chiave IDmaster e utilizzando l'algoritmo specificato. <br />(Esegue l'override SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey (String, String, Byte[]).)|  
|pubblica byte [] encryptColumnEncryptionKey (masterKeyPath stringa, stringa encryptionAlgorithm, byte [] columnEncryptionKey)|Crittografa una chiave di crittografia di colonna usando la chiave master di colonna specificato e utilizzando l'algoritmo specificato. <br />(Esegue l'override SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey (String, String, Byte[]).)|  
|pubblica setName void (nome della stringa)|Imposta il nome di questo provider dell'archivio chiavi.|
|pubblica stringa getName (.)|Ottiene il nome di questo provider dell'archivio chiavi.|  
  
  
 **Interfaccia SQLServerKeyVaultAuthenticationCallback**  
  
 Questa interfaccia contiene un metodo per l'autenticazione insieme credenziali chiavi Azure, che deve essere implementata dall'utente.  
  
 Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica getAccessToken stringa (autorità di stringa, risorsa di tipo stringa, ambito stringa);|Il metodo deve essere sottoposto a override. Il metodo viene utilizzato per ottenere token per l'insieme di credenziali di Azure chiave di accesso.|  
  
 **Classe SQLServerColumnEncryptionKeyStoreProvider**  
  
 Estendere questa classe per implementare un provider personalizzato dell’archivio delle chiavi.  
  
|Nome|Description|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|Classe base per tutti i provider degli archivi delle chiavi. Un provider personalizzato deve derivare da questa classe ed eseguire l'override delle relative funzioni membro e quindi registrarlo utilizzando SQLServerConnection. registerColumnEncryptionKeyStoreProviders().|  
  
 Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)|Metodo della classe base per eseguire la decrittografia del valore crittografato specificato di una column encryption key. Il valore crittografato dovrebbe essere crittografato utilizzando la column master key con il percorso della chiave specificato e l'algoritmo specificato.|  
|public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)|Metodo della classe base per eseguire la crittografia di una column encryption key utilizzando la column master key con il percorso della chiave specificato e l'algoritmo specificato.|
|astratta public void setName (nome della stringa)|Imposta il nome di questo provider dell'archivio chiavi.|
|pubblica getName() stringa astratta|Ottiene il nome di questo provider dell'archivio chiavi.|  
  
 Metodi di nuovo o sottoposto a overload in **SQLServerPreparedStatement** classe  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica setBigDecimal void (int parameterIndex, BigDecimal x, int precisione, scala int)<br /><br /> pubblica setObject void (int parameterIndex, oggetto x, int targetSqlType, precisione Integer, scala int)<br /><br /> pubblica setObject void (int parameterIndex, oggetto x, SQLType targetSqlType, precisione Integer, scala Integer)<br /><br /> pubblica setTime void (parameterIndex int, Java.SQL. Time, scala int x)<br /><br /> pubblica setTimestamp void (parameterIndex int, Java.SQL. timestamp, int scala x) <br />pubblica setDateTimeOffset void (int parameterIndex, Microsoft.SQL x, scala int)|Questi metodi sono sottoposti a overload con una precisione di un argomento di scala e/o per supportare Always Encrypted per specifici tipi di dati che richiedono una precisione e informazioni sulla scala.|  
|pubblica setMoney void (int parameterIndex, BigDecimal x)<br /><br /> pubblica setSmallMoney void (int parameterIndex, BigDecimal x)<br /><br /> pubblica setUniqueIdentifier void (int parameterIndex, stringa guid)<br /><br /> pubblica setDateTime void (parameterIndex int, Java.SQL. timestamp x)<br /><br /> pubblica setSmallDateTime void (parameterIndex int, Java.SQL. timestamp x)|Questi metodi vengono aggiunti per supportare Always Encrypted per money di tipi di dati, smallmoney, uniqueidentifier, datetime e smalldatetime. <br/><br/>Si noti che il metodo setTimestamp() esistente viene utilizzato per l'invio di valori dei parametri per la colonna crittografata datetime2. Per ora crittografati e le colonne smalldatetime utilizzare rispettivamente i nuovi metodi setDateTime() e setSmallDateTime().|  
|pubblica setBigDecimal void finale (int parameterIndex, BigDecimal x, int precisione, scala int, boolean forceEncrypt)<br /><br /> finale public void setMoney (int parameterIndex, BigDecimal x, forceEncrypt booleano)<br /><br /> finale public void setSmallMoney (int parameterIndex, BigDecimal x, forceEncrypt booleano)<br /><br /> pubblica setBoolean void finale (parameterIndex int, boolean x, forceEncrypt booleano)<br /><br /> pubblica setByte void finale (parameterIndex int, byte 0x, forceEncrypt booleano)<br /><br /> pubblica setBytes void finale (parameterIndex int, byte x[], forceEncrypt booleano)<br /><br /> pubblica setUniqueIdentifier void finale (int parameterIndex, stringa guid, boolean forceEncrypt)<br /><br /> pubblica setDouble void finale (parameterIndex int, double x, forceEncrypt booleano)<br /><br /> pubblica setFloat void finale (parameterIndex int, float, x, forceEncrypt booleano)<br /><br /> pubblica setInt void finale (int parameterIndex, il valore int, boolean forceEncrypt)<br /><br /> pubblica setLong void finale (parameterIndex int, long x, forceEncrypt booleano)<br /><br /> pubblica setObject finale (int parameterIndex, oggetto x targetSqlType int, Integer mobile e precisione scala int, boolean forceEncrypt)<br /><br /> pubblica setObject void finale (int parameterIndex, oggetto x SQLType targetSqlType, intero mobile e precisione scala Integer, boolean forceEncrypt)<br /><br /> pubblica setShort void finale (parameterIndex int, short x, forceEncrypt booleano)<br /><br /> finale public void setString (int parameterIndex, str String, boolean forceEncrypt)<br /><br /> pubblica setNString void finale (int parameterIndex, il valore di stringa, booleano forceEncrypt)<br /><br /> pubblica setTime void finale (parameterIndex int, Java.SQL. time x, scala int, boolean forceEncrypt)<br /><br /> pubblica setTimestamp void finale (parameterIndex int, Java.SQL. timestamp, int scala, x forceEncrypt booleano)<br /><br /> pubblica setDateTimeOffset void finale (int parameterIndex, Microsoft.SQL x, scala int, boolean forceEncrypt)<br /><br /> pubblica setDateTime void finale (parameterIndex int, Java.SQL. timestamp x, forceEncrypt booleano)<br /><br /> pubblica setSmallDateTime void finale (parameterIndex int, Java.SQL. timestamp x, forceEncrypt booleano)<br /><br /> pubblica setDate void finale (parameterIndex int, Java.SQL. date x, cal java.util.Calendar, forceEncrypt booleano)<br /><br /> pubblica setTime void finale (parameterIndex int, Java.SQL. time x, cal java.util.Calendar, forceEncrypt booleano)<br /><br /> pubblica setTimestamp void finale (parameterIndex int, Java.SQL. timestamp x, cal java.util.Calendar, forceEncrypt booleano)|Imposta il parametro designato sul valore java specificato.<br /><br /> Se il forceEncrypt booleano è impostato su true, la query parametro verrà impostato solo se la definizione di colonna è crittografata e Always Encrypted è abilitato per la connessione o per l'istruzione.<br /><br /> Se il forceEncrypt booleano è impostato su false, il driver non forza la crittografia sui parametri.|  
  
 Metodi di nuovo o sottoposto a overload in **SQLServerCallableStatement** classe  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica registerOutParameter void (int parameterIndex sqlType int, int precisione, scala int)<br /><br /> pubblica registerOutParameter void (int parameterIndex SQLType sqlType, int precisione, scala int)<br /><br /> pubblica registerOutParameter void (stringa parameterName sqlType int, int precisione, scala int)<br /><br /> pubblica registerOutParameter void (stringa parameterName SQLType sqlType, int precisione, scala int)<br />pubblica setBigDecimal void (stringa parameterName, BigDecimal bd, int precisione, scala int)<br /><br /> pubblica setTime void (stringa parameterName, t Java.SQL. Time, scala int)<br /><br /> pubblica setTimestamp void (stringa parameterName, t Java.SQL. timestamp, int scala)<br /><br /> pubblica setDateTimeOffset void (stringa parameterName, Microsoft.SQL t, scala int)<br/><br/>pubblica setObject void finale (int targetSqlType sCol stringa, oggetto x, precisione Integer, scala int)|Questi metodi sono sottoposti a overload con una precisione di un argomento di scala e/o per supportare Always Encrypted per specifici tipi di dati che richiedono una precisione e informazioni sulla scala.|  
|pubblica setDateTime void (parameterName String, Java.SQL. timestamp x)<br /><br /> pubblica setSmallDateTime void (parameterName String, Java.SQL. timestamp x)<br /><br /> pubblica setUniqueIdentifier void (parameterName stringa, stringa guid)<br /><br /> pubblica setMoney void (stringa parameterName, bd BigDecimal)<br /><br /> pubblica setSmallMoney void (stringa parameterName, bd BigDecimal)<br/><br/>pubblica Timestamp getDateTime (int index)<br/><br/>pubblica Timestamp getDateTime (stringa sCol)<br/><br/>pubblica getDateTime Timestamp (indice int, calendario cal)<br/><br/>pubblica Timestamp getSmallDateTime (int index)<br/><br/>pubblica Timestamp getSmallDateTime (stringa sCol)<br/><br/>pubblica getSmallDateTime Timestamp (indice int, calendario cal)<br/><br/>pubblica getSmallDateTime Timestamp (nome della stringa, calendario cal)<br/><br/>pubblica BigDecimal getMoney (int index)<br/><br/>pubblica BigDecimal getMoney (stringa sCol)<br/><br/>pubblica BigDecimal getSmallMoney (int index)<br/><br/>pubblica BigDecimal getSmallMoney (stringa sCol)|Questi metodi vengono aggiunti per supportare Always Encrypted per money di tipi di dati, smallmoney, uniqueidentifier, datetime e smalldatetime. <br/><br/>Si noti che il metodo setTimestamp() esistente viene utilizzato per l'invio di valori dei parametri per la colonna crittografata datetime2. Per ora crittografati e le colonne smalldatetime utilizzare rispettivamente i nuovi metodi setDateTime() e setSmallDateTime().|  
|pubblica setObject void (parameterName stringa, oggetto o, n int, int m, forceEncrypt booleano)<br /><br /> pubblica setObject void (parameterName stringa, oggetto obj, SQLType jdbcType, scala int, boolean forceEncrypt)<br /><br /> pubblica setDate void (parameterName String, Java.SQL. date x, calendario c, forceEncrypt booleano)<br /><br /> pubblica setTime void (parameterName stringa, t Java.SQL. Time, scala int, boolean forceEncrypt)<br /><br /> pubblica setTime void (parameterName String, Java.SQL. time x, calendario c, forceEncrypt booleano)<br /><br /> pubblica setDateTime void (parameterName String, Java.SQL. timestamp x, forceEncrypt booleano)<br /><br /> pubblica setDateTimeOffset void (stringa parameterName, Microsoft.SQL t, scala int, boolean forceEncrypt)<br /><br /> pubblica setSmallDateTime void (parameterName String, Java.SQL. timestamp x, forceEncrypt booleano)<br /><br /> pubblica setTimestamp void (stringa parameterName, t Java.SQL. timestamp, scala int, boolean forceEncrypt)<br /><br /> pubblica setTimestamp void (parameterName String, Java.SQL. timestamp x, forceEncrypt booleano)<br /><br /> pubblica setUniqueIdentifier void (parameterName stringa, stringa guid, boolean forceEncrypt)<br /><br /> pubblica setBytes void (byte [] b parameterName stringa, booleano forceEncrypt)<br /><br /> pubblica setByte void (stringa parameterName, byte b, forceEncrypt booleano)<br /><br /> pubblica setString void (parameterName stringa, valori String, boolean forceEncrypt)<br /><br /> pubblica setNString void finale (parameterName stringa, il valore di stringa, booleano forceEncrypt)<br /><br /> pubblica setMoney void (BigDecimal bd parameterName stringa, booleano forceEncrypt)<br /><br /> pubblica setSmallMoney void (BigDecimal bd parameterName stringa, booleano forceEncrypt)<br /><br /> pubblica setBigDecimal void (stringa parameterName BigDecimal bd, int mobile e precisione, scala int forceEncrypt booleano)<br /><br /> pubblica setDouble void (parameterName stringa, double d, forceEncrypt booleano)<br /><br /> pubblica setFloat void (stringa parameterName, float, f, forceEncrypt booleano)<br /><br /> pubblica setInt void (parameterName String, int i, forceEncrypt booleano)<br /><br /> pubblica setLong void (prolungata l parameterName stringa, booleano forceEncrypt)<br /><br /> pubblica setShort void (stringa parameterName, breve s, forceEncrypt booleano)<br /><br /> pubblica setBoolean void (parameterNames stringa, booleano b, forceEncrypt booleano)<br/><br/>pubblica setTimeStamp void (sCol String, Java.SQL. timestamp x, calendario c, forceEncrypt booleano)|Imposta il parametro designato sul valore java specificato.<br /><br /> Se il forceEncrypt booleano è impostato su true, la query parametro verrà impostato solo se la definizione di colonna è crittografata e Always Encrypted è abilitato per la connessione o per l'istruzione.<br /><br /> Se il forceEncrypt booleano è impostato su false, il driver non forza la crittografia sui parametri.|
 

 Metodi di nuovo o sottoposto a overload in **SQLServerResultSet** classe  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica stringa getUniqueIdentifier (int columnIndex)<br/><br/>pubblica stringa getUniqueIdentifier (stringa columnLabel)<br/><br/>   pubblica Java.SQL. timestamp getDateTime (int columnIndex) <br/><br/> pubblica Java.SQL. timestamp getDateTime (columnName stringa)   <br/><br/> pubblica Java.SQL. timestamp getDateTime (int columnIndex, calendario cal)   <br/><br/>pubblica Java.SQL. timestamp getDateTime (stringa colName, calendario cal)    <br/><br/>pubblica Java.SQL. timestamp getSmallDateTime (int columnIndex)    <br/><br/> pubblica Java.SQL. timestamp getSmallDateTime (columnName stringa)   <br/><br/> pubblica Java.SQL. timestamp getSmallDateTime (int columnIndex, calendario cal)   <br/><br/> pubblica Java.SQL. timestamp getSmallDateTime (stringa colName, calendario cal)   <br/><br/>  pubblica BigDecimal getMoney (int columnIndex)  <br/><br/> pubblica BigDecimal getMoney (columnName stringa)   <br/><br/> pubblica BigDecimal getSmallMoney (int columnIndex)   <br/><br/>  pubblica BigDecimal getSmallMoney (columnName stringa)  <br/><br/>pubblica updateMoney void (stringa columnName, BigDecimal x)    <br/><br/>  pubblica updateSmallMoney void (stringa columnName, BigDecimal x)  <br/><br/>     pubblica updateDateTime void (indice int, Java.SQL. timestamp x) <br/><br/> pubblica updateSmallDateTime void (indice int, Java.SQL. timestamp x) |Questi metodi vengono aggiunti per supportare Always Encrypted per money di tipi di dati, smallmoney, uniqueidentifier, datetime e smalldatetime. <br/><br/>Si noti che il metodo updateTimestamp() esistente viene utilizzato per aggiornare le colonne crittografate datetime2. Per ora crittografati e le colonne smalldatetime utilizzare rispettivamente i nuovi metodi updateDateTime() e updateSmallDateTime().|
|pubblica updateBoolean void (indice int, boolean x, forceEncrypt booleano)  <br/><br/>  pubblica updateByte void (indice int, byte 0x, forceEncrypt booleano)  <br/><br/>  pubblica updateShort void (indice int, short x, forceEncrypt booleano)  <br/><br/> pubblica updateInt void (indice int, int x, forceEncrypt booleano)   <br/><br/>  pubblica updateLong void (indice int, long x, forceEncrypt booleano)  <br/><br/> pubblica updateFloat void (indice int, float, x, forceEncrypt booleano)   <br/><br/> pubblica updateDouble void (indice int, double x, forceEncrypt booleano)   <br/><br/> pubblica updateMoney void (int index, BigDecimal x, forceEncrypt booleano)   <br/><br/>  pubblica updateMoney void (stringa columnName, BigDecimal x, forceEncrypt booleano)  <br/><br/> pubblica updateSmallMoney void (int index, BigDecimal x, forceEncrypt booleano)   <br/><br/>  pubblica updateSmallMoney void (stringa columnName, BigDecimal x, forceEncrypt booleano)  <br/><br/> pubblica updateBigDecimal void (int index, BigDecimal x, precisione Integer, la scala di Integer, boolean forceEncrypt)   <br/><br/>  pubblica updateString void (int columnIndex, stringValue stringa, booleano forceEncrypt)  <br/><br/>  pubblica updateNString void (int columnIndex, nString stringa, booleano forceEncrypt)  <br/><br/>  pubblica updateNString void (stringa columnLabel, nString stringa, booleano forceEncrypt)  <br/><br/> pubblica updateBytes void (indice int, byte x[], forceEncrypt booleano)   <br/><br/>  pubblica updateDate void (indice int, Java.SQL. date x, forceEncrypt booleano)  <br/><br/> pubblica updateTime void (indice int, Java.SQL. time x, la scala di Integer, boolean forceEncrypt)   <br/><br/> pubblica updateTimestamp void (indice int, Java.SQL. timestamp, int scala, x forceEncrypt booleano)   <br/><br/> pubblica updateDateTime void (indice int, Java.SQL. timestamp x, la scala di Integer, boolean forceEncrypt)   <br/><br/> pubblica updateSmallDateTime void (indice int, Java.SQL. timestamp x, la scala di Integer, boolean forceEncrypt)   <br/><br/>  pubblica updateDateTimeOffset void (int index, Microsoft.SQL x, la scala di Integer, boolean forceEncrypt)  <br/><br/> pubblica updateUniqueIdentifier void (int index, stringa x, forceEncrypt booleano)    <br/><br/>  pubblica updateObject void (int index, oggetto x, int precisione, scala int, boolean forceEncrypt)  <br/><br/>  pubblica updateObject void (int indice, oggetto obj, SQLType targetSqlType, scala int, boolean forceEncrypt)  <br/><br/> pubblica updateBoolean void (columnName stringa, booleano x, forceEncrypt booleano)    <br/><br/>  pubblica updateByte void (columnName String, byte x, forceEncrypt booleano)  <br/><br/>  pubblica updateShort void (x breve stringa columnName, forceEncrypt booleano)  <br/><br/> pubblica updateInt void (columnName String, int x, forceEncrypt booleano)   <br/><br/>   pubblica updateLong void (columnName String, long x, forceEncrypt booleano) <br/><br/>  pubblica updateFloat void (stringa columnName, float, x, forceEncrypt booleano)  <br/><br/>  pubblica updateDouble void (columnName stringa, double x, forceEncrypt booleano)  <br/><br/> pubblica updateBigDecimal void (stringa columnName, BigDecimal x, forceEncrypt booleano)   <br/><br/>  pubblica updateBigDecimal void (stringa columnName, BigDecimal x, precisione Integer, la scala di Integer, boolean forceEncrypt)  <br/><br/> pubblica updateString void (columnName stringa, stringa x, forceEncrypt booleano)   <br/><br/>  pubblica updateBytes void (stringa columnName, x[] byte, boolean forceEncrypt)  <br/><br/> pubblica updateDate void (columnName String, Java.SQL. date x, forceEncrypt booleano)   <br/><br/>  pubblica updateTime void (columnName String, Java.SQL. time x, scala int, boolean forceEncrypt)  <br/><br/>  pubblica updateTimestamp void (columnName String, Java.SQL. timestamp, int scala, x forceEncrypt booleano)  <br/><br/> pubblica updateDateTime void (columnName String, Java.SQL. timestamp, int scala, x forceEncrypt booleano)   <br/><br/>  pubblica updateSmallDateTime void (columnName String, Java.SQL. timestamp, int scala, x forceEncrypt booleano)  <br/><br/>  pubblica updateDateTimeOffset void (stringa columnName, Microsoft.SQL x, scala int, boolean forceEncrypt)  <br/><br/>  pubblica updateUniqueIdentifier void (columnName stringa, stringa x, forceEncrypt booleano)<br/><br/>pubblica updateObject void (columnName stringa, oggetto x, int precisione, scala int, boolean forceEncrypt)<br/><br/>pubblica updateObject void (columnName stringa, oggetto obj, SQLType targetSqlType, scala int, boolean forceEncrypt)|Aggiornare la colonna designata sul valore java specificato.<br/><br/>Se il forceEncrypt booleano è impostato su true, la colonna verrà impostata solo se è crittografata e Always Encrypted è abilitato per la connessione o per l'istruzione.<br/><br/>Se il forceEncrypt booleano è impostato su false, il driver non forza la crittografia sui parametri.|

  
Nuovi tipi in **microsoft.sql.Types** classe
|Nome|Description|  
|----------|-----------------|  
|DATETIME, SMALLDATETIME, MONEY, SMALLMONEY, GUID|Utilizzare questi tipi come tipi SQL di destinazione per l'invio di valori dei parametri **crittografati** datetime, smalldatetime, money, smallmoney, utilizzando i metodi API setObject()/updateObject() delle colonne di tipo uniqueidentifier.|  
  
  
 **Enumerazione SQLServerStatementColumnEncryptionSetting**  
  
 Specifica la modalità cui dati verranno inviati e ricevuti durante la lettura e scrittura delle colonne crittografate. A seconda della query specifica, l'impatto sulle prestazioni può essere ridotto ignorando l'elaborazione del driver sempre crittografato quando vengono utilizzate colonne non crittografate. Tenere presente queste impostazioni non possono essere utilizzate per ignorare la crittografia e ottenere l'accesso ai dati di testo normale.  
  
 **Sintassi**  
  
```  
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **Membri**  
  
|Nome|Description|  
|----------|-----------------|  
|UseConnectionSetting|Specifica che il comando deve essere predefinito per l'impostazione sempre crittografato nella stringa di connessione.|  
|Abilitata|Abilita sempre crittografato per la query.|  
|ResultSetOnly|Specifica che solo i risultati del comando devono essere elaborati in base alla routine sempre crittografato nel driver. Utilizzare questo valore quando il comando non dispone di parametri che richiedono la crittografia.|  
|Disabilitata|Disabilita sempre crittografato per la query.|  
  
 Impostazione del livello di istruzione per AE vengono aggiunti alla classe SQLServerConnection e alla classe SQLServerConnectionPoolProxy. I metodi seguenti in queste classi sono sottoposti a overload con la nuova impostazione.  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica createStatement istruzione (int NLE nConcur int, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Crea un oggetto istruzione che genera gli oggetti ResultSet con l'impostazione di crittografia di tipo, di concorrenza, di trattenibilità e di colonna specificato.|  
|pubblica prepareCall CallableStatement (stringa sql NLE int, int nConcur, statementHoldability int, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)|Crea un oggetto CallableStatement con l'impostazione di crittografia di colonna specificata che genera gli oggetti ResultSet con il tipo specificato, concorrenza e trattenibilità.|  
|pubblica prepareStatement PreparedStatement (sql String, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Crea un oggetto PreparedStatement con l'impostazione di crittografia di colonna specificata che ha la possibilità di recuperare le chiavi generate automaticamente.|  
|pubblica prepareStatement PreparedStatement (stringa sql, String [] columnNames, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Crea un oggetto PreparedStatement con l'impostazione di crittografia di colonna specificata che genera gli oggetti ResultSet con i nomi di colonna specificato.|  
|pubblica prepareStatement PreparedStatement (sql String, int [] columnIndexes, SQLServerStatementColumnEncryptionSetting stmtColEncSetting|Crea un oggetto PreparedStatement con l'impostazione di crittografia di colonna specificata che genera gli oggetti ResultSet con gli indici di colonna specificato.|  
|pubblica prepareStatement PreparedStatement (stringa sql NLE int, int nConcur, nHold int, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Crea un oggetto PreparedStatement con l'impostazione di crittografia di colonna specificata che genera gli oggetti ResultSet con il tipo specificato, concorrenza e trattenibilità.|  
  
> [!NOTE]  
>  Se Always Encrypted è disabilitato per una query e la query contiene parametri che devono essere crittografati (parametri che corrispondono a colonne crittografate), la query avrà esito negativo.  
>   
>  Se Always Encrypted è disabilitato per una query e la query restituisce risultati dalle colonne crittografate, la query restituirà i valori crittografati. I valori crittografati avranno il tipo di dati varbinary.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di Always Encrypted con il JDBC Driver](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  
  
