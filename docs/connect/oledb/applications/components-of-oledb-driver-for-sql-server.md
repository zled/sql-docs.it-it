---
title: Componenti di Driver OLE DB per SQL Server | Documenti Microsoft
description: Componenti di Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 982790c72cd4179c78305ac76bf7178b8af80896
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Componenti di Driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server contiene i componenti seguenti:  

|Componente|Description|  
|---------------|-----------------|  
|msoledbsql.dll|Il file di libreria a collegamento dinamico (DLL) che contiene tutti i Driver OLE DB per la funzionalità di SQL Server.|  
|msoledbsqlr.rll|File di risorse associato per il Driver OLE DB per la libreria di SQL Server.|   
|msoledbsql.h|Il Driver OLE DB per il file di intestazione di SQL Server che contiene tutte le nuove definizioni necessarie per utilizzare il Driver OLE DB per SQL Server. Questo file di intestazione sostituisce il file di intestazione SQLOLEDB. h.<br /><br /> Nota: È possibile fare riferimento a msoledbsql.h e SQLOLEDB. h nello stesso programma, purché venga definito prima SQLOLEDB. h.|  
|msoledbsql.lib|Il file di libreria necessario per chiamare direttamente il **bcp** funzioni di utilità che fanno parte del Driver OLE DB per SQL Server.<br /><br /> Nota: Se si fa riferimento il file msoledbsql.lib nel codice di programmazione, è necessario assicurarsi che il file msoledbsql.dll sia nel proprio percorso di sistema e nel percorso di sistema di utenti che utilizzano l'applicazione.|  

## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con il driver OLE DB per SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
