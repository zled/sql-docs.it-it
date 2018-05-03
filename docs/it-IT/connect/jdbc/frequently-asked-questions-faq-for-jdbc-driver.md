---
title: Domande frequenti (FAQ per il Driver JDBC) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
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
ms.assetid: cbc0e397-ecf2-4494-87b2-a492609bceae
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b53dc714cc0e4936d080ed9f9ccf25c344c3ebfb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="frequently-asked-questions-faq-for-jdbc-driver"></a>Domande frequenti (FAQ per il Driver JDBC)
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Questo articolo fornisce le risposte alle domande frequenti su Microsoft JDBC Driver per SQL Server.  
  
## <a name="frequently-asked-questions"></a>Domande frequenti  
**Come posso utile migliorare il Driver JDBC?**  
Il Driver JDBC è open source e il codice sorgente può trovarsi in [GitHub](https://github.com/microsoft/mssql-jdbc). È possibile migliorare il driver di archiviazione di problemi e che hanno contribuito alla base di codice.

**Supportano le versioni di SQL Server e non di Java il driver?**  
 Vedere il [Microsoft JDBC Driver per SQL Server Support Matrix](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md) pagina per informazioni dettagliate.  
  
 **Cosa è necessario conoscere quando si aggiorna il driver?**  
 Microsoft JDBC Driver 6.4 supporta JDBC 4.1, 4.2 e 4.3 (parzialmente) specifiche e include tre librerie di classi JAR nel pacchetto di installazione, come indicato di seguito:  
  
|JAR|Specifica JDBC|Versione di JDK|  
|-|-|-|  
|mssql-jdbc-6.4.0.jre9.jar|JDBC 4.3 (parzialmente), 4.2 e 4.1|JDK 9.0|  
|mssql-jdbc-6.4.0.jre8.jar|JDBC 4.2 e 4.1|JDK 8.0|  
|mssql-jdbc-6.4.0.jre7.jar|JDBC 4.1|JDK 7.0|  

 Il Driver JDBC di Microsoft 6.2 supporta le specifiche JDBC 4.0, 4.1 e 4.2 e include due librerie di classi JAR nel pacchetto di installazione, come indicato di seguito:  
  
|JAR|Specifica JDBC|Versione di JDK|  
|-|-|-|  
|mssql-jdbc-6.2.1.jre8.jar|JDBC 4.2, 4.1 e 4.0|JDK 8.0|  
|mssql-jdbc-6.2.1.jre7.jar|JDBC 4.1 e 4.0|JDK 7.0|  
 
 Microsoft JDBC driver 6.0 e 4.2 per SQL Server supporta le specifiche JDBC 4.0, 4.1 e 4.2 e includono due librerie di classi JAR nel pacchetto di installazione, come indicato di seguito:  
  
|JAR|Specifica JDBC|Versione di JDK|   
|-|-|-|  
|sqljdbc42.jar|JDBC 4.2, 4.1 e 4.0|JDK 8.0|  
|sqljdbc41.jar|JDBC 4.1 e 4.0|JDK 7.0|  
  
 Microsoft JDBC Driver 4.1 per SQL Server supporta la specifica JDBC 4.0 e include una libreria di classi JAR nel pacchetto di installazione, come indicato di seguito:  
  
|JAR|Specifica JDBC|Versione di JDK|    
|-|-|-|  
|sqljdbc41.jar|JDBC 4.0|JDK 7.0 and 6.0|
  
 **È necessario apportare alcuna modifica al codice nell'applicazione per utilizzare il driver più recente con la versione di SQL Server esistente?**  
 In generale, il driver è progettato per essere compatibile con le versioni precedenti in modo che non è necessario modificare le applicazioni esistenti quando si aggiorna il driver. Nel caso in cui una nuova versione del driver introduca una modifica significativa, la [note sulla versione per il Driver JDBC](../../connect/jdbc/release-notes-for-the-jdbc-driver.md) sezione vengono forniti dettagli deselezionare la modifica e l'impatto sulle applicazioni esistenti. Inoltre, è possibile esaminare le note sulla versione incluse con il driver per un elenco dei bug corretti in tale versione e per i problemi noti.  
  
 **Quanto costa il driver?**  
 Microsoft JDBC Driver per SQL Server è disponibile gratuitamente.  
  
 **È possibile ridistribuire il driver?** Il driver JDBC 4.1, 4.2, 6.0, 6.2 e 6.4 sono ridistribuibili. Esaminare la clausola "Codice distribuibile" nei contratti di licenza. 
   
 **È possibile utilizzare il driver per accedere a Microsoft SQL Server da un computer Linux?** Sì. È possibile usare il driver per accedere a SQL Server da Unix, Linux e altre piattaforme non Windows. Vedere [Microsoft JDBC Driver per SQL Server Support Matrix](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md) per altri dettagli.  
  
 **Il driver supporta la crittografia Secure Sockets Layer (SSL)?** A partire dalla versione 1.2, il driver supporta la crittografia Secure Sockets Layer (SSL). Per ulteriori informazioni, vedere [utilizzando la crittografia SSL](../../connect/jdbc/using-ssl-encryption.md).  
  
 **I tipi di autenticazione supportati da Microsoft JDBC Driver per SQL Server?**  
 La tabella seguente elenca le opzioni di autenticazione disponibili. L'autenticazione Kerberos Java pura è disponibile a partire dalla versione 4.0 del driver.  
  
|||  
|-|-|  
|Piattaforma|Autenticazione|  
|Non Windows|Kerberos Java pura|  
|Non Windows|SQL Server|  
|Non Windows|Autenticazione di Azure Active Directory|
|Windows|Kerberos Java pura|  
|Windows|SQL Server|
|Windows|Kerberos con backup NTLM|  
|Windows|NTLM|  
|Windows|Autenticazione di Azure Active Directory|  
  
**Il driver supporta Internet Protocol versione 6 (IPv6) indirizzi?**  
 Sì, il driver supporta l'utilizzo di indirizzi IPv6 con la raccolta delle proprietà di connessione e con la proprietà della stringa di connessione serverName. Per ulteriori informazioni, vedere [creazione dell'URL di connessione](../../connect/jdbc/building-the-connection-url.md).  
  
**Che cos'è il buffer adattivo?**  
 Il buffering adattivo è stato introdotto da Microsoft SQL Server 2005 JDBC Driver versione 1.2 ed è progettato per recuperare qualsiasi tipo di dati con valori di grandi dimensioni senza l'overhead dei cursori del server. La funzionalità di buffering adattivo di Microsoft SQL Server JDBC Driver fornisce una proprietà della stringa di connessione responseBuffering che può essere impostata su "adattiva" o "completa". A partire da JDBC Driver versione 2.0 il comportamento predefinito è "adattivo". In altre parole, per ottenere il comportamento del buffer adattivo in questa versione, l'applicazione non deve richiederlo in modo esplicito. Nella versione 1.2, tuttavia, la modalità di buffering predefinita è "completa" e l'applicazione deve richiedere la modalità di buffering adattivo in modo esplicito. Per ulteriori informazioni, vedere [utilizzando il buffer adattivo](../../connect/jdbc/using-adaptive-buffering.md) argomento e il blog. [Che cos'è il buffering adaptiveresponse e perché usarla?](http://go.microsoft.com/fwlink/?LinkId=111575)  
  
**Il pool di connessioni supporto driver?**  
 Il driver fornisce il supporto per il pool di connessioni Java Platform, Enterprise Edition 5 (Java EE 5). Il driver implementa le interfacce JDBC 3.0 necessarie per consentire al driver di partecipare a qualsiasi implementazione di pool di connessioni offerta dai fornitori di server applicazioni middleware. Il driver partecipa alle connessioni in pool in questi ambienti. Per ulteriori informazioni, vedere [utilizzando il pool di connessioni](../../connect/jdbc/using-connection-pooling.md). Il driver non fornisce una propria implementazione di pool, ma si basa su server applicazioni Java di terze parti.  
  
**È disponibile per il driver di supporto?**  
 Sono disponibili diverse opzioni di supporto. È possibile inviare una domanda o eseguire il nostro [repository GitHub](https://github.com/microsoft/mssql-jdbc) che viene monitorato da Microsoft. [Forum](http://go.microsoft.com/fwlink/?LinkID=246673) vengono monitorati da Microsoft, MVP e community. È anche possibile contattare il Supporto tecnico Microsoft. Il team di sviluppo potrebbe essere richiesto di riprodurre il problema di fuori di qualsiasi server applicazioni di terze parti. Se il problema non può essere riprodotto all'esterno dell'hosting ambiente contenitore Java, è necessario coinvolgere le terze parti in modo che il team può continuare assistere. Il team potrebbe essere anche richiesto di riprodurre il problema in un sistema operativo, ad esempio Windows, pertanto il problema può essere più supportato.  
  
**Il driver è certificato per l'utilizzo con qualsiasi server applicazioni di terze parti?**
Il driver è stato testato nei principali server applicazioni, inclusi IBM WebSphere e SAP NetWeaver.  
  
**Come attivare l'analisi**  
 Il driver supporta l'utilizzo della traccia (o registrazione) per semplificare la risoluzione dei problemi relativi all'utilizzo del driver JDBC nell'applicazione. Per abilitare l'utilizzo della traccia JAR sul lato client, il driver JDBC usa le API di registrazione in java.util.logging. Per ulteriori informazioni, vedere [traccia operazione Driver](../../connect/jdbc/tracing-driver-operation.md). Per informazioni sulla traccia XA sul lato server, vedere la pagina relativa alla [traccia di accesso ai dati in SQL Server](http://go.microsoft.com/fwlink/?LinkId=248705).  
  
**In cui è possibile scaricare le versioni precedenti del driver, ad esempio il driver JDBC di SQL Server 2000, 2005 driver 1.0, 1.1 o 1.2 driver?**  
 Queste versioni del driver non sono disponibili per il download perché non sono più supportate. È in continuo miglioramento il supporto della connettività Java. Di conseguenza, si consiglia che si lavora con la versione più recente di Microsoft JDBC driver.  
  
**Utilizzo di JRE 1.4. Il driver è compatibile con JRE 1.4?**  
 I clienti che usano prodotti SAP e richiedono il supporto di JRE 1.4 possono contattare [SAPService Marketplace](http://service.sap.com/) per ottenere Microsoft JDBC Driver 1.2.  
  
**Il driver può comunicare con gli algoritmi FIPS convalidati?**  
 Microsoft JDBC Driver non contiene algoritmi di crittografia. Se un cliente utilizza il sistema operativo, applicazioni e gli algoritmi JVM considerati accettabili da FIPS Federal Information Processing Standard () e configura il driver per l'utilizzo di tali algoritmi il driver utilizza solo gli algoritmi designati per comunicazione.  
  
 ## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
