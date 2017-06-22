---
title: Replica transazionale bidirezionale | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5357fa35dcc99b260049788238a446dbaac38808
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="bidirectional-transactional-replication"></a>replica transazionale bidirezionale
  La replica transazionale bidirezionale è una topologia di replica transazionale specifica che consente lo scambio reciproco di modifiche tra due server: ogni server pubblica i dati e successivamente esegue la sottoscrizione di una pubblicazione con gli stessi dati dell'altro server. Il parametro **@loopback_detection** di [sp_addsubscription &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) è impostato su TRUE per garantire che le modifiche vengano inviate solo al Sottoscrittore e non restituite al server di pubblicazione.  
  
 In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive questa topologia è supportata inoltre dalla replica transazionale peer-to-peer, ma la replica bidirezionale consente di migliorare le prestazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Peer-to-Peer Transactional Replication](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
