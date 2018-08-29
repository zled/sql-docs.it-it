---
title: Risultati dei messaggi SQL Server | Microsoft Docs
description: risultati dei messaggi di SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: e13ec74572e04e210b312e19d1e04aa1423d26db
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028838"
---
# <a name="sql-server-message-results"></a>Risultati dei messaggi di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le istruzioni [!INCLUDE[tsql](../../../includes/tsql-md.md)] seguenti non generano set di righe del driver OLE DB per SQL Server o un conteggio delle righe interessate durante l'esecuzione:  
  
-   PRINT  
  
-   RAISERROR con gravità minore o uguale a 10  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Queste istruzioni restituiscono uno o più messaggi informativi o determinano la restituzione da parte di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] di messaggi informativi in sostituzione dei risultati del conteggio o del set di righe. In caso di esecuzione, il Driver OLE DB per SQL Server restituisce S_OK e i messaggi sono disponibili per il Driver OLE DB per il consumer di SQL Server.  
  
 Il Driver OLE DB per SQL Server restituisce S_OK e include uno o più messaggi informativi disponibili in seguito all'esecuzione di molte [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzioni o l'esecuzione del consumer di un Driver OLE DB per la funzione membro di SQL Server.  
  
 Il consumer del driver OLE DB per SQL Server che consente la specifica dinamica del testo della query deve controllare le interfacce di errore dopo l'esecuzione di ogni funzione membro, indipendentemente dal valore del codice restituito, dalla presenza o dall'assenza di un riferimento all'interfaccia **IRowset** o **IMultipleResults** restituito o di un conteggio delle righe interessate.  
  
## <a name="see-also"></a>Vedere anche  
 [errori](../../oledb/ole-db-errors/errors.md)  
  
  
