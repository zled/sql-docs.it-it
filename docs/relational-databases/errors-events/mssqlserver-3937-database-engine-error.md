---
title: MSSQLSERVER_3937 | Microsoft Docs
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
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8f40def8cedfcdd2a090941fb2dc8a6547a2d766
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver3937"></a>MSSQLSERVER_3937
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|MSSQLSERVER|  
|ID evento|3937|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|XACT_FILESTREAM_ROLLBACK_ERROR|  
|Testo del messaggio|Durante il rollback di una transazione, si è verificato un errore nel tentativo di notificare l'esecuzione del rollback di una transazione al driver del filtro FILESTREAM. Codice di errore: 0x%0x.|  
  
## <a name="explanation"></a>Spiegazione  
Durante l'invio di una notifica di esecuzione del rollback di una transazione, è stato restituito un errore dal driver RsFx, probabilmente a causa di risorse insufficienti. Questa situazione potrebbe provocare una piccola perdita di memoria nel driver del filtro RsFx, in cui tuttavia verrà liberato spazio quando il processo sqlservr.exe che creato la transazione termina.  
  
## <a name="user-action"></a>Azione dell'utente  

