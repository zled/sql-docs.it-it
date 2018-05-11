---
title: MSSQLSERVER_3937 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6f02486a0a113f2e589a5f17d40344c374c1d853
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver3937"></a>MSSQLSERVER_3937
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|MSSQLSERVER|  
|ID evento|3937|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|XACT_FILESTREAM_ROLLBACK_ERROR|  
|Testo del messaggio|Durante il rollback di una transazione, si è verificato un errore nel tentativo di notificare l'esecuzione del rollback di una transazione al driver del filtro FILESTREAM. Codice di errore: 0x%0x.|  
  
## <a name="explanation"></a>Spiegazione  
Durante l'invio di una notifica di esecuzione del rollback di una transazione, è stato restituito un errore dal driver RsFx, probabilmente a causa di risorse insufficienti. Questa situazione potrebbe provocare una piccola perdita di memoria nel driver del filtro RsFx, in cui tuttavia verrà liberato spazio quando il processo sqlservr.exe che creato la transazione termina.  
  
## <a name="user-action"></a>Azione dell'utente  
