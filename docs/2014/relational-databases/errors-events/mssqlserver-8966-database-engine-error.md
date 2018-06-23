---
title: MSSQLSERVER_8966 | Microsoft Docs
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
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0db9faf0217e8f0d352f92547b5ba6c31631e64e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169674"
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
  
  