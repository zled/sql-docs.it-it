---
title: MSSQLSERVER_611 | Microsoft Docs
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
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b96bc69d694f4831086804cec2fe655c113e9d89
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver611"></a>MSSQLSERVER_611
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|611|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|VAR_SIZE_TOO_BIG|  
|Testo del messaggio|Impossibile inserire o aggiornare una riga perché le dimensioni di colonna variabili totali, incluso l'overhead, superano il limite di %d byte.|  
  
## <a name="explanation"></a>Spiegazione  
Le dimensioni di colonna variabili totali sono maggiori del limite consentito dallo schema. L'errore 611 viene restituito quando la colonna variabili supera il limite nel case fisso, se il formato di archiviazione vardecimal è abilitato, o quando le dimensioni della colonna variabili superano il limite consentito in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per un record di dati compresso.  
  
## <a name="user-action"></a>Azione dell'utente  
Ridurre le dimensioni del record.  
  

