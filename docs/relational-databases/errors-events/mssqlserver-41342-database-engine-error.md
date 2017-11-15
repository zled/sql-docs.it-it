---
title: MSSQLSERVER_41342 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 8af7be1ae4b0a1cbba1b56bd9644d6b33cbdd8bf
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver41342"></a>MSSQLSERVER_41342
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41342|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|HK_HW_NOT_SUPPORTED|  
|Testo del messaggio|Il modello del processore del sistema non supporta la creazione di *costrutto*. Questo errore si verifica in genere nei processori meno recenti. Per informazioni sui modelli supportati, vedere la documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="explanation"></a>Spiegazione  
Per le tabelle con ottimizzazione per la memoria è richiesto un modello di processore che supporta le operazioni di scambio e confronto atomiche su valori a 128 bit, che richiedono l'istruzione di assembly CMPXCHG16B. Alcuni modelli di processore AMD meno recenti non supportano l'istruzione CMPXCHG16B. Inoltre, alcuni ambienti di virtualizzazione non consentono l'utilizzo di questa istruzione per impostazione predefinita.  
  
## <a name="user-action"></a>Azione dell'utente  
Aggiornare il processore. Se il processore supporta l'istruzione e si sta eseguendo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in una macchina virtuale, modificare la configurazione per supportare l'istruzione CMPXCHG16B.  
  
## <a name="see-also"></a>Vedere anche  
[OLTP in memoria &#40;ottimizzazione per la memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
