---
title: MSSQLSERVER_7308 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6a85c217cc88367f287b2d60ee56be4183ea1850
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064457"
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
  
  