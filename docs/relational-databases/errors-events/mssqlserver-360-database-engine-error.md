---
title: MSSQLSERVER_360 | Microsoft Docs
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
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 52d9475d877440981a549ae6142479ce1d94af64
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver360"></a>MSSQLSERVER_360
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|360|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DML_UPDATE_SPARSE_AND_COLSET|  
|Testo del messaggio|L'elenco delle colonne di destinazione di un'istruzione INSERT, UPDATE o MERGE non può includere sia una colonna di tipo sparse sia il set di colonne che contiene tale colonna. Riscrivere l'istruzione in modo che includa la colonna di tipo sparse o il set di colonne, ma non entrambi.|  
  
## <a name="explanation"></a>Spiegazione  
Un set di colonne è una rappresentazione XML non tipizzata che combina alcune colonne di una tabella in un output strutturato. È stato effettuato un tentativo di modificare sia il set di colonne che una colonna inclusa nel set, provocando due riferimenti alla stessa colonna.  
  
## <a name="user-action"></a>Azione dell'utente  
Riscrivere l'istruzione in modo che includa i riferimenti o alla colonna oppure al set di colonne, ma non a entrambi.  
  
