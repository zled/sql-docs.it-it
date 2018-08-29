---
title: Creazione di un set di righe con IOpenRowset | Microsoft Docs
description: Creazione di un set di righe con IOpenRowset interfaccia del Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 08ed7ed1d56ccd5ef6887387ea9ba53eed2c5df9
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032081"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Creazione di un set di righe con IOpenRowset
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server supporta il **IOpenRowset:: OPENROWSET** metodo con le restrizioni seguenti:  
  
-   Una vista o una tabella di base deve essere specificata in una struttura del database (DBID) a cui punta il parametro *pTableID*.  
  
-   Il membro DBID *eKind* deve indicare DBKIND_NAME.  
  
-   Il membro DBID *uName* deve specificare il nome di una vista o di una tabella di base esistente come stringa di caratteri Unicode.  
  
-   Il parametro *pIndexID* di **OpenRowset** deve essere NULL.  
  
 Il set di risultati di **IOpenRowset::OpenRowset** contiene un solo set di righe. I set di risultati che contengono un solo set di righe possono essere supportati dai cursori di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il supporto del cursore consente allo sviluppatore di utilizzare i meccanismi di concorrenza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
