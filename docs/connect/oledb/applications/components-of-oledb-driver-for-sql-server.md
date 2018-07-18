---
title: Componenti di Driver OLE DB per SQL Server | Documenti Microsoft
description: Componenti di Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 78b72796de5aa4ac2fb9bc0793f98365b7d8281e
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611686"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Componenti di Driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server contiene i componenti seguenti:  

|Componente|Description|  
|---------------|-----------------|  
|msoledbsql.dll|Il file di libreria a collegamento dinamico (DLL) che contiene tutti i Driver OLE DB per la funzionalità di SQL Server.|  
|msoledbsqlr.rll|File di risorse associato per il Driver OLE DB per la libreria di SQL Server.|   
|msoledbsql.h|Il Driver OLE DB per il file di intestazione di SQL Server che contiene tutte le nuove definizioni necessarie per utilizzare il Driver OLE DB per SQL Server. Questo file di intestazione sostituisce il file di intestazione SQLOLEDB. h.<br /><br /> Nota: È possibile fare riferimento a msoledbsql.h e SQLOLEDB. h nello stesso programma, purché venga definito prima SQLOLEDB. h.|  
|msoledbsql.lib|Il file di libreria necessario per chiamare direttamente il [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) funzione che fa parte del Driver OLE DB per SQL Server.<br /><br /> Nota: Se si fa riferimento il file msoledbsql.lib nel codice di programmazione, è necessario assicurarsi che il file msoledbsql.dll sia nel proprio percorso di sistema e nel percorso di sistema di utenti che utilizzano l'applicazione.|  

## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con il driver OLE DB per SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
