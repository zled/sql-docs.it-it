---
title: MSSQLSERVER_7901 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cfc5c7bb78561a106130c3663c9ab11bfbf2688a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver7901"></a>MSSQLSERVER_7901
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|7901|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC2_DATABASE_IN_EMERGENCY_MODE|  
|Testo del messaggio|L'istruzione di correzione non è stata elaborata. Questo livello di correzione non è supportato quando il database è in modalità di emergenza.|  
  
## <a name="explanation"></a>Spiegazione  
Il database è in modalità di emergenza ed è stato specificato un livello di correzione diverso da REPAIR_ALLOW_DATA_LOSS. Non è possibile implementare correzioni in modalità di emergenza a meno che non venga specificata l'opzione REPAIR_ALLOW_DATA_LOSS.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire nuovamente il comando e specificare l'opzione REPAIR_ALLOW_DATA_LOSS.  
  
