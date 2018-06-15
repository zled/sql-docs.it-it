---
title: MSSQLSERVER_17887 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 53c67b1050c33addce50755f91218bd8a74e0641
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34318512"
---
# <a name="mssqlserver17887"></a>MSSQLSERVER_17887
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17887|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SRV_IO_COMP_LISTENER_NONYIELDING|  
|Testo del messaggio|Listener completamento I/O (0x%lx) È possibile che il thread di lavoro 0x%p non ceda la precedenza del nodo %ld. Utilizzo CPU (circa): kernel %I64d ms, utente %I64d ms, intervallo: %I64d.|  
  
## <a name="explanation"></a>Spiegazione  
Indica l'esistenza di un possibile problema con il Listener porta completamento I/O sul nodo specificato durante l'esecuzione della routine Completamento I/O per un evento di lettura/scrittura di rete. Questo errore non viene più visualizzato quando viene restituito il Listener della porta di completamento I/O in seguito all'esecuzione della routine Completamento I/O.  
  
## <a name="user-action"></a>Azione dell'utente  
Contattare il Servizio Supporto Tecnico Microsoft.  
  
