---
title: Wrapper e interfacce | Documenti Microsoft
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
ms.assetid: 27fc9b72-9f21-4728-abcb-5c015f28a6ab
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1cee557293ccc5949977f0d3a9225ba0ea3d018d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="wrappers-and-interfaces"></a>Wrapper e interfacce
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta le interfacce che consentono di creare un proxy di una classe e i wrapper che consentono di accedere alle estensioni dell'API JDBC siano di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] tramite un'interfaccia proxy.  
  
## <a name="wrappers"></a>Wrapper  
 Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta l'interfaccia Java.SQL. Questa interfaccia fornisce un meccanismo per le estensioni di accesso all'API JDBC specifiche di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] tramite un'interfaccia proxy.  
  
 L'interfaccia Java.SQL definisce due metodi: **isWrapperFor** e **unwrap**. Il **isWrapperFor** metodo controlla se l'oggetto di input specificato implementa questa interfaccia. Il **unwrap** metodo restituisce un oggetto che implementa questa interfaccia per consentire l'accesso per il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] metodi specifici.  
  
 **isWrapperFor** e **unwrap** i metodi vengono esposti come indicato di seguito:  
  
-   [Metodo isWrapperFor &#40;SQLServerCallableStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)  
  
-   [Metodo Unwrap &#40;SQLServerCallableStatement&#41;](../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)  
  
-   [Metodo isWrapperFor &#40;SQLServerConnectionPoolDataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverconnectionpooldatasource.md)  
  
-   [Metodo Unwrap &#40;SQLServerConnectionPoolDataSource&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md)  
  
-   [Metodo isWrapperFor &#40;SQLServerDataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)  
  
-   [Metodo Unwrap &#40;SQLServerDataSource&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)  
  
-   [Metodo isWrapperFor &#40;SQLServerPreparedStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)  
  
-   [Metodo Unwrap &#40;SQLServerPreparedStatement&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)  
  
-   [Metodo isWrapperFor &#40;SQLServerStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)  
  
-   [Metodo Unwrap &#40;SQLServerStatement&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)  
  
-   [Metodo isWrapperFor &#40;SQLServerXADataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md)  
  
-   [Metodo Unwrap &#40;SQLServerXADataSource&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)  
  
## <a name="interfaces"></a>Interfacce  
 A partire da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Driver JDBC 3.0, le interfacce sono disponibili per un server applicazioni di accedere a un metodo specifico del driver dalla classe associata. Il server applicazioni può eseguire il wrapping della classe mediante la creazione di un proxy, esponendo il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-specifica funzionalità da un'interfaccia. Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta interfacce che dispongono di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] costanti in modo da un server applicazioni è possibile creare un proxy della classe e i metodi specifici.  
  
 Le interfacce derivano da interfacce Java è possibile utilizzare lo stesso oggetto dopo averne annullato il wrapping per accedere a funzionalità specifiche del driver o generico standard [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] funzionalità.  
  
 Sono aggiunte le interfacce seguenti:  
  
-   [ISQLServerCallableStatement](../../connect/jdbc/reference/isqlservercallablestatement-interface.md)  
  
-   [ISQLServerConnection](../../connect/jdbc/reference/isqlserverconnection-interface.md)  
  
-   [ISQLServerDataSource](../../connect/jdbc/reference/isqlserverdatasource-interface.md)  
  
-   [ISQLServerPreparedStatement](../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)  
  
-   [ISQLServerResultSet](../../connect/jdbc/reference/isqlserverresultset-interface.md)  
  
-   [ISQLServerStatement](../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Description  
 Questo esempio viene illustrato come accedere a un [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-funzione specifica da un oggetto origine dati. Questa classe di origine dati potrebbe sono stata integrata in un server applicazioni. Per accedere alla costante o una funzione specifica del driver JDBC, è possibile annullare il wrapping di origine dati da un'interfaccia ISQLServerDataSource e utilizzare le funzioni dichiarate in questa interfaccia.  
  
### <a name="code"></a>Codice  
  
```  
import javax.sql.*;  
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  
  
public class UnWrapTest {  
   public static void main(String[] args) {  
      // This is a test.  This DataSource object could be something from an appserver   
      // which has wrapped the real SQLServerDataSource with its own wrapper  
      SQLServerDataSource ds = new SQLServerDataSource();  
      checkSendStringParametersAsUnicode(ds);  
   }  
  
   // Unwrap to the ISQLServerDataSource interface to access the getSendStringParametersAsUnicode function  
   static void checkSendStringParametersAsUnicode(DataSource ds) {  
      try {  
         final ISQLServerDataSource sqlServerDataSource = ds.unwrap(ISQLServerDataSource.class);  
         boolean sendStringParametersAsUnicode = sqlServerDataSource.getSendStringParametersAsUnicode();  
  
         System.out.println("Send string as parameter value is:-" + sendStringParametersAsUnicode);  
  
      } catch (SQLException sqlE) {  
         System.out.println("Exception:-" + sqlE);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sui tipi di dati del driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
