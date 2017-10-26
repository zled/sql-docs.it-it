---
title: MSSQLSERVER_617 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 570073a75fd1a325837812aa0f75dba2e1a90902
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver617"></a>MSSQLSERVER_617
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|617|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|NODESHASH|  
|Testo del messaggio|Impossibile trovare nella tabella hash il descrittore per l'ID di oggetto %ld nel database con ID %d durante il tentativo di annullare l'hashing. Voce mancante in una tabella di lavoro. Eseguire nuovamente la query. Se viene utilizzato un cursore, chiuderlo e riaprirlo.|  
  
## <a name="explanation"></a>Spiegazione  
SQL Server non è in grado di trovare la tabella di lavoro per una voce specifica.  
  
## <a name="user-action"></a>Azione dell'utente  
  
1.  Se viene utilizzato un cursore, chiuderlo e riaprirlo.  
  
2.  Eseguire nuovamente la query.  
  

