---
title: MSSQLSERVER_41302 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41302 (Database Engine error)
ms.assetid: 01e75618-afec-4232-ba68-93ab7bc31003
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 115bcedd799d0e8d66d959b84af19d2c688d2485
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428710"
---
# <a name="mssqlserver41302"></a>MSSQLSERVER_41302
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41302|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|WRITE_WRITE_CONFLICT|  
|Testo del messaggio|Tentativo da parte della transazione corrente di aggiornare un record che è già stato aggiornato dopo l'avvio della transazione. La transazione è stata interrotta.|  
  
## <a name="explanation"></a>Spiegazione  
 La transazione ha rilevato un conflitto di scrittura/scrittura e l'istruzione è stata terminata.  
  
## <a name="user-action"></a>Azione dell'utente  
 Rieseguire l'operazione in una transazione diversa in un secondo momento. Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Vedere anche  
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
