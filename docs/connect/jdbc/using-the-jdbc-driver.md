---
title: Utilizzo del Driver JDBC | Documenti Microsoft
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
ms.assetid: 6faaf05b-8b70-4ed2-9b44-eee5897f1cd0
caps.latest.revision: "54"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 018679acc5c3e0119755e5ab5e0378c6f3fec7f0
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="using-the-jdbc-driver"></a>Utilizzo del driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  In questa sezione vengono fornite istruzioni introduttive per creare una semplice connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database utilizzando il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]. Prima di connettersi a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] deve prima essere installato nel computer locale o un server, e il driver JDBC deve essere installato nel computer locale.  
  
## <a name="choosing-the-right-jar-file"></a>Scelta del file JAR corretto  
 Il Driver JDBC di Microsoft 6.2 per SQL Server fornisce **mssql-jdbc-6.2.1.jre7.jar**, e **mssql-jdbc-6.2.1.jre8.jar** classe i file di libreria da utilizzare a seconda del preferito di Java Runtime Impostazioni Environment (JRE).  
  
  Microsoft JDBC driver 6.0 e 4.2 per SQL Server forniscono **sqljdbc41.jar**, e **sqljdbc42.jar** classe i file di libreria da utilizzare a seconda delle impostazioni preferite di Java Runtime Environment (JRE).  
  
 Microsoft JDBC Driver 4.1 per SQL Server fornisce il **sqljdbc41.jar** file di libreria di classi da utilizzare a seconda delle impostazioni preferite di Java Runtime Environment (JRE).  
  
 Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 4.0 fornisce **sqljdbc.jar** e **sqljdbc4.jar** classe i file di libreria da utilizzare a seconda delle impostazioni preferite di Java Runtime Environment (JRE).  
  
 La scelta determinerà anche le funzionalità disponibili. Per ulteriori informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="setting-the-classpath"></a>Impostazione del classpath  
 Il driver JDBC non fa parte di Java SDK. Se si desidera utilizzarlo, è necessario impostare il classpath per includere il **sqljdbc.jar** file **sqljdbc4.jar** file, il **sqljdbc41.jar** file, o  **sqljdbc42.jar** file. Se tramite 6.2 Driver JDBC, impostare il classpath per includere il **mssql-jdbc-6.2.1.jre7.jar** o **mssql-jdbc-6.2.1.jre8.jar**. Se nel classpath manca una voce, l'applicazione genererà l'eccezione comune "Classe non trovata".  
  
### <a name="for-microsoft-jdbc-driver-62"></a>Per Microsoft JDBC Driver 6.2
 Il **mssql-jdbc-6.2.1.jre7.jar** o **mssql-jdbc-6.2.1.jre8.jar** file vengono installati nel percorso seguente:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \mssql-jdbc-6.2.1.jre7.jar 
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \mssql-jdbc-6.2.1.jre8.jar
  
 Nell'esempio seguente viene riportata l'istruzione CLASSPATH utilizzata per un'applicazione di Windows:  
  
 `CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.2 for SQL Server\sqljdbc_6.2\enu\mssql-jdbc-6.2.1.jre8.jar`  
  
 Nell'esempio seguente viene riportata l'istruzione CLASSPATH utilizzata per un'applicazione di Unix e Linux:  
  
 `CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_6.2/enu/mssql-jdbc-6.2.1.jre8.jar`  
  
 È necessario assicurarsi che l'istruzione CLASSPATH contenga un solo [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], ad esempio mssql-jdbc-6.2.1.jre7.jar o mssql-jdbc-6.2.1.jre8.jar.  

### <a name="for-microsoft-jdbc-driver-40-41-42-and-60"></a>Per Microsoft JDBC Driver 4.0, 4.1, 4.2 e 6.0
 I file sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar e sqljdbc42.jar vengono installati nei percorsi seguenti:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \sqljdbc.jar  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \sqljdbc4.jar  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \sqljdbc41.jar  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \sqljdbc42.jar  
  
 Nell'esempio seguente viene riportata l'istruzione CLASSPATH utilizzata per un'applicazione di Windows:  
  
 `CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.0 for SQL Server\sqljdbc_4.2\enu\sqljdbc42.jar`  
  
 Nell'esempio seguente viene riportata l'istruzione CLASSPATH utilizzata per un'applicazione di Unix e Linux:  
  
 `CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_4.2/enu/sqljdbc42.jar`  
  
 È necessario assicurarsi che l'istruzione CLASSPATH contenga un solo [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], ad esempio sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar o sqljdbc42.jar.  
  
> [!NOTE]  
>  Nei sistemi Windows i nomi di directory con lunghezza superiore a quella della convenzione 8.3 o i nomi delle cartelle con spazi possono causare problemi con i classpath. Se si ritiene di questi tipi di problemi, si consiglia di spostare il file sqljdbc.jar, sqljdbc4.jar file o il file sqljdbc41.jar in un nome di directory semplice, ad esempio `C:\Temp`, modificare il classpath e determinare se che consente di risolvere il problema.  
  
### <a name="applications-that-are-run-directly-at-the-command-prompt"></a>Applicazioni eseguite direttamente dal prompt dei comandi  
 Il classpath è configurato nel sistema operativo. Accodare sqljdbc.jar, sqljdbc4.jar o sqljdbc41.jar al classpath del sistema. In alternativa, è possibile specificare il classpath nella riga di comando Java che esegue l'applicazione utilizzando il `java -classpath` opzione.  
  
### <a name="applications-that-run-in-an-ide"></a>Applicazioni eseguite in un IDE  
 Ogni fornitore IDE offre un metodo diverso per impostare il classpath nel proprio IDE. La semplice impostazione del classpath nel sistema operativo non funzionerà. È necessario aggiungere sqljdbc.jar, sqljdbc4.jar o sqljdbc41.jar al classpath IDE.  
  
### <a name="servlets-and-jsps"></a>Servlet e JSP  
 Servlet e JSP vengono eseguiti in un motore servlet/JSP, ad esempio Tomcat. Il classpath deve essere impostato in base alla documentazione del motore del servlet/JSP. La semplice impostazione del classpath nel sistema operativo non funzionerà. Alcuni motori del servlet/JSP offrono schermate di installazione utilizzabili per impostare il classpath del motore. In questo caso è necessario accodare il file JDBC Driver JAR corretto al classpath del motore esistente e riavviare il motore. In altri casi è possibile distribuire il driver copiando il file sqljdbc.jar, sqljdbc4.jar o sqljdbc41.jar in una directory specifica, ad esempio lib, durante l'installazione del motore. Il classpath del driver del motore può anche essere indicato in un file di configurazione specifico.  
  
### <a name="enterprise-java-beans"></a>Enterprise Java Beans  
 Le piattaforme Enterprise Java Beans (EJB) vengono eseguite in un contenitore EJB. I contenitori EJB provengono da vari fornitori. Le applet Java vengono eseguite in un browser ma scaricate da un server Web. Copiare i file sqljdbc.jar, sqljdbc4.jar o sqljdbc41.jar nella radice del server web e specificare il nome del file JAR nel tag HTML archive dell'applet, ad esempio, `<applet ... archive=sqljdbc.jar>`.  
  
## <a name="making-a-simple-connection-to-a-database"></a>Creazione di una connessione semplice a un database  
 Se si utilizza la libreria di classi sqljdbc.jar, le applicazioni devono innanzitutto registrare il driver, come indicato di seguito:  
  
 `Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");`  
  
 Quando viene caricato il driver, è possibile stabilire una connessione tramite un URL di connessione e il metodo getConnection della classe DriverManager:  
  
```  
String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
   "databaseName=AdventureWorks;user=MyUserName;password=*****;";  
Connection con = DriverManager.getConnection(connectionUrl);  
```  
  
 Nell'API di JDBC 4.0, il metodo DriverManager.getConnection è stato migliorato per caricare automaticamente i driver JDBC. Pertanto, le applicazioni non è necessario chiamare il metodo forName per registrare o caricare il driver quando si utilizza il sqljdbc4.jar, sqljdbc41.jar o sqljdbc42.jar libreria di classi.  
  
 Quando viene chiamato il metodo getConnection della classe DriverManager, un driver appropriato viene individuato dal set di driver JDBC registrati. il file sqljdbc4.jar, sqljdbc41.jar o sqljdbc42.jar include il file "META-INF/services/java.sql.Driver", che contiene il **sqlserverdriver** come driver registrato. Le applicazioni esistenti, utilizzate attualmente per caricare i driver tramite il metodo forName, continueranno a funzionare senza alcuna modifica.  
  
> [!NOTE]  
>  la libreria di classi sqljdbc4.jar, sqljdbc41.jar o sqljdbc42.jar non può essere utilizzata con le versioni precedenti di Java Runtime Environment (JRE). Vedere [requisiti di sistema per il Driver JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md) per l'elenco di versioni JRE supportate dal [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 Per ulteriori informazioni su come connettersi con origini dati e utilizzare un URL di connessione, vedere [creazione dell'URL di connessione](../../connect/jdbc/building-the-connection-url.md) e [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
