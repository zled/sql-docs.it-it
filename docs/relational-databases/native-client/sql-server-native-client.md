---
title: SQL Server Native Client | Documenti Microsoft
ms.date: 04/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
caps.latest.revision: "43"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7474d620d96880396e8fe7dc44e55b4cdcf7f440
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="sql-server-native-client"></a>SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

SNAC o SQL Server Native Client, è un termine utilizzato in modo intercambiabile per fare riferimento ai driver ODBC e OLE DB per SQL Server. 

**Per ulteriori informazioni e per scaricare i driver ODBC SNAC, visitare [ciclo di vita SNAC illustrato](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).**

Per ulteriori informazioni sul Driver ODBC per SQL Server, vedere [Microsoft ODBC Driver for SQL Server in Windows](https://msdn.microsoft.com/library/jj730314(v=sql.110).aspx).  Vedere anche [introdurre i nuovi driver ODBC di Microsoft per SQL Server](https://blogs.msdn.microsoft.com/sqlnativeclient/2013/01/23/introducing-the-new-microsoft-odbc-drivers-for-sql-server/), e [ODBC Driver 13.1 for SQL Server rilasciato](https://blogs.technet.microsoft.com/dataplatforminsider/2016/08/03/odbc-driver-13-1-for-sql-server-released/).  
  
 Informazioni sul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funzionalità Native Client rilasciata con [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], l'ultima versione disponibile di SQL Server native Client: 
  
-   [Supporto di SQL Server Native Client per Local DB](../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)  
  
-   [Individuazione dei metadati](../../relational-databases/native-client/features/metadata-discovery.md)  
  
-   [Supporto di UTF-16 in SQL Server Native Client 11.0](../../relational-databases/native-client/features/utf-16-support-in-sql-server-native-client-11-0.md)  
  
-   [Supporto SQL Server Native Client per il ripristino di emergenza a disponibilità elevato](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [Accesso alle informazioni di diagnostica nel log degli eventi estesi](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)  
  
ODBC in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client supporta tre funzionalità aggiunte a ODBC standard in Windows 7 SDK:  
  
-   Esecuzione asincrona nelle operazioni correlate alla connessione. Per ulteriori informazioni, vedere [esecuzione asincrona](http://go.microsoft.com/fwlink/?LinkID=191493).  
  
-   Estendibilità del tipo di dati C. Per ulteriori informazioni, vedere [tipi di dati C in ODBC](http://go.microsoft.com/fwlink/?LinkID=191495).  
  
     Per supportare questa funzionalità in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, può restituire SQLGetDescField **SQL_C_SS_TIME2** (per **ora** tipi) o **SQL_C_SS_TIMESTAMPOFFSET** (per **datetimeoffset**) anziché **SQL_C_BINARY**, se l'applicazione utilizza ODBC 3.8. Per ulteriori informazioni, vedere [supporto tipo di dati per ODBC Date e i miglioramenti di tempo](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md).  
  
-   La chiamata **SQLGetData** con un buffer di piccole dimensioni più volte per recuperare un valore di parametro di grandi dimensioni. Per ulteriori informazioni, vedere [il recupero dei parametri di Output tramite SQLGetData](http://go.microsoft.com/fwlink/?LinkID=191494).  
  
 Negli argomenti seguenti vengono descritte le modifiche nel comportamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   Quando si chiama **ICommandWithParameters:: SetParameterInfo**, il valore passato al *pwszName* parametro deve essere un identificatore valido. Per ulteriori informazioni, vedere [ICommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md).  
  
-   **SQLDescribeParam** restituirà sempre un valore conforme specifica di ODBC. Per ulteriori informazioni, vedere [SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md).  
  
-   [Modifica del comportamento del driver ODBC quando si gestiscono le conversioni di caratteri](../../relational-databases/native-client/features/odbc-driver-behavior-change-when-handling-character-conversions.md)  
  
## <a name="see-also"></a>Vedere anche  
[Installare SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 [Funzionalità di SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
