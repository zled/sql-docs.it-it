---
title: MSSQLSERVER_1461 | Microsoft Docs
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
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: db041bd22b068dc43bc922003675f0cece338aba
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver1461"></a>MSSQLSERVER_1461
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1461|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBM_SAFETY_MISMATCH|  
|Testo del messaggio|Rilevati livelli di protezione del mirroring del database diversi tra i server per il database "%.*ls". Verrà utilizzato il livello di protezione FULL.|  
  
## <a name="explanation"></a>Spiegazione  
Le connessioni per il mirroring sono state interrotte quando il livello di protezione delle transazioni è stato modificato a causa dell'inconsistenza delle impostazioni di protezione delle transazioni nei database principale e mirror. Verrà utilizzata l'impostazione predefinita del livello di protezione FULL delle transazioni. La sessione verrà eseguita in modalità a protezione elevata.  
  
## <a name="user-action"></a>Azione dell'utente  
Per disattivare la protezione delle transazioni, eseguire nuovamente l'istruzione ALTER DATABASE *nome_database* SET PARTNER SAFETY OFF nel database principale.  
  
