---
title: Informazioni sulle transazioni XA | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 574e326f-0520-4003-bdf1-62d92c3db457
caps.latest.revision: 80
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a78fdb7edae90289d64d4c7fdf74ac3a12d4b115
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32853046"
---
# <a name="understanding-xa-transactions"></a>Informazioni sulle transazioni XA
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce il supporto per Java Platform, Enterprise Edition/JDBC 2.0 le transazioni distribuite facoltative. Le connessioni JDBC ottenute dal [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) classe può partecipare standard, ad esempio i server di applicazione Enterprise Edition (Java EE) Java Platform, elaborazione delle transazioni distribuite.  
  
> [!WARNING]  
>  Microsoft JDBC Driver 4.2 (e versioni successive) per SQL include nuove opzioni di timeout per la funzionalità esistente per il rollback automatico delle transazioni non preparate. Vedere [configurazione delle impostazioni di timeout sul lato server per il rollback automatico delle transazioni non preparate](../../connect/jdbc/understanding-xa-transactions.md#BKMK_ServerSide) più avanti in questo argomento per ulteriori dettagli.  
  
## <a name="remarks"></a>Osservazioni  
 Le classi per l'implementazione delle transazioni distribuite sono le seguenti:  
  
|Classe|Implementa|Description|  
|-----------|----------------|-----------------|  
|com.microsoft.sqlserver.jdbc.SQLServerXADataSource|javax.sql.XADataSource|Class factory per le connessioni distribuite.|  
|com.microsoft.sqlserver.jdbc.SQLServerXAResource|javax.transaction.xa.XAResource|Adattatore di risorse per il responsabile delle transazioni.|  
  
> [!NOTE]  
>  Le connessioni delle transazioni distribuite XA sono impostate sul livello di isolamento predefinito Read Committed.  
  
## <a name="guidelines-and-limitations-when-using-xa-transactions"></a>Linee guida e limitazioni relative all'utilizzo di transazioni XA  
 Le seguenti linee guida aggiuntive si applicano alle transazioni a "regime di controllo stretto ("tightly-coupled")":  
  
-   Quando si utilizzano le transazioni XA con Microsoft Distributed Transaction Coordinator (MS DTC), è possibile che la versione corrente di MS DTC non supporti il comportamento dei rami XA a "regime di controllo stretto ("tightly-coupled")". In MS DTC è ad esempio presente un mapping uno-a-uno tra un ID di transazione dei rami XA (XID) e un ID di transazione MS DTC e il lavoro eseguito da ognuno dei rami XA a regime di controllo libero ("loosely-coupled") viene isolato da quello degli altri rami.  
  
     L'hotfix fornito in [MSDTC and Tightly Coupled Transactions](http://support.microsoft.com/kb/938653) fornisce il supporto per i rami XA a più rami XA con lo stesso ID (GTRID) di transazione globale vengono eseguito il mapping a un singolo ID di transazione MS DTC. Questo supporto consente a più rami XA a vedere altra e le modifiche nella gestione delle risorse, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Oggetto [SSTRANSTIGHTLYCPLD](../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) flag consente alle applicazioni di utilizzare le transazioni XA fortemente accoppiate, transazione dei rami XA ID (BQUAL) diversi ma con la stessa transazione globale ID (GTRID) e ID di formato (FormatID). Per usare questa funzionalità, è necessario impostare il [SSTRANSTIGHTLYCPLD](../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) sul parametro del metodo XAResource.start flag:  
  
    ```  
    xaRes.start(xid, SQLServerXAResource.SSTRANSTIGHTLYCPLD);  
    ```  
  
## <a name="configuration-instructions"></a>Istruzioni di configurazione  
 Per utilizzare le origini dei dati XA con Microsoft Distributed Transaction Coordinator (MS DTC) per la gestione delle transazioni distribuite, è necessario utilizzare la procedura seguente.  
  
> [!NOTE]  
>  I componenti della transazione distribuita JDBC sono inclusi nella directory xa dell'installazione del driver JDBC. Tali componenti includono i file xa_install.sql e sqljdbc_xa.dll.  
  
### <a name="running-the-ms-dtc-service"></a>Esecuzione del servizio MS DTC  
 Il servizio MS DTC deve essere contrassegnato come **automatica** in Service Manager per assicurarsi che venga eseguito quando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] servizio è stato avviato. Per abilitare MS DTC per le transazioni XA, procedere come segue:  
  
 In Windows Vista e versioni successive:  
  
1.  Fare clic su di **avviare** pulsante digitare **dcomcnfg** all'inizio **ricerca** casella e quindi premere INVIO per aprire **Servizi componenti**. È anche possibile digitare %windir%\system32\comexp.msc nella **Inizia ricerca** casella per aprire **Servizi componenti**.  
  
2.  Espandere Servizi componenti, Computer, Computer locale, quindi Distributed Transaction Coordinator.  
  
3.  Fare doppio clic su **DTC locale** e quindi selezionare **proprietà**.  
  
4.  Fare clic su di **sicurezza** scheda la **proprietà DTC locale** la finestra di dialogo.  
  
5.  Selezionare il **Abilita transazioni XA** casella di controllo e quindi fare clic su **OK**. Il servizio MS DTC verrà riavviato.  
  
6.  Fare clic su **OK** per chiudere la **proprietà** la finestra di dialogo e quindi chiudere **Servizi componenti**.  
  
7.  Arrestare e riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per assicurarsi che venga eseguita la sincronizzazione con le modifiche di MS DTC.  
  
### <a name="configuring-the-jdbc-distributed-transaction-components"></a>Configurazione dei componenti delle transazioni distribuite JDBC  
 Per configurare i componenti delle transazioni distribuite del driver JDBC, procedere come segue:  
  
1.  Copiare il nuovo file sqljdbc_xa.dll dalla directory di installazione del driver JDBC alla directory Binn di ogni [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] computer che farà parte di transazioni distribuite.  
  
    > [!NOTE]  
    >  Se si utilizzano transazioni XA con 32 bit [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], utilizzare il file sqljdbc_xa.dll nella x86 cartella, anche se il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è installato su un x64 processore. Se si utilizzano transazioni XA con a 64 bit [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in x64 processore, utilizzare il file sqljdbc_xa.dll nella x64 cartella.  
  
2.  Eseguire lo script di database xa_install.sql su ogni [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istanza che farà parte di transazioni distribuite. Lo script installa le stored procedure estese chiamate da sqljdbc_xa.dll. Tali stored procedure estese implementano transazione distribuita e XA supporto per il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]. È necessario eseguire questo script come amministratore del [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istanza.  
  
3.  Per concedere a un utente specifico l'autorizzazione necessaria per partecipare alle transazioni distribuite con il driver JDBC, aggiungere l'utente al ruolo SqlJDBCXAUser.  
  
 È possibile configurare solo una versione dell'assembly sqljdbc_xa.dll in ogni [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istanza alla volta. Le applicazioni debbano utilizzare versioni diverse del driver JDBC per connettersi alla stessa [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istanza utilizzando la stessa connessione XA. In tal caso, deve essere installato file sqljdbc_xa.dll, fornito con il driver JDBC più recente, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istanza.  
  
 Esistono tre modi per verificare la versione del file sqljdbc_xa.dll attualmente installata nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istanza:  
  
1.  Aprire la directory LOG del [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] computer che farà parte di transazioni distribuite. Selezionare e aprire il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] file "ERRORLOG". Eseguire la ricerca della frase "Using 'SQLJDBC_XA.dll' version ..." nel file "ERRORLOG".  
  
2.  Aprire la directory Binn di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] computer che farà parte di transazioni distribuite. Selezionare l'assembly sqljdbc_xa.dll.  
  
    -   In Windows Vista o versione successiva: fare clic con il pulsante destro del mouse su sqljdbc_xa.dll, quindi scegliere Proprietà. Scegliere il **dettagli** scheda. Il **versione del File** campo Visualizza la versione del file sqljdbc_xa.dll attualmente installata nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istanza.  
  
3.  Impostare la funzionalità di registrazione come illustrato nell'esempio di codice della sezione successiva. Eseguire la ricerca della frase "Server XA DLL version:..." nel file del log di output.  
  
###  <a name="BKMK_ServerSide"></a> Configurazione delle impostazioni di timeout sul lato server per il rollback automatico delle transazioni non preparate  
  
> [!WARNING]  
>  Questa opzione sul lato server è nuova con Microsoft JDBC Driver 4.2 (e versioni successive) per SQL Server. Per ottenere il comportamento aggiornato, verificare che il file sqljdbc_xa.dll nel server sia aggiornato. Per ulteriori informazioni sull'impostazione di timeout lato client, vedere [XAResource](http://docs.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html).  
  
 Sono disponibili due impostazioni del Registro di sistema (valori DWORD) per controllare il comportamento di timeout delle transazioni distribuite:  
  
-   **XADefaultTimeout** (in secondi): il valore di timeout predefinito da utilizzare quando l'utente non specifica alcun timeout. Il valore predefinito è 0.  
  
-   **XAMaxTimeout** (in secondi): il valore massimo di timeout che un utente può impostare. Il valore predefinito è 0.  
  
 Queste impostazioni sono specifiche dell'istanza di SQL Server e devono essere create nella seguente chiave del Registro di sistema:  
  
 HKEY_LOCAL_MACHINE\Software\Microsoft\Microsoft SQL Server\MSSQL<\<**versione**>.\< *instance_name*> \XATimeout  
  
> [!NOTE]  
>  Per Server SQL a 32 bit in esecuzione in computer a 64 bit, le impostazioni del Registro di sistema devono essere create nella seguente chiave: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Microsoft SQL Server\MSSQL\<versione >. < instance_name > \ XATimeout  
  
 Un valore di timeout viene impostato per ogni transazione all'avvio e SQL Server esegue il rollback della transazione se il timeout scade. Il timeout viene determinato in base a queste impostazioni del Registro di sistema e a seconda di ciò che ha specificato l'utente tramite XAResource.setTransactionTimeout(). Di seguito sono riportati alcuni esempi su come vengono interpretati questi valori di timeout:  
  
-   XADefaultTimeout = 0, XAMaxTimeout = 0  
  
     Indica che non verrà utilizzato alcun timeout predefinito e non verrà applicato alcun timeout massimo per i client. In questo caso, le transazioni avranno un timeout solo se il client imposta un timeout utilizzando XAResource.setTransactionTimeout.  
  
-   XADefaultTimeout = 60, XAMaxTimeout = 0  
  
     Indica che tutte le transazioni avranno un timeout di 60 secondi se il client non specifica alcun timeout. Se il client specifica un timeout, verrà utilizzato tale valore di timeout. Non viene applicato alcun valore massimo per il timeout.  
  
-   XADefaultTimeout = 30, XAMaxTimeout = 60  
  
     Indica che tutte le transazioni avranno un timeout di 30 secondi se il client non specifica alcun timeout. Se il client specifica un timeout, verrà utilizzato il timeout del client, a condizione che sia minore di 60 secondi (il valore massimo).  
  
-   XADefaultTimeout = 0, XAMaxTimeout = 30  
  
     Indica che tutte le transazioni avranno un timeout di 30 secondi (il valore massimo) se il client non specifica alcun timeout. Se il client specifica un timeout, verrà utilizzato il timeout del client, a condizione che sia minore di 30 secondi (il valore massimo).  
  
### <a name="upgrading-sqljdbcxadll"></a>Aggiornamento di sqljdbc_xa.dll  
 Quando si installa una nuova versione del driver JDBC, è consigliabile utilizzare il file sqljdbc_xa.dll della nuova versione per aggiornare il file sqljdbc_xa.dll nel server.  
  
> [!IMPORTANT]  
>  Aggiornare il file sqljdbc_xa.dll durante il periodo di manutenzione o quando nessuna transazione MS DTC è in corso.  
  
1.  Scaricare il file sqljdbc_xa.dll mediante il [!INCLUDE[tsql](../../includes/tsql_md.md)] comando **sqljdbc_xa DBCC (FREE)**.  
  
2.  Copiare il nuovo file sqljdbc_xa.dll dalla directory di installazione del driver JDBC alla directory Binn di ogni [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] computer che farà parte di transazioni distribuite.  
  
     La nuova DLL verrà caricata quando viene chiamata una procedura estesa in sqljdbc_xa.dll. Non è necessario riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per caricare le nuove definizioni.  
  
### <a name="configuring-the-user-defined-roles"></a>Configurazione dei ruoli definiti dall'utente  
 Per concedere a un utente specifico l'autorizzazione necessaria per partecipare alle transazioni distribuite con il driver JDBC, aggiungere l'utente al ruolo SqlJDBCXAUser. Ad esempio, utilizzare la seguente [!INCLUDE[tsql](../../includes/tsql_md.md)] codice per aggiungere un utente denominato 'shelby' (utente di accesso standard SQL denominato 'shelby') al ruolo SqlJDBCXAUser:  
  
```  
USE master  
GO  
EXEC sp_grantdbaccess 'shelby', 'shelby'  
GO  
EXEC sp_addrolemember [SqlJDBCXAUser], 'shelby'  
```  
  
 I ruoli SQL definiti dall'utente vengono definiti per database. Per creare il proprio ruolo al fine di ottenere maggiore sicurezza, sarà necessario definire il ruolo in ciascun database e aggiungere gli utenti per database. Il ruolo SqlJDBCXAUser è rigorosamente definito nel database master poiché viene utilizzato per concedere l'accesso alle stored procedure estese SQL JDBC che risiedono nel master. Sarà necessario concedere prima l'accesso al master ai singoli utenti, quindi consentire l'accesso al ruolo SqlJDBCXAUser una volta connessi al database master.  
  
## <a name="example"></a>Esempio  
  
```  
import java.net.Inet4Address;  
import java.sql.*;  
import java.util.Random;  
import javax.transaction.xa.*;  
import javax.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  
  
public class testXA {  
  
   public static void main(String[] args) throws Exception {  
  
      // Create variables for the connection string.  
      String prefix = "jdbc:sqlserver://";  
      String serverName = "localhost";  
      int portNumber = 1433;  
      String databaseName = "AdventureWorks";   
      String user = "UserName";   
      String password = "*****";  
      String connectionUrl = prefix + serverName + ":" + portNumber  
         + ";databaseName=" + databaseName + ";user=" + user + ";password=" + password;  
  
      try {  
         // Establish the connection.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         Connection con = DriverManager.getConnection(connectionUrl);  
  
         // Create a test table.  
         Statement stmt = con.createStatement();  
         try {  
            stmt.executeUpdate("DROP TABLE XAMin");   
         }  
         catch (Exception e) {  
         }  
         stmt.executeUpdate("CREATE TABLE XAMin (f1 int, f2 varchar(max))");  
         stmt.close();  
         con.close();  
  
         // Create the XA data source and XA ready connection.  
         SQLServerXADataSource ds = new SQLServerXADataSource();  
         ds.setUser(user);  
         ds.setPassword(password);  
         ds.setServerName(serverName);  
         ds.setPortNumber(portNumber);  
         ds.setDatabaseName(databaseName);  
         XAConnection xaCon = ds.getXAConnection();  
         con = xaCon.getConnection();  
  
         // Get a unique Xid object for testing.  
         XAResource xaRes = null;  
         Xid xid = null;  
         xid = XidImpl.getUniqueXid(1);  
  
         // Get the XAResource object and set the timeout value.  
         xaRes = xaCon.getXAResource();  
         xaRes.setTransactionTimeout(0);  
  
         // Perform the XA transaction.  
         System.out.println("Write -> xid = " + xid.toString());  
         xaRes.start(xid,XAResource.TMNOFLAGS);  
         PreparedStatement pstmt =   
         con.prepareStatement("INSERT INTO XAMin (f1,f2) VALUES (?, ?)");  
         pstmt.setInt(1,1);  
         pstmt.setString(2,xid.toString());  
         pstmt.executeUpdate();  
  
         // Commit the transaction.  
         xaRes.end(xid,XAResource.TMSUCCESS);  
         xaRes.commit(xid,true);  
  
         // Cleanup.  
         con.close();  
         xaCon.close();  
  
         // Open a new connection and read back the record to verify that it worked.  
         con = DriverManager.getConnection(connectionUrl);  
         ResultSet rs = con.createStatement().executeQuery("SELECT * FROM XAMin");  
         rs.next();  
         System.out.println("Read -> xid = " + rs.getString(2));  
         rs.close();  
         con.close();  
      }   
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
   }  
}  
  
class XidImpl implements Xid {  
  
   public int formatId;  
   public byte[] gtrid;  
   public byte[] bqual;  
   public byte[] getGlobalTransactionId() {return gtrid;}  
   public byte[] getBranchQualifier() {return bqual;}  
   public int getFormatId() {return formatId;}  
  
   XidImpl(int formatId, byte[] gtrid, byte[] bqual) {  
      this.formatId = formatId;  
      this.gtrid = gtrid;  
      this.bqual = bqual;  
   }  
  
   public String toString() {  
      int hexVal;  
      StringBuffer sb = new StringBuffer(512);  
      sb.append("formatId=" + formatId);  
      sb.append(" gtrid(" + gtrid.length + ")={0x");  
      for (int i=0; i<gtrid.length; i++) {  
         hexVal = gtrid[i]&0xFF;  
         if ( hexVal < 0x10 )  
            sb.append("0" + Integer.toHexString(gtrid[i]&0xFF));  
         else  
            sb.append(Integer.toHexString(gtrid[i]&0xFF));  
         }  
         sb.append("} bqual(" + bqual.length + ")={0x");  
         for (int i=0; i<bqual.length; i++) {  
            hexVal = bqual[i]&0xFF;  
            if ( hexVal < 0x10 )  
               sb.append("0" + Integer.toHexString(bqual[i]&0xFF));  
            else  
               sb.append(Integer.toHexString(bqual[i]&0xFF));  
         }  
         sb.append("}");  
         return sb.toString();  
      }  
  
      // Returns a globally unique transaction id.  
      static byte [] localIP = null;  
      static int txnUniqueID = 0;  
      static Xid getUniqueXid(int tid) {  
  
      Random rnd = new Random(System.currentTimeMillis());  
      txnUniqueID++;  
      int txnUID = txnUniqueID;  
      int tidID = tid;  
      int randID = rnd.nextInt();  
      byte[] gtrid = new byte[64];  
      byte[] bqual = new byte[64];  
      if ( null == localIP) {  
         try {  
            localIP = Inet4Address.getLocalHost().getAddress();  
         }  
         catch ( Exception ex ) {  
            localIP =  new byte[] { 0x01,0x02,0x03,0x04 };  
         }  
      }  
      System.arraycopy(localIP,0,gtrid,0,4);  
      System.arraycopy(localIP,0,bqual,0,4);  
  
      // Bytes 4 -> 7 - unique transaction id.  
      // Bytes 8 ->11 - thread id.  
      // Bytes 12->15 - random number generated by using seed from current time in milliseconds.  
      for (int i=0; i<=3; i++) {  
         gtrid[i+4] = (byte)(txnUID%0x100);  
         bqual[i+4] = (byte)(txnUID%0x100);  
         txnUID >>= 8;  
         gtrid[i+8] = (byte)(tidID%0x100);  
         bqual[i+8] = (byte)(tidID%0x100);  
         tidID >>= 8;  
         gtrid[i+12] = (byte)(randID%0x100);  
         bqual[i+12] = (byte)(randID%0x100);  
         randID >>= 8;  
      }  
      return new XidImpl(0x1234, gtrid, bqual);  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di transazioni con il driver JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  
