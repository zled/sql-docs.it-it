---
title: Microsoft ODBC Driver for SQL Server in Windows | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b10cfc22-6a2c-4707-a456-0dcec317982b
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: be37bf73c0fe662b15c8ad26210ed243b5ca317c
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="microsoft-odbc-driver-for-sql-server-on-windows"></a>Microsoft ODBC Driver for SQL Server in Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Microsoft ODBC Driver 13.1, 13 / 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sono driver ODBC autonomi che forniscono un'API application programming interface () che implementa le interfacce ODBC standard in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].

Il Driver ODBC di Microsoft per SQL Server consente di creare nuove applicazioni. È inoltre possibile aggiornare le applicazioni precedenti che attualmente usano un driver ODBC meno recente. Il Driver ODBC per SQL Server supporta le connessioni al Database SQL di Azure, Azure SQL Data Warehouse, SQL Server 2016, SQL Server 2014, SQL Server 2012, SQL Server 2008 R2, SQL Server 2008 e SQL Server 2005.  

## <a name="summary"></a>Riepilogo

| Versione       | Funzionalità supportate      |
| ------------- |---------------| 
| Microsoft ODBC Driver 13.1 for SQL Server     | <ul><li>Crittografia sempre attiva</li><li>Autenticazione di Azure AD</li><li>Gruppi di disponibilità AlwaysOn</li></ul>   | 
| Microsoft ODBC Driver 13 for SQL Server      | <ul><li>Internationalized Domain Name (IDN)</li></ul> |
| Microsoft ODBC Driver 11 per SQL Server | <ul><li>Pool di connessioni compatibile con il driver</li><li>Resilienza della connessione</li><li>Esecuzione asincrona (metodo di Polling)</li></ul> |    

## <a name="documentation"></a>Documentazione  
Questa documentazione per Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] include:  
  
-   [Note sulla versione](../../../connect/odbc/windows/release-notes.md)  
-   [Funzionalità di Microsoft ODBC Driver for SQL Server in Windows](../../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)  
-   [Requisiti di sistema, installazione e file del driver](../../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)  
-   [Pool di connessioni compatibile con il driver nel driver ODBC per SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)  
-   [Asynchronous Execution &#40;Notification Method&#41; Sample (Esempio di esecuzione asincrona - metodo di notifica)](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)  
-   [Resilienza di connessione nel driver ODBC di Windows](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)  
-   [Utilizzo di Always Encrypted con il Driver ODBC](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
-   [Utilizzo di Azure Active Directory con il Driver ODBC](../../../connect/odbc/using-azure-active-directory.md) 
-   [Utilizzando la risoluzione IP di rete Transparent](../../../connect/odbc/using-transparent-network-ip-resolution.md)   

## <a name="community"></a>Community  
- [Blog del team di Microsoft ODBC Driver for SQL Server](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [Forum di accesso ai dati di SQL Server](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
  
## <a name="see-also"></a>Vedere anche  
- [Informazioni su SQL Server Native Client](https://msdn.microsoft.com/sqlserver/ff658532.aspx)   
- [Creazione di applicazioni con SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)   
- [Domande frequenti su SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937707.aspx)   
- [ODBC Programmer's Reference (Guida di riferimento per programmatori ODBC)](../../../odbc/reference/odbc-programmer-s-reference.md)   
- [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  

