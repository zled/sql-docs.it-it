---
title: Criteri di supporto per Driver OLE DB per SQL Server | Documenti Microsoft
description: Criteri di supporto per il Driver OLE DB per SQL Server
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 1c3cac083215c2af00142a17d6ad8960dfe760ad
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Criteri di supporto per Driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Questo articolo viene illustrato come le varie componenti di accesso ai dati possono essere utilizzati con il Driver OLE DB per SQL Server.  

## <a name="server-support"></a>Supporto server  
 Il Driver OLE DB per SQL Server supporta le connessioni a [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)],[!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)], [!INCLUDE[ssSQL17](../../../includes/sssql17-md.md)], e [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].

## <a name="supported-operating-system-versions"></a>Versioni di sistema operativo supportate  
 Nella tabella seguente sono elencati i sistemi operativi supportati Driver OLE DB per SQL Server.  

|Sistemi operativi supportati|  
|--------------------------------------|---------------------------------|   
|Microsoft Windows 8.1<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012<br /><br />Microsoft Windows Server 2012 R2<br /><br />Microsoft Windows Server 2016|  

## <a name="ado-support-policies"></a>Criteri di supporto ADO  
 Le applicazioni ADO possono utilizzare il provider OLE DB SQLOLEDB incluso in Windows se non richiedono alcuna funzionalità di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva.  

 Le applicazioni ADO possono utilizzare il Driver OLE DB per SQL Server, ma se a tale scopo devono specificare `DataTypeCompatibility=80` nelle stringhe di connessione. Se nelle stringhe di connessione è presente `DataTypeCompatibility=80`, sono disponibili solo le funzionalità di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  

## <a name="ole-db-support-policies"></a>Criteri di supporto OLE DB  
Le applicazioni possono utilizzare il provider OLE DB (SQLOLEDB) incluso con il sistema operativo Windows. Tuttavia, che è in modalità di manutenzione e non viene più aggiornata. È consigliabile utilizzare il Driver OLE DB per SQL Server (MSOLEDBSQL).

## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con il driver OLE DB per SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
