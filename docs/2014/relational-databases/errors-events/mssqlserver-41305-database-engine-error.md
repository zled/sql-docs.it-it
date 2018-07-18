---
title: MSSQLSERVER_41305 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41305 (Database Engine error)
ms.assetid: a96e5083-ff97-4003-a900-07942454151d
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 499ec2d1630f74a329a5f72a1bc6a784463ec2a4
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415880"
---
# <a name="mssqlserver41305"></a>MSSQLSERVER_41305
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41305|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|HK_TX_COMMIT_RR_VALIDATION|  
|Testo del messaggio|Impossibile eseguire il commit della transazione corrente a causa di un errore di convalida di lettura ripetibile.|  
  
## <a name="explanation"></a>Spiegazione  
 La transazione ha rilevato un errore di convalida ed è stata eliminata.  
  
 Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="user-action"></a>Azione dell'utente  
 Ripetere la transazione non riuscita.  
  
## <a name="see-also"></a>Vedere anche  
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
