---
title: Replica transazionale bidirezionale | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
caps.latest.revision: 26
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 59817a189d1e52f7d4e8532c35fc024aa1745e3f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168063"
---
# <a name="bidirectional-transactional-replication"></a>replica transazionale bidirezionale
  La replica transazionale bidirezionale è una topologia di replica transazionale specifica che consente lo scambio reciproco di modifiche tra due server: ogni server pubblica i dati e successivamente esegue la sottoscrizione di una pubblicazione con gli stessi dati dell'altro server. Il parametro **@loopback_detection** di [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) è impostato su TRUE per garantire che le modifiche vengano inviate solo al Sottoscrittore e non restituite al server di pubblicazione.  
  
 In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive questa topologia è supportata inoltre dalla replica transazionale peer-to-peer, ma la replica bidirezionale consente di migliorare le prestazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md)  
  
  
