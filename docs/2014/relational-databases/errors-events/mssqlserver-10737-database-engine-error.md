---
title: MSSQLSERVER_10737 | Microsoft Docs
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
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 36d2c8b330ada7caad303ddc97b6b19b9f62cdc9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168767"
---
# <a name="mssqlserver10737"></a>MSSQLSERVER_10737
    
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
  
  