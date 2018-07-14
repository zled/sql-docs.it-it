---
title: MSSQL_ENG020572 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020572 error
ms.assetid: 636566db-ffcf-4109-8c11-15b8c7cb9cd9
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 653aaa002ee37f7c7cdd3aeea7983486f35d1fcd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37188318"
---
# <a name="mssqleng020572"></a>MSSQL_ENG020572
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|20572|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|La sottoscrizione del Sottoscrittore '%s' dell'articolo '%s' della pubblicazione '%s' è stata reinizializzata dopo un errore di convalida.|  
  
## <a name="explanation"></a>Spiegazione  
 I dati nel Sottoscrittore sono stati convalidati in base a quelli nel server di pubblicazione e non corrispondono, pertanto la convalida non è stata eseguita. Quando è stato specificato che è necessario eseguire la convalida, è stata selezionata l'opzione che prevede la reinizializzazione di una sottoscrizione in caso di mancata convalida. La reinizializzazione di una sottoscrizione implica l'applicazione di un nuovo snapshot nel Sottoscrittore. Per ulteriori informazioni sulla convalida, vedere [Validate Replicated Data](validate-replicated-data.md).  
  
## <a name="user-action"></a>Azione dell'utente  
 I dati nel server di pubblicazione e nel Sottoscrittore corrisponderanno dopo l'applicazione del nuovo snapshot nel Sottoscrittore.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)  
  
  
