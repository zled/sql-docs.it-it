---
title: Driver OLE DB per SQL Server | Documenti Microsoft
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
description: ''
ms.custom: ''
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: article
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 89e66fe2c61ae17a43e2a58071ba04374f33ea04
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="ole-db-driver-for-sql-server"></a>Driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

MSOLEDBSQL o il Driver OLE DB per SQL Server, è un termine che è stato usato in modo intercambiabile per fare riferimento al Driver OLE DB per SQL Server.

## <a name="different-incarnations-of-ole-db-drivers"></a>Rappresentazioni diverse del driver OLE DB

Esistono tre tipi distinti di provider Microsoft OLE DB per SQL Server.


### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1. Provider Microsoft OLE DB per SQL Server (SQLOLEDB)

Il [il Provider Microsoft OLE DB per SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) ancora fornito come parte di [Windows Data Access Components](https://msdn.microsoft.com/en-us/library/ms692897.aspx). Non è consigliabile utilizzare il driver per i nuovi sviluppi.


### <a name="2-sql-server-native-client-snac"></a>2. SQL Server Native Client (SNAC)

A partire da SQL Server 2005, il [SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) include un'interfaccia di provider OLE DB (SQLNCLI) e il provider OLE DB fornito con SQL Server 2005 tramite SQL Server 2017.

Era [deprecati nel 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) e non è consigliabile utilizzare il driver per i nuovi sviluppi.


### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3. Driver Microsoft OLE DB per SQL Server (MSOLEDBSQL)

OLE DB non è [annunciate come undeprecated in 2017](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/). Un nuovo rilascio pianificato è stato annunciato per 2018.

Il nuovo provider OLE DB viene chiamato il Driver OLE DB Microsoft per SQL Server (MSOLEDBSQL). Il nuovo provider verrà aggiornato con le funzionalità di server più recenti in futuro.

Informazioni sul Driver OLE DB per le funzionalità di SQL Server:

-   [Driver OLE DB per SQL Server Support for LocalDB](../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  

-   [Individuazione dei metadati](../oledb/features/metadata-discovery.md)  

-   [Supporto UTF-16 in OLE DB Driver per SQL Server](../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  

-   [Driver OLE DB per SQL Server Support for High Availability, Disaster Recovery](../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  

-   [Accesso alle informazioni di diagnostica nel log degli eventi estesi](../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

## <a name="see-also"></a>Vedere anche  
[Installare i Driver OLE DB per SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
 [Driver OLE DB per la funzionalità di SQL Server](../oledb/features/oledb-driver-for-sql-server-features.md )  
