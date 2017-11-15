---
title: MSSQLSERVER_5237 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: eafae8fdc25989aaec7ea987d5e72ed7a9221e93
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver5237"></a>MSSQLSERVER_5237
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|5237|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE|  
|Testo del messaggio|Controllo DBCC per il set di righe non riuscito per l'oggetto 'NAME' (ID di oggetto O_ID) a causa di un errore interno della query.|  
  
## <a name="explanation"></a>Spiegazione  
Si è verificato un errore interno poiché DBCC non è in grado di eseguire la query per controllare viste indicizzate.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire di nuovo il comando DBCC.  
  
