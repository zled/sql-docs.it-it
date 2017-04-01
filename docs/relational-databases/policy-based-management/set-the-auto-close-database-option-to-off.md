---
title: "Impostazione dell&#39;opzione di database AUTO_CLOSE su OFF | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Procedure consigliate [Motore di database]"
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# Impostazione dell&#39;opzione di database AUTO_CLOSE su OFF
  Questa regola consente di controllare se l'opzione di database AUTO_ CLOSE è impostata su OFF. Se impostata su ON, l'opzione AUTO_CLOSE può provocare una riduzione delle prestazione nei database cui si accede di frequente a causa dell'aumento di overhead dovuto all'apertura e alla chiusura del database dopo ogni connessione. L'opzione AUTO_CLOSE comporta anche lo scaricamento della cache delle procedure dopo ogni connessione.  
  
## Procedure consigliate  
 Impostare l'opzione AUTO_CLOSE su OFF per i database cui si accede di frequente.  
  
## Ulteriori informazioni  
 [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md)  
  
## Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  