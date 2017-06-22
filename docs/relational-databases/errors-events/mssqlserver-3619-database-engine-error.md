---
title: MSSQLSERVER_3619 | Microsoft Docs
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
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f487685e727f9f5ccf3862ac62cf0f1e21fb78ea
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver3619"></a>MSSQLSERVER_3619
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|3619|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SYS_NOLOG|  
|Testo del messaggio|Impossibile scrivere un record di checkpoint nel database con ID %d perché nel log non è disponibile spazio. Rivolgersi all'amministratore di sistema per troncare il log o per allocare più spazio per i file dei log del database.|  
  
## <a name="explanation"></a>Spiegazione  
Lo spazio nel log delle transazioni è esaurito.  
  
## <a name="user-action"></a>Azione dell'utente  
Troncare il log per liberare spazio oppure allocare ulteriore spazio per il log. Per ulteriori informazioni, vedere "Risoluzione dei problemi relativi a un log delle transazioni pieno (Errore 9002)" nella documentazione online di SQL Server.  
  

