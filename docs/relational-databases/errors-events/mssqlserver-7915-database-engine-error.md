---
title: MSSQLSERVER_7915 | Microsoft Docs
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
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d2c66a3be8c75f871bc75166e3f63972f03aa28b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver7915"></a>MSSQLSERVER_7915
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|7915|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC2_REPAIR_IAM_CHAIN_REBUILT|  
|Testo del messaggio|Correzione: la catena IAM per l'oggetto con ID O_ID, indice con ID I_ID, partizione con ID PN_ID, unità allocazione con ID A_ID (tipo TYPE), è stata troncata prima della pagina P_ID e verrà ricompilata.|  
  
## <a name="explanation"></a>Spiegazione  
Si tratta di un messaggio informativo inviato da REPAIR che indica che la catena IAM (Index Allocation Map) specificata è stata corretta in modo da essere ricompilata. Per la correzione può essere necessaria l'allocazione di un nuovo inizio della catena IAM o la rimozione delle pagine danneggiate dalla catena.  
  
## <a name="user-action"></a>Azione dell'utente  
None  
  
