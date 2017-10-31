---
title: MSSQLSERVER_7308 | Microsoft Docs
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
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b1566e13224284179f42dc24002e37dec0063e17
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver7308"></a>MSSQLSERVER_7308
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|7308|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|RMT_STA_DISABLED|  
|Testo del messaggio|Il provider OLE DB '%ls' è configurato per l'esecuzione in modalità apartment a thread singolo. Impossibile utilizzarlo per le query distribuite.|  
  
## <a name="explanation"></a>Spiegazione  
È stato utilizzato un provider OLE DB configurato per l'esecuzione in modalità apartment a thread singolo. I provider OLE DB in esecuzione in modalità apartment a thread singolo non possono essere utilizzati per le query distribuite.  
  
## <a name="user-action"></a>Azione dell'utente  
Per risolvere l'errore, configurare il provider per l'esecuzione in modalità apartment a thread multipli. Se il provider non supporta la modalità MTA e non può essere aggiornato a una versione che la supporta, configurarlo per l'esecuzione out-of-process. Il fornitore del provider deve essere in grado di indicare se il provider supporta la modalità MTA o l'esecuzione out-of-process.  
  

