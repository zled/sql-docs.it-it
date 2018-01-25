---
title: Creazione di un set di righe con IOpenRowset | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
caps.latest.revision: "30"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d82035e5996bbab2fe95f2379771b4b9cb60202d
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Creazione di un set di righe con IOpenRowset
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta il **IOpenRowset:: OPENROWSET** (metodo) con le restrizioni seguenti:  
  
-   Una tabella di base o una vista deve essere specificato in un database (DBID) ID struttura che la *pTableID* punta al parametro.  
  
-   Il DBID *eKind* membro deve indicare DBKIND_NAME.  
  
-   Il DBID *uName* membro deve specificare il nome di una tabella di base esistente o una vista come una stringa di caratteri Unicode.  
  
-   Il *pIndexID* parametro di **OpenRowset** deve essere NULL.  
  
 Il set di risultati di **IOpenRowset:: OPENROWSET** contiene un singolo set di righe. Set di risultati che contengono un singolo set di righe possono essere supportati da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursori. Il supporto del cursore consente allo sviluppatore di utilizzare i meccanismi di concorrenza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
