---
title: Individuazione dei metadati | Documenti Microsoft
description: Individuazione dei metadati nel Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5990632392ec4656af7f655fcbd1b19b29346066
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="metadata-discovery"></a>Individuazione dei metadati
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  I miglioramenti apportati all'individuazione dei metadati in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] consente il Driver OLE DB per le applicazioni di SQL Server verificare che la colonna o parametro metadati restituiti dall'esecuzione di una query sono identici a o compatibili con il formato dei metadati specificato prima di l'esecuzione della query. Se i metadati restituiti dopo l'esecuzione di una query non sono compatibili con il formato dei metadati specificato prima dell'esecuzione della query, viene generato un errore.  
  
 In bcp e dalle interfacce IBCPSession e IBCPSession2, è ora possibile specificare un ritardo lettura (individuazione dei metadati ritardata) per evitare l'individuazione dei metadati per operazioni di query. In questo modo, è possibile migliorare le prestazioni ed eliminare gli errori di individuazione dei metadati.  
  
 Se si sviluppa un'applicazione utilizzando il Driver OLE DB per SQL Server ma si connette a una versione server precedente a [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], funzionalità corrisponderà alla versione del server di individuazione dei metadati.  
  
## <a name="remarks"></a>Osservazioni   
 Le funzioni membro OLE DB seguenti sono state migliorate in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] per garantire una migliore individuazione dei metadati:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters:: GetParameterInfo (vedere [ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md) per altre informazioni)  
  
 Si verifica anche un miglioramento delle prestazioni quando si specifica il formato dei metadati utilizzando IBCPSession::BCPSetBulkMode  
  
 L'individuazione dei metadati migliorata in Driver OLE DB per SQL Server è possibile grazie all'aggiunta di due stored procedure in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per la funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
