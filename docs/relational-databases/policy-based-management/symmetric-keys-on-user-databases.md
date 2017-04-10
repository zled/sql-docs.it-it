---
title: "Chiavi simmetriche nei database utente | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Procedure consigliate [Motore di database]"
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Chiavi simmetriche nei database utente
  Questa regola consente di controllare se le chiavi con lunghezza minore di 128 byte utilizzano l'algoritmo di crittografia RC2 o RC4.  
  
## Procedure consigliate  
 Utilizzare la crittografia AES a 128 bit o maggiore per creare chiavi simmetriche per la crittografia dei dati. Se la crittografia AES non è supportata dal sistema operativo in uso, utilizzare 3DES.  
  
## Ulteriori informazioni  
 [Scelta di un algoritmo di crittografia](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  