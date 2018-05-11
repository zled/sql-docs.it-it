---
title: MSSQLSERVER_5554 | Microsoft Docs
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
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 496718ec066f690ddd6e14e9937e356b40ef819b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver5554"></a>MSSQLSERVER_5554
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|MSSQLSERVER|  
|ID evento|5554|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|FS_MINIVER_OVERFLOW|  
|Testo del messaggio|È stato raggiunto il limite massimo di versioni totali per un singolo supportato dal file system.|  
  
## <a name="explanation"></a>Spiegazione  
In scenari MARS (Multiple Active Result Set) o con presenza di trigger, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa la miniversione specificata dal sistema operativo.  
  
## <a name="user-action"></a>Azione dell'utente  
Tentare di evitare aggiornamenti ripetuti ai dati nella stessa transazione.  
  
