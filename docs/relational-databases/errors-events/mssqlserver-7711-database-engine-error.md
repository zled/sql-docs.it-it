---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 870b2060d5a43e3e8cfd3430e38ef95356d492ef
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver7711"></a>MSSQLSERVER_7711
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|7711|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PRT_RANGE_OVERLAP|  
|Testo del messaggio|L'opzione DATA_COMPRESSION è stata specificata più di una volta per la tabella o per l'indice o per una delle relative partizioni.|  
  
## <a name="explanation"></a>Spiegazione  
Si è verificato un errore nell'opzione DATA_COMPRESSION di una delle istruzioni seguenti:  
  
-   CREATE TABLE  
  
-   ALTER TABLE  
  
-   CREATE INDEX  
  
-   ALTER INDEX  
  
Se la tabella o l'indice indicato è partizionato, l'opzione DATA_COMPRESSION è stata elencata più volte per almeno una delle partizioni. Se la tabella o l'indice non è partizionato, l'opzione DATA_COMPRESSION è stata indicata più volte.  
  
## <a name="user-action"></a>Azione dell'utente  
Per una tabella o un indice partizionato, verificare che l'opzione DATA_COMPRESSION sia specificata solo una volta per ciascuna partizione. Per una tabella o un indice non partizionato, utilizzare l'opzione DATA_COMPRESSION solo una volta nell'istruzione.  
  
