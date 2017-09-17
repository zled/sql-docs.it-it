---
title: Connessione a SQL Server con il Driver JDBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94bcfbe3-f00e-4774-bda8-bb7577518fec
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1ebc9542e5683eb58c198745892916893f284822
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-to-sql-server-with-the-jdbc-driver"></a>Connessione a SQL Server con il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Uno degli aspetti più importanti che è possibile eseguire con il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] consiste nell'eseguire una connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database. Ogni interazione con il database viene eseguita tramite il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto, e poiché il driver JDBC ha un'architettura flat, quasi tutte le interessanti l'oggetto SQLServerConnection.  
  
 Se un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è in ascolto solo su una porta IPv6, impostare la proprietà di sistema Java.NET. preferipv6addresses per assicurarsi che IPv6 viene utilizzato invece di IPv4 per connettersi al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]:  
  
```  
System.setProperty("java.net.preferIPv6Addresses", "true");  
```  
  
 Negli argomenti di questa sezione viene descritto come creare e utilizzare una connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Creazione dell'URL di connessione](../../connect/jdbc/building-the-connection-url.md)|Viene descritto come creare un URL di connessione per la connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database. Viene illustrata anche la connessione a istanze denominate di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.|  
|[Impostazione delle proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md)|Vengono descritte le varie proprietà di connessione e come possono essere utilizzati quando ci si connette a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.|  
|[L'impostazione di proprietà dell'origine dati](../../connect/jdbc/setting-the-data-source-properties.md)|Viene descritto come utilizzare le origini dei dati in un ambiente Java EE (Java Platform, Enterprise Edition).|  
|[Utilizzo di una connessione](../../connect/jdbc/working-with-a-connection.md)|Descrive i vari modi in cui creare un'istanza di una connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.|  
|[Utilizzando pool di connessioni](../../connect/jdbc/using-connection-pooling.md)|Viene descritto come il driver JDBC supporta l'utilizzo del pool di connessioni.|  
|[Tramite il mirroring del Database &#40; JDBC &#41;](../../connect/jdbc/using-database-mirroring-jdbc.md)|Viene descritto il supporto del driver JDBC per l'utilizzo del mirroring del database.|  
|[Supporto del Driver JDBC per il ripristino di emergenza a disponibilità elevato](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)|Viene descritto come sviluppare un'applicazione che verrà connessa a un gruppo di disponibilità AlwaysOn.|  
|[Utilizza l'autenticazione integrata Kerberos per connettersi a SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)|Viene descritta un'implementazione Java per applicazioni di connettersi a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database utilizzando l'autenticazione integrata Kerberos.|  
|[Connessione a un database SQL di Azure](../../connect/jdbc/connecting-to-an-azure-sql-database.md)|Vengono descritti i problemi di connettività per i database in SQL Azure.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del Driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  