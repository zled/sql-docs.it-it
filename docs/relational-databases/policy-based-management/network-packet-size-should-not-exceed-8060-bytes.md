---
title: "Valore massimo per le dimensioni del pacchetto di rete impostato su 8060 byte | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Procedure consigliate [Motore di database]"
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Valore massimo per le dimensioni del pacchetto di rete impostato su 8060 byte
  Se il valore specificato per sp_configure ''network packet size' o se le dimensioni del pacchetto di rete di qualsiasi utente connesso sono maggiori di 8060 byte, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue operazioni di allocazione della memoria diverse. In questo caso, può verificarsi un aumento dello spazio degli indirizzi virtuali dei processi non riservato per il pool di buffer.  
  
## Procedure consigliate  
 Le dimensioni del pacchetto di rete non devono superare 8060 byte.  
  
## Ulteriori informazioni  
 [Articolo 903002 della Microsoft Knowledge Base](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  