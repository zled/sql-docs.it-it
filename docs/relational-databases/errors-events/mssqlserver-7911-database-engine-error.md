---
title: MSSQLSERVER_7911 | Microsoft Docs
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
- 7911 (Database Engine error)
ms.assetid: dd8390f3-0f77-4fb2-ba94-631a56e42bc6
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
robots: noindex,nofollow
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a263211de746ed459a1f76c1146671bb0f746301
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver7911"></a>MSSQLSERVER_7911
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|7911|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC2_REPAIR_PAGE_DEALLOCATED|  
|Testo del messaggio|Correzione: la pagina P_ID è stata deallocata all'oggetto con ID O_ID, indice con ID I_ID, partizione con ID PN_ID, unità allocazione con ID A_ID (tipo TYPE).|  
  
## <a name="explanation"></a>Spiegazione  
Si tratta di un messaggio informativo generato dall'istruzione REPAIR in cui viene indicato che una pagina è stata deallocata dalla matrice di slot a pagina singola di una mappa di allocazione degli indici (IAM, Index Allocation Map).  
  
## <a name="user-action"></a>Azione dell'utente  
Nessuno  
  

