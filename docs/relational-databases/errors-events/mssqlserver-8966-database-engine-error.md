---
title: MSSQLSERVER_8966 | Microsoft Docs
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
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4c93290eaf142f7048458d9e4a18d12bc70e028b
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver8966"></a>MSSQLSERVER_8966
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|8966|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC3_FAILED_TO_READ_AND_LATCH_PAGE|  
|Testo del messaggio|Impostare leggere e impostare un latch nella pagina P_ID con tipo di latch TYPE. Impossibile eseguire OPERATION.|  
  
## <a name="explanation"></a>Spiegazione  
L'operazione di lettura della pagina non è stata eseguita oppure non è stato possibile impostare un latch in una pagina PFS o GAM. È possibile che nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] siano segnalati timeout del latch o altri messaggi associati.  
  
## <a name="user-action"></a>Azione dell'utente  
Controllare il log degli errori di SQL Server per esaminare i messaggi contenuti e risolvere gli errori.  
  

