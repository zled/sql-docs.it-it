---
title: MSSQLSERVER_8649 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 82867bf2346c69a5a30a8021c13fb64bf179607f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682349"
---
# <a name="mssqlserver8649"></a>MSSQLSERVER_8649
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|8649|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|COST_TOO_HIGH|  
|Testo del messaggio|La query è stata annullata perché il suo costo stimato (%d) è maggiore della soglia configurata, pari a %d. Contattare l'amministratore del sistema.|  
  
## <a name="explanation"></a>Spiegazione  
La query è stata annullata perché il suo costo stimato supera la soglia configurata impostata per QUERY_GOVERNOR_COST_LIMIT.  
  
## <a name="user-action"></a>Azione dell'utente  
Impostare l'opzione QUERY_GOVERNOR_COST_LIMIT su un valore più elevato.  
  
## <a name="see-also"></a>Vedere anche  
[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](~/t-sql/statements/set-query-governor-cost-limit-transact-sql.md)  
  
