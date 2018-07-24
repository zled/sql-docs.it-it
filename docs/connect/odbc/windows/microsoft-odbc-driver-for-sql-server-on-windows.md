---
title: Installare Microsoft ODBC Driver for SQL Server in Windows
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b10cfc22-6a2c-4707-a456-0dcec317982b
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5d818e4ce5c267432e6e456e11720f546ebaa19
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38047439"
---
# <a name="microsoft-odbc-driver-for-sql-server-on-windows"></a>Microsoft ODBC Driver for SQL Server in Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sono i driver ODBC autonomi che forniscono un'API application programming interface () che implementa le interfacce ODBC standard in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].

Il driver ODBC per SQL Server consente di creare nuove applicazioni. È inoltre possibile aggiornare le applicazioni precedenti che attualmente usano un driver ODBC meno recente. Il driver ODBC per SQL Server supporta le connessioni a database SQL di Azure, Azure SQL Data Warehouse, SQL Server 2017, SQL Server 2016, SQL Server 2014 R2, SQL Server 2012 e SQL Server 2008.  

## <a name="summary"></a>Riepilogo

| Versione       | Funzionalità supportate      |
| ------------- |---------------| 
| Microsoft ODBC Driver 17 per SQL Server | <ul><li>Supporto per Always Encrypted per l'API BCP</li><li>Nuovo attributo di stringa di connessione UseFMTONLY fa in modo che i driver per l'uso di metadati legacy in casi particolari che richiedono le tabelle temporanee</li>
| Microsoft ODBC Driver 13.1 per SQL Server     | <ul><li>Crittografia sempre attiva</li><li>Configurare l'autenticazione di AD</li><li>Gruppi di disponibilità AlwaysOn</li></ul>   | 
| Microsoft ODBC Driver 13 per SQL Server      | <ul><li>Internationalized Domain Name (IDN)</li></ul> |
| Microsoft ODBC Driver 11 per SQL Server | <ul><li>Pool di connessioni compatibile con il driver</li><li>Resilienza della connessione</li><li>Esecuzione asincrona (metodo di polling)</li></ul> |    

## <a name="documentation"></a>Documentazione  
Questa documentazione per Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] include:  
  
-   [Note sulla versione](../../../connect/odbc/windows/release-notes.md)  
-   [Funzionalità di Microsoft ODBC Driver for SQL Server in Windows](../../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)  
-   [Requisiti di sistema, installazione e file del driver](../../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)  
-   [Pool di connessioni compatibile con il driver nel driver ODBC per SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)  
-   [Asynchronous Execution &#40;Notification Method&#41; Sample (Esempio di esecuzione asincrona - metodo di notifica)](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)  
-   [Resilienza di connessione nel driver ODBC di Windows](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)  
-   [Utilizzo di Always Encrypted con il JDBC Driver](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
-   [Uso di Azure Active Directory con ODBC Driver](../../../connect/odbc/using-azure-active-directory.md) 
-   [Uso della stringa di connessione TransparentNetworkIPResolution](../../../connect/odbc/using-transparent-network-ip-resolution.md)   

## <a name="community"></a>Community  
- [Blog del team di Microsoft ODBC Driver for SQL Server](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [Forum di accesso ai dati di SQL Server](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
  
## <a name="see-also"></a>Vedere anche  
- [Informazioni su SQL Server Native Client](https://msdn.microsoft.com/sqlserver/ff658532.aspx)   
- [Compilazione di applicazioni con SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)   
- [Domande frequenti su SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937707.aspx)   
- [Guida di riferimento per programmatori ODBC](../../../odbc/reference/odbc-programmer-s-reference.md)   
- [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
