---
title: MSSQLSERVER_611 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fc1a8b3bc8f492e73b543ce7551dfba52a1dbd55
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055693"
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
  
  