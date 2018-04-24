---
title: MSSQLSERVER_10737 | Microsoft Docs
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
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9956654eebe7793269d85a51f61df69bd96c6fbc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver10737"></a>MSSQLSERVER_10737
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|MSSQLSERVER|  
|ID evento|10737|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|REBUILD_PARTITION_ALL_NOT_SPECIFIED|  
|Testo del messaggio|Quando in un'istruzione ALTER TABLE REBUILD o ALTER INDEX REBUILD si specifica una partizione in una clausola DATA_COMPRESSION, è necessario specificare PARTITION=ALL. La clausola PARTITION=ALL viene utilizzata per ribadire che tutte le partizioni della tabella o dell'indice verranno ricompilate anche se nella clausola DATA_COMPRESSION viene specificato un solo subset.|  
  
## <a name="user-action"></a>Azione dell'utente  
Aggiungere la clausola PARTITION=ALL all'istruzione ALTER TABLE o ALTER INDEX. In alternativa, per ricompilare una partizione specifica, usare REBUILD PARTITION = \<partition-number-expr> WITH (DATA_COMPRESSION={ON | OFF}).  
  
