---
title: MSSQLSERVER_17883 | Microsoft Docs
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
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6228ef52269a304a5e72a3ff3bc50b915ab372f4
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver17883"></a>MSSQLSERVER_17883
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17883|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SRV_SCHEDULER_NONYIELDING|  
|Testo del messaggio|Processo %ld:%ld:%ld (0x%lx) È possibile che il thread di lavoro 0x%p non ceda il controllo all'utilità di pianificazione %ld. Durata creazione thread: %I64d. Utilizzo CPU thread (circa): kernel %I64d ms, utente %I64d ms. Utilizzo processo %d%%. Inattività del sistema: %d%%. Intervallo: %I64d ms.|  
  
## <a name="explanation"></a>Spiegazione  
Indica la presenza di un possibile problema relativo a un thread che non cede il controllo a un'utilità di pianificazione.  Il problema potrebbe essere causato da un bug in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o da un numero di cicli insufficienti per l'esecuzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  L'errore potrebbe risolversi qualora il thread ceda eventualmente il controllo.  
  
## <a name="user-action"></a>Azione dell'utente  
Se il carico sul sistema è eccessivo, ridurlo. In caso contrario, contattare il Servizio Supporto Tecnico Clienti Microsoft.  
  
