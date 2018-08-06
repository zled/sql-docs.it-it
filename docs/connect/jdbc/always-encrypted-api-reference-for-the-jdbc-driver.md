---
title: Informazioni di riferimento sull'API Always Encrypted per il driver JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1b720a607b702e93643d70b40a5e6ab036f2f56
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279252"
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Informazioni di riferimento sull'API Always Encrypted per il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Always Encrypted consente ai client di eseguire la crittografia dei dati sensibili all'interno delle applicazioni client e non rivelare le chiavi di crittografia di SQL Server. Un driver abilitato Always Encrypted installato nel computer client usa questa funzionalità eseguendo automaticamente la crittografia e la decrittografia dei dati sensibili nell'applicazione client di SQL Server. Il driver esegue la crittografia dei dati in colonne riservate prima di passare i dati a SQL Server e riscrive automaticamente le query in modo da mantenere la semantica per l'applicazione. Analogamente, il driver esegue in modo trasparente la decrittografia dei dati archiviati in colonne crittografate del database presenti nei risultati della query. Per altre informazioni, vedere [Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) e [utilizzo di Always Encrypted con il Driver JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Always Encrypted è supportato solo da Microsoft JDBC Driver 6.0 o versione successiva per SQL Server con SQL Server 2016.  
  
 ## <a name="always-encrypted-api-references"></a>Riferimento all'API di Always Encrypted
 
 Esistono diverse nuove funzionalità e modifiche all'API del driver JDBC da utilizzare in applicazioni client che utilizzano Always Encrypted.  
  
 **Classe SQLServerConnection**  
  
|nome|Descrizione|  
|----------|-----------------|  
|Nuova parola chiave della stringa di connessione:<br /><br /> columnEncryptionSetting|columnEncryptionSetting=Enabled abilita la funzionalità Always Encrypted per la connessione e columnEncryptionSetting=Disabled la disabilita. I valori accettati sono Enabled/Disabled. Il valore predefinito è Disabled.|  
|Nuovi metodi:<br /><br /> setColumnEncryptionTrustedMasterKeyPaths void statico pubblico (mappa < stringa ed elencazione\<stringa >> trustedKeyPaths)<br /><br /> updateColumnEncryptionTrustedMasterKeyPaths void statico pubblico (elenco di server stringa\<stringa > trustedKeyPaths)<br /><br /> static public void removeColumnEncryptionTrustedMasterKeyPaths (server stringa)|Consente di impostare, aggiornare o rimuovere un elenco di percorsi principali attendibili per un server di database. Se durante l'elaborazione di una query dell'applicazione, il driver riceve il percorso di una chiave che non è presente nell'elenco, la query ha esito negativo. Questa proprietà garantisce una maggiore protezione da attacchi alla sicurezza in cui un'istanza compromessa di SQL Server invia falsi percorsi delle chiavi, causando potenzialmente la perdita delle credenziali dell'archivio di chiavi.|  
|Nuovo metodo:<br /><br /> public static Map<String, List\<String>> getColumnEncryptionTrustedMasterKeyPaths()|Restituisce un elenco di percorsi attendibili delle chiavi per un server di database.|  
|Nuovo metodo:<br /><br /> public static void registerColumnEncryptionKeyStoreProviders (Map\<String, SQLServerColumnEncryptionKeyStoreProvider> clientKeyStoreProviders)|Consente di registrare provider personalizzati per gli archivi delle chiavi. È un dizionario che esegue il mapping dei nomi dei provider degli archivi delle chiavi per le implementazioni del provider dell'archivio delle chiavi.<br /><br /> Per usare l'archivio chiavi JVM è necessario creare un'istanza di un oggetto SQLServerColumnEncryptionJVMKeyStoreProvider con le credenziali keystore di JVM e registrarla con il driver. Il nome per questo provider deve essere MSSQL_JVM_KEYSTORE.<br /><br /> Per usare l'archivio di Azure Key Vault, è necessario creare un'istanza di un oggetto SQLServerColumnEncryptionAzureKeyStoreProvider e registrarlo con il driver. Il nome per questo provider deve essere 'AZURE_KEY_VAULT'.|
|public final boolean getSendTimeAsDatetime()|Restituisce l'impostazione della proprietà di connessione sendTimeAsDatetime.|
|public void setSendTimeAsDatetime (sendTimeAsDateTimeValue booleano)|Modifica l'impostazione della proprietà di connessione sendTimeAsDatetime.|

 **Classe SQLServerConnectionPoolProxy**
|nome|Descrizione|  
|----------|-----------------|  
|public final boolean getSendTimeAsDatetime()|Restituisce l'impostazione della proprietà di connessione sendTimeAsDatetime.|
|public void setSendTimeAsDatetime (sendTimeAsDateTimeValue booleano)|Modifica l'impostazione della proprietà di connessione sendTimeAsDatetime.|
     
  
 **Classe SQLServerDataSource**  
  
|nome|Descrizione|  
|----------|-----------------|  
|public void setColumnEncryptionSetting(String columnEncryptionSetting)|Abilita/disabilita la funzionalità Always Encrypted per l'oggetto di origine dati.<br /><br /> Il valore predefinito è Disabled.|  
|pubblica getColumnEncryptionSetting() stringa|Recupera l'impostazione della funzionalità Always Encrypted per l'oggetto di origine dati.|
|public void setKeyStoreAuthentication (stringa keyStoreAuthentication)|Imposta il nome che identifica un archivio chiavi. Unico valore supportato è il **JavaKeyStorePassword** per identificare la Store chiave Java.<br/><br/>Il valore predefinito è Null.|
|pubblica getKeyStoreAuthentication() stringa|Ottiene il valore dell'impostazione keyStoreAuthentication per l'oggetto origine dati.|
|public void setKeyStoreSecret (stringa keyStoreSecret)|Imposta la password dell'archivio chiavi Java. La password per l'archivio chiavi e la chiave deve essere lo stesso. Si noti che keyStoreAuthentication deve essere impostata con **JavaKeyStorePassword**.|
|public void setKeyStoreLocation (stringa keyStoreLocation)|Imposta il percorso, incluso il nome del file dell'archivio chiavi Java. Si noti che keyStoreAuthentication deve essere impostata con **JavaKeyStorePassword**.|
|pubblica getKeyStoreLocation() stringa|Recupera il keyStoreLocation per Store la chiave di Java.|
  
 **Classe SQLServerColumnEncryptionJavaKeyStoreProvider**  
  
 Implementazione del provider dell'archivio chiavi per l'archivio chiavi Java. Questa classe consente l'utilizzo di certificati archiviati nell'archivio chiavi Java come chiavi master della colonna.  
  
 Costruttori  
  
|nome|Descrizione|  
|----------|-----------------|  
|pubblica SQLServerColumnEncryptionJavaKeyStoreProvider (keyStoreLocation String, char [] keyStoreSecret)|Provider dell'archivio chiavi per la Store chiave Java.|  
  
 Metodi  
  
|nome|Descrizione|  
|----------|-----------------|  
|public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)|Consente di effettuare la decrittografia del valore crittografato specificato di una column encryption key. Il valore crittografato deve essere crittografato utilizzando il certificato con il percorso della chiave specificato e l'algoritmo specificato.<br /><br /> **Il formato del percorso della chiave deve essere uno dei seguenti:**<br /><br /> Thumbprint:<certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (Sostituisce SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey (String, String, Byte[]).)|  
|public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)|Consente di eseguire la crittografia di una column encryption key utilizzando il certificato con il percorso della chiave specificato e l'algoritmo specificato.<br /><br /> **Il formato del percorso della chiave deve essere uno dei seguenti:**<br /><br /> Thumbprint:<certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (Sostituisce SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey (String, String, Byte[]).)|  
|public void setName (nome della stringa)|Imposta il nome di questo provider dell'archivio chiavi.|
|public String getName ()|Ottiene il nome di questo provider dell'archivio chiavi.|
  
 **Classe SQLServerColumnEncryptionAzureKeyVaultProvider**  
  
 Implementazione del provider dell'archivio chiavi per Azure Key Vault. Questa classe consente di usare le chiavi archiviate in Azure Key Vault come chiavi master della colonna.  
  
 Costruttori  
  
|nome|Descrizione|  
|----------|-----------------|  
|pubblica SQLServerColumnEncryptionAzureKeyVaultProvider (clientId stringa, stringa clientKey)|Provider dell'archivio chiavi per Azure Key Vault.  È necessario specificare l'identificatore e la chiave del client richiede il token per l'autenticazione ad Azure Key Vault.|  
  
 Metodi  
  
|nome|Descrizione|  
|----------|-----------------|  
|public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)|Consente di effettuare la decrittografia del valore crittografato specificato di una column encryption key. Il valore crittografato deve essere crittografato usando la chiave IDmaster della chiave della colonna e l'algoritmo specificato. <br />(Sostituisce SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey (String, String, Byte[]).)|  
|public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] columnEncryptionKey)|Crittografa una chiave di crittografia di colonna usando la chiave master della colonna specificata e utilizzando l'algoritmo specificato. <br />(Sostituisce SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey (String, String, Byte[]).)|  
|public void setName (nome della stringa)|Imposta il nome di questo provider dell'archivio chiavi.|
|public String getName ()|Ottiene il nome di questo provider dell'archivio chiavi.|  
  
  
 **Interfaccia SQLServerKeyVaultAuthenticationCallback**  
  
 Questa interfaccia contiene un metodo per l'autenticazione di Azure Key Vault, che deve essere implementata dall'utente.  
  
 Metodi  
  
|nome|Descrizione|  
|----------|-----------------|  
|pubblica stringa il parametro getAccessToken (autorità di stringa, risorsa di tipo stringa, stringa ambito);|Il metodo deve essere sottoposto a override. Il metodo viene usato per ottenere l'accesso token da Azure Key Vault.|  
  
 **Classe SQLServerColumnEncryptionKeyStoreProvider**  
  
 Estendere questa classe per implementare un provider personalizzato dell’archivio delle chiavi.  
  
|nome|Descrizione|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|Classe base per tutti i provider degli archivi delle chiavi. Un provider personalizzato deve derivare da questa classe ed eseguire l'override delle relative funzioni membro e quindi registrarlo usando SQLServerConnection. registerColumnEncryptionKeyStoreProviders().|  
  
 Metodi  
  
|nome|Descrizione|  
|----------|-----------------|  
|public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)|Metodo della classe base per eseguire la decrittografia del valore crittografato specificato di una column encryption key. Il valore crittografato dovrebbe essere crittografato utilizzando la chiave master della colonna con il percorso della chiave specificato e l'algoritmo specificato.|  
|public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)|Metodo della classe base per eseguire la crittografia di una column encryption key utilizzando la column master key con il percorso della chiave specificato e l'algoritmo specificato.|
|abstract public void setName (nome della stringa)|Imposta il nome di questo provider dell'archivio chiavi.|
|pubblica getName() stringa astratta|Ottiene il nome di questo provider dell'archivio chiavi.|  
  
 I metodi di nuovo o sottoposto a overload in **SQLServerPreparedStatement** classe  
  
|nome|Descrizione|  
|----------|-----------------|  
|public void setBigDecimal (parametro parameterIndex int, BigDecimal x, int precisione, scala int)<br /><br /> public void setObject (int parametro parameterIndex, x dell'oggetto, targetSqlType int, precisione di Integer, la scala di int)<br /><br /> public void setObject (int parametro parameterIndex, x dell'oggetto, SQLType targetSqlType, precisione di Integer, Integer scala)<br /><br /> public void setTime (parametro parameterIndex int, Java, scala int x)<br /><br /> public void setTimestamp (parametro parameterIndex int, Java, scala int x) <br />public void setDateTimeOffset (parametro parameterIndex int, int scala x, DateTimeOffset)|Questi metodi sono sottoposti a overload con una precisione o un argomento di scala o entrambi per il supporto di Always Encrypted per i tipi di dati specifici che richiedono la precisione e informazioni sulla scala.|  
|pubblica setMoney void (parametro parameterIndex int, BigDecimal x)<br /><br /> pubblica setSmallMoney void (parametro parameterIndex int, BigDecimal x)<br /><br /> pubblica setUniqueIdentifier void (parametro parameterIndex int, stringa guid)<br /><br /> public void setDateTime (parametro parameterIndex int, Java x)<br /><br /> pubblica setSmallDateTime void (parametro parameterIndex int, Java x)|Questi metodi vengono aggiunti per supportare la crittografia sempre attiva per il denaro di tipi di dati, smallmoney, uniqueidentifier, datetime e smalldatetime. <br/><br/>Si noti che il metodo setTimestamp() esistente viene utilizzato per l'invio di valori dei parametri per la colonna crittografata datetime2. Per data e ora crittografati e le colonne smalldatetime utilizzare rispettivamente i nuovi metodi setDateTime() e setSmallDateTime().|  
|pubblica setBigDecimal void finale (parametro parameterIndex int, BigDecimal x, int precisione, scala int, boolean forceEncrypt)<br /><br /> pubblica setMoney void finale (int parametro parameterIndex, x, booleano forceEncrypt BigDecimal)<br /><br /> pubblica setSmallMoney void finale (int parametro parameterIndex, x, booleano forceEncrypt BigDecimal)<br /><br /> pubblica setBoolean void finale (parametro parameterIndex int, boolean x, forceEncrypt booleano)<br /><br /> pubblica setByte void finale (parametro parameterIndex int, byte x, forceEncrypt booleano)<br /><br /> pubblica setBytes void finale (parametro parameterIndex int, byte x[], forceEncrypt booleano)<br /><br /> pubblica setUniqueIdentifier void finale (parametro parameterIndex int, stringa guid, forceEncrypt booleano)<br /><br /> pubblica setDouble void finale (parametro parameterIndex int, double x, forceEncrypt booleano)<br /><br /> pubblica setFloat void finale (parametro parameterIndex int, float x, forceEncrypt booleano)<br /><br /> pubblica setInt void finale (parametro parameterIndex int, valore int, boolean forceEncrypt)<br /><br /> pubblica setLong void finale (parametro parameterIndex int, long x, forceEncrypt booleano)<br /><br /> pubblica finale setObject (int parametro parameterIndex, x dell'oggetto targetSqlType int, valore Integer mobile e precisione scala int, boolean forceEncrypt)<br /><br /> pubblica setObject void finale (parametro parameterIndex int, x dell'oggetto, SQLType targetSqlType, precisione di Integer, scalabilità Integer, booleano forceEncrypt)<br /><br /> pubblica setShort void finale (parametro parameterIndex int, short x, forceEncrypt booleano)<br /><br /> finale public void setString (int parametro parameterIndex, str String, boolean forceEncrypt)<br /><br /> pubblica setNString void finale (parametro parameterIndex int, valore della stringa, booleano forceEncrypt)<br /><br /> pubblica setTime void finale (parametro parameterIndex int, Java, scala int, x forceEncrypt booleano)<br /><br /> pubblica setTimestamp void finale (parametro parameterIndex int, Java, scala int, x forceEncrypt booleano)<br /><br /> pubblica setDateTimeOffset void finale (parametro parameterIndex int, DateTimeOffset x, int scala, forceEncrypt booleano)<br /><br /> pubblica setDateTime void finale (parametro parameterIndex int, Java, x, forceEncrypt booleano)<br /><br /> pubblica setSmallDateTime void finale (parametro parameterIndex int, Java, x, forceEncrypt booleano)<br /><br /> pubblica setDate void finale (parametro parameterIndex int, java.sql.Date x, java.util.Calendar cal, forceEncrypt booleano)<br /><br /> pubblica setTime void finale (parametro parameterIndex int, Java, x, java.util.Calendar cal, forceEncrypt booleano)<br /><br /> pubblica setTimestamp void finale (parametro parameterIndex int, Java, x, java.util.Calendar cal, forceEncrypt booleano)|Imposta il parametro designato sul valore Java specificato.<br /><br /> Se il forceEncrypt booleana è impostata su true, la query parametro sarà necessario impostare solo se la colonna di designazione è crittografata e Always Encrypted è abilitato per la connessione o per l'istruzione.<br /><br /> Se il forceEncrypt booleana è impostata su false, il driver non forza la crittografia sui parametri.|  
  
 I metodi di nuovo o sottoposto a overload in **SQLServerCallableStatement** classe  
  
|nome|Descrizione|  
|----------|-----------------|  
|public void registerOutParameter (int parametro parameterIndex, sqlType int, int precisione, scala int)<br /><br /> public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)<br /><br /> pubblica registerOutParameter void (stringa parameterName, sqlType int, int precisione, scala int)<br /><br /> public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)<br />public void setBigDecimal (stringa parameterName, BigDecimal bd, int precisione, scala int)<br /><br /> public void setTime (stringa parameterName, t Java, scala int)<br /><br /> public void setTimestamp (stringa parameterName, t Java, scala int)<br /><br /> public void setDateTimeOffset (stringa parameterName, t DateTimeOffset, scalabilità int)<br/><br/>pubblica setObject void finale (sCol stringa, oggetto x, int targetSqlType, precisione di Integer, la scala di int)|Questi metodi sono sottoposti a overload con una precisione o un argomento di scala o entrambi per il supporto di Always Encrypted per i tipi di dati specifici che richiedono la precisione e informazioni sulla scala.|  
|public void setDateTime (parameterName String, Java x)<br /><br /> public void setSmallDateTime (parameterName String, Java x)<br /><br /> pubblica setUniqueIdentifier void (parameterName stringa, stringa guid)<br /><br /> pubblica setMoney void (stringa parameterName, bd BigDecimal)<br /><br /> pubblica setSmallMoney void (stringa parameterName, bd BigDecimal)<br/><br/>pubblica Timestamp getDateTime (int index)<br/><br/>pubblica Timestamp getDateTime (stringa sCol)<br/><br/>pubblica Timestamp getDateTime (int index, calendario cal)<br/><br/>pubblica Timestamp getSmallDateTime (indice int)<br/><br/>pubblica Timestamp getSmallDateTime (stringa sCol)<br/><br/>pubblica getSmallDateTime Timestamp (int index, calendario cal)<br/><br/>pubblica getSmallDateTime Timestamp (nome della stringa, calendario cal)<br/><br/>pubblica BigDecimal getMoney (indice int)<br/><br/>pubblica BigDecimal getMoney (stringa sCol)<br/><br/>pubblica BigDecimal getSmallMoney (indice int)<br/><br/>pubblica BigDecimal getSmallMoney (stringa sCol)|Questi metodi vengono aggiunti per supportare la crittografia sempre attiva per il denaro di tipi di dati, smallmoney, uniqueidentifier, datetime e smalldatetime. <br/><br/>Si noti che il metodo setTimestamp() esistente viene utilizzato per l'invio di valori dei parametri per la colonna crittografata datetime2. Per data e ora crittografati e le colonne smalldatetime utilizzare rispettivamente i nuovi metodi setDateTime() e setSmallDateTime().|  
|public void setObject (parameterName String, Object o, n int, int m, forceEncrypt booleano)<br /><br /> public void setObject (parameterName stringa, Object obj, SQLType jdbcType, scalabilità int, forceEncrypt booleano)<br /><br /> public void setDate (java.sql.Date x, c, calendario, stringa parameterName forceEncrypt booleano)<br /><br /> public void setTime (stringa parameterName, t Java, scala int, forceEncrypt booleano)<br /><br /> public void setTime (parameterName String, Java x, c, calendario forceEncrypt booleano)<br /><br /> public void setDateTime (parameterName String, Java x, forceEncrypt booleano)<br /><br /> public void setDateTimeOffset (stringa parameterName, t DateTimeOffset, scalabilità int, forceEncrypt booleano)<br /><br /> pubblica setSmallDateTime void (parameterName String, Java x, forceEncrypt booleano)<br /><br /> public void setTimestamp (stringa parameterName, t Java, scala int, forceEncrypt booleano)<br /><br /> public void setTimestamp (parameterName String, Java x, forceEncrypt booleano)<br /><br /> pubblica setUniqueIdentifier void (parameterName stringa, stringa guid, forceEncrypt booleano)<br /><br /> public void setBytes (parameterName stringa, byte [] b, forceEncrypt booleano)<br /><br /> public void setByte (parameterName stringa, byte b, forceEncrypt booleano)<br /><br /> public void setString (parameterName stringa, valori String, booleano forceEncrypt)<br /><br /> pubblica setNString void finale (parameterName stringa, valore della stringa, booleano forceEncrypt)<br /><br /> pubblica setMoney void (stringa parameterName, BigDecimal bd, forceEncrypt booleano)<br /><br /> pubblica setSmallMoney void (stringa parameterName, BigDecimal bd, forceEncrypt booleano)<br /><br /> public void setBigDecimal (stringa parameterName BigDecimal bd, int mobile e precisione, scala int forceEncrypt booleano)<br /><br /> public void setDouble (parameterName stringa, double d, forceEncrypt booleano)<br /><br /> public void setFloat (parameterName String, float f, forceEncrypt booleano)<br /><br /> public void setInt (parameterName String, int i, forceEncrypt booleano)<br /><br /> public void setLong (parameterName String, long l, forceEncrypt booleano)<br /><br /> public void setShort (parameterName String, short s, forceEncrypt booleano)<br /><br /> public void setBoolean (parameterNames String, boolean b, forceEncrypt booleano)<br/><br/>public void setTimeStamp (sCol String, Java, x, c, calendario forceEncrypt booleano)|Imposta il parametro designato sul valore Java specificato.<br /><br /> Se il forceEncrypt booleana è impostata su true, la query parametro sarà necessario impostare solo se la colonna di designazione è crittografata e Always Encrypted è abilitato per la connessione o per l'istruzione.<br /><br /> Se il forceEncrypt booleana è impostata su false, il driver non forza la crittografia sui parametri.|
 

 I metodi di nuovo o sottoposto a overload in **SQLServerResultSet** classe  
  
|nome|Descrizione|  
|----------|-----------------|  
|pubblica stringa getUniqueIdentifier (int columnIndex)<br/><br/>pubblica getUniqueIdentifier String (stringa columnLabel)<br/><br/>   pubblica Java getDateTime (int columnIndex) <br/><br/> pubblica Java getDateTime (columnName stringa)   <br/><br/> pubblica Java getDateTime (int columnIndex, calendario cal)   <br/><br/>pubblica Java getDateTime (stringa colName, calendario cal)    <br/><br/>pubblica Java getSmallDateTime (int columnIndex)    <br/><br/> pubblica Java getSmallDateTime (columnName stringa)   <br/><br/> pubblica Java getSmallDateTime (int columnIndex, calendario cal)   <br/><br/> pubblica Java getSmallDateTime (stringa colName, calendario cal)   <br/><br/>  pubblica BigDecimal getMoney (int columnIndex)  <br/><br/> pubblica BigDecimal getMoney (columnName stringa)   <br/><br/> pubblica BigDecimal getSmallMoney (int columnIndex)   <br/><br/>  pubblica BigDecimal getSmallMoney (columnName stringa)  <br/><br/>pubblica updateMoney void (stringa columnName, BigDecimal x)    <br/><br/>  pubblica updateSmallMoney void (stringa columnName, BigDecimal x)  <br/><br/>     pubblica updateDateTime void (indice int, Java x) <br/><br/> pubblica updateSmallDateTime void (indice int, Java x) |Questi metodi vengono aggiunti per supportare la crittografia sempre attiva per il denaro i tipi di dati, smallmoney, uniqueidentifier, datetime e smalldatetime. <br/><br/>Si noti che il metodo updateTimestamp() esistente viene utilizzato per l'aggiornamento delle colonne datetime2 crittografato. Per data e ora crittografati e le colonne smalldatetime utilizzare rispettivamente i nuovi metodi updateDateTime() e updateSmallDateTime().|
|public void updateBoolean (int index, booleano x, forceEncrypt booleano)  <br/><br/>  public void updateByte (int index, byte x, forceEncrypt booleano)  <br/><br/>  public void updateShort (int index, x breve, forceEncrypt booleano)  <br/><br/> public void updateInt (indice int, int x, forceEncrypt booleano)   <br/><br/>  public void updateLong (int index, prolungata x, forceEncrypt booleano)  <br/><br/> public void updateFloat (int index, float x, forceEncrypt booleano)   <br/><br/> public void updateDouble (int index, double x, forceEncrypt booleano)   <br/><br/> public void updateMoney (int index, x, booleano forceEncrypt BigDecimal)   <br/><br/>  public void updateMoney (stringa columnName, x, booleano forceEncrypt BigDecimal)  <br/><br/> public void updateSmallMoney (int index, x, booleano forceEncrypt BigDecimal)   <br/><br/>  public void updateSmallMoney (stringa columnName, x, booleano forceEncrypt BigDecimal)  <br/><br/> public void updateBigDecimal (int index, BigDecimal x, precisione di Integer, Integer scala, forceEncrypt booleano)   <br/><br/>  public void updateString (int columnIndex, stringa stringValue, forceEncrypt booleano)  <br/><br/>  public void updateNString (int columnIndex, stringa noppure stringa, booleano forceEncrypt)  <br/><br/>  public void updateNString (columnLabel stringa, stringa noppure stringa, booleano forceEncrypt)  <br/><br/> public void updateBytes (int index, byte x[], forceEncrypt booleano)   <br/><br/>  public void updateDate (int index, java.sql.Date x, forceEncrypt booleano)  <br/><br/> public void updateTime (indice int, Java, scala interi, x forceEncrypt booleano)   <br/><br/> public void updateTimestamp (indice int, Java, scala int, x forceEncrypt booleano)   <br/><br/> pubblica updateDateTime void (indice int, Java, scala interi, x forceEncrypt booleano)   <br/><br/> pubblica updateSmallDateTime void (indice int, Java, scala interi, x forceEncrypt booleano)   <br/><br/>  pubblica updateDateTimeOffset void (int index, DateTimeOffset, scala interi, x forceEncrypt booleano)  <br/><br/> public void updateUniqueIdentifier (int index, stringa x, forceEncrypt booleano)    <br/><br/>  public void updateObject (int index, l'oggetto x, int precisione, scala int, boolean forceEncrypt)  <br/><br/>  public void updateObject (int index, Object obj, SQLType targetSqlType, scalabilità int, forceEncrypt booleano)  <br/><br/> public void updateBoolean (columnName stringa, booleano x, forceEncrypt booleano)    <br/><br/>  public void updateByte (columnName stringa, byte x, forceEncrypt booleano)  <br/><br/>  public void updateShort (columnName stringa, x breve, forceEncrypt booleano)  <br/><br/> public void updateInt (columnName String, int x, forceEncrypt booleano)   <br/><br/>   public void updateLong (columnName String, long x, forceEncrypt booleano) <br/><br/>  public void updateFloat (columnName String, float x, forceEncrypt booleano)  <br/><br/>  public void updateDouble (columnName stringa, double x, forceEncrypt booleano)  <br/><br/> public void updateBigDecimal (stringa columnName, x, booleano forceEncrypt BigDecimal)   <br/><br/>  public void updateBigDecimal (stringa columnName, BigDecimal x, precisione di Integer, Integer scala, forceEncrypt booleano)  <br/><br/> public void updateString (columnName stringa, stringa x, forceEncrypt booleano)   <br/><br/>  public void updateBytes (columnName stringa, byte x[], forceEncrypt booleano)  <br/><br/> public void updateDate (columnName stringa, java.sql.Date x, forceEncrypt booleano)   <br/><br/>  public void updateTime (columnName String, Java, scala int, x forceEncrypt booleano)  <br/><br/>  public void updateTimestamp (columnName String, Java, scala int, x forceEncrypt booleano)  <br/><br/> public void updateDateTime (columnName String, Java, scala int, x forceEncrypt booleano)   <br/><br/>  public void updateSmallDateTime (columnName String, Java, scala int, x forceEncrypt booleano)  <br/><br/>  public void updateDateTimeOffset (DateTimeOffset x, scalabilità, int, stringa columnName forceEncrypt booleano)  <br/><br/>  public void updateUniqueIdentifier (columnName stringa, stringa x, forceEncrypt booleano)<br/><br/>public void updateObject (columnName stringa, oggetto x, int precisione, scala int, boolean forceEncrypt)<br/><br/>public void updateObject (columnName stringa, Object obj, SQLType targetSqlType, scalabilità int, forceEncrypt booleano)|Aggiornare la colonna designata sul valore java specificato.<br/><br/>Se il forceEncrypt booleana è impostata su true, la colonna verrà essere impostata solo se sono crittografati e Always Encrypted è abilitato per la connessione o per l'istruzione.<br/><br/>Se il forceEncrypt booleana è impostata su false, il driver non forza la crittografia sui parametri.|

  
Nuovi tipi nella **microsoft.sql.Types** classe
|nome|Descrizione|  
|----------|-----------------|  
|DATETIME, SMALLDATETIME, MONEY, SMALLMONEY, GUID|Usare questi tipi come tipi SQL di destinazione quando si inviano i valori dei parametri **crittografato** datetime, smalldatetime, money, smallmoney, colonne di tipo uniqueidentifier usando metodi setObject()/updateObject() API.|  
  
  
 **SQLServerStatementColumnEncryptionSetting Enum**  
  
 Specifica come cui dati verranno inviati e ricevuti durante la lettura e scrittura alle colonne crittografate. A seconda della query specifica, l'impatto sulle prestazioni può essere ridotto ignorando l'elaborazione del driver sempre crittografato quando si usano colonne non crittografate. Si noti che queste impostazioni non possono essere usate per ignorare la crittografia e ottenere l'accesso ai dati di testo normale.  
  
 **Sintassi**  
  
```java
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **Membri**  
  
|nome|Descrizione|  
|----------|-----------------|  
|UseConnectionSetting|Specifica che il comando deve essere predefinito per l'impostazione di Always Encrypted nella stringa di connessione.|  
|Abilitata|Abilita Always Encrypted per la query.|  
|ResultSetOnly|Specifica che solo i risultati del comando devono essere elaborati in base alla routine sempre crittografato nel driver. Utilizzare questo valore quando il comando non dispone di parametri che richiedono la crittografia.|  
|Disabilitata|Disabilita Always Encrypted per la query.|  
  
 L'impostazione del livello di istruzione per Always Encrypted viene aggiunto alla classe SQLServerConnection e alla classe SQLServerConnectionPoolProxy. I metodi seguenti di queste classi sono sottoposti a overload con la nuova impostazione.  
  
|nome|Descrizione|  
|----------|-----------------|  
|pubblica istruzione createStatement (int NLE, nConcur int, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Crea un oggetto istruzione che genera oggetti con set di risultati con il tipo specificato, la concorrenza, trattenibilità e impostazione di crittografia di colonna.|  
|pubblica prepareCall CallableStatement (stringa sql, NLE int, int nConcur, statementHoldability int, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)|Crea un oggetto CallableStatement con l'impostazione di crittografia di colonna specificata che consentono di generare oggetti set di risultati con il tipo specificato, concorrenza e la trattenibilità.|  
|pubblica PreparedStatement prepareStatement (sql String, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Crea un oggetto di impostazione PreparedStatement con l'impostazione di crittografia di colonna specificata che ha la possibilità di recuperare le chiavi generate automaticamente.|  
|pubblica PreparedStatement prepareStatement (stringa sql, nomi di colonna stringa [], SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Crea un oggetto di impostazione PreparedStatement con l'impostazione di crittografia di colonna specificata che genera gli oggetti set di risultati con i nomi di colonna specificato.|  
|pubblica PreparedStatement prepareStatement (sql String, int [] columnIndexes, SQLServerStatementColumnEncryptionSetting stmtColEncSetting|Crea un oggetto di impostazione PreparedStatement con l'impostazione di crittografia di colonna specificata che genera gli oggetti set di risultati con gli indici di colonna specificato.|  
|pubblica PreparedStatement prepareStatement (stringa sql, NLE int, int nConcur, nHold int, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Crea un oggetto di impostazione PreparedStatement con l'impostazione di crittografia di colonna specificata che consentono di generare oggetti set di risultati con il tipo specificato, concorrenza e la trattenibilità.|  
  
> [!NOTE]  
>  Se Always Encrypted è disabilitato per una query e la query include parametri che devono essere crittografati (parametri che corrispondono alle colonne crittografate), la query avrà esito negativo.  
>   
>  Se Always Encrypted è disabilitato per una query e la query restituisce risultati dalle colonne crittografate, la query restituirà i valori crittografati. I valori crittografati avranno il tipo di dati varbinary.  
  
 ## <a name="see-also"></a>Vedere anche  
 [Utilizzo di Always Encrypted con il JDBC Driver](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

