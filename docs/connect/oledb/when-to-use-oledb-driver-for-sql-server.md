---
title: Quando utilizzare OLE DB Driver per SQL Server | Documenti Microsoft
description: Quando utilizzare Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 250fdffb328fe781279819ae2e856624388122bb
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>Quando utilizzare OLE DB Driver per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server è una tecnologia che è possibile utilizzare per accedere ai dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.  Per una descrizione delle tecnologie di accesso ai dati diversi, vedere [Mappa stradale tecnologie di accesso ai dati](http://go.microsoft.com/fwlink/?LinkID=179186)  
  
 Quando si decide se utilizzare il Driver OLE DB per SQL Server come la tecnologia di accesso ai dati dell'applicazione, è necessario considerare diversi fattori.  
  
 Per le nuove applicazioni, se si utilizza un linguaggio di programmazione gestito, come Microsoft Visual C# o Visual Basic, e si desidera accedere alle nuove caratteristiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario utilizzare il provider di dati .NET Framework per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], incluso in .NET Framework.  
  
 Se si sviluppa un'applicazione basata su COM e si desidera accedere alle nuove funzionalità introdotte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è consigliabile utilizzare Driver OLE DB per SQL Server. Se non è necessario accedere alle nuove caratteristiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile continuare a utilizzare Windows Data Access Components (WDAC).  
  
 Per le applicazioni OLE DB esistente, il problema principale è dato dalla necessità di accedere alle nuove funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In caso di un'applicazione obsoleta per la quale non sono richieste le nuove funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile continuare a utilizzare WDAC. Tuttavia, se si desidera accedere alle nuove funzionalità, ad esempio il [tipo di dati xml](../../t-sql/xml/xml-transact-sql.md), è consigliabile utilizzare Driver OLE DB per SQL Server.  
  
 Entrambi Driver OLE DB per SQL Server che MDAC supportano l'isolamento transazione sottoposta a commit utilizzando delle versioni delle righe, ma solo Driver OLE DB per SQL Server supporta l'isolamento delle transazioni read. In termini di programmazione, l'isolamento delle transazioni Read Committed mediante il controllo delle versioni delle righe equivale a una transazione Read Committed.  
  
 Per informazioni sulle differenze tra il Driver OLE DB per SQL Server e MDAC, vedere [aggiornamento di un'applicazione al Driver OLE DB per SQL Server da MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per SQL Server](../oledb/oledb-driver-for-sql-server.md)     
 [Procedure per OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
