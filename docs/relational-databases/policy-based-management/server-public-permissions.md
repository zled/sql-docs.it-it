---
title: "Autorizzazioni server per il ruolo public | Microsoft Docs"
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
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Autorizzazioni server per il ruolo public
  Questa regola consente di determinare se il ruolo del server public dispone di autorizzazioni server. Ogni account di accesso creato nel server è un membro del ruolo del server public. Se questa condizione viene soddisfatta, ogni account di accesso nel server disporrà di autorizzazioni server.  
  
## Procedure consigliate  
 Non concedere autorizzazioni server al ruolo del server public.  
  
> [!IMPORTANT]  
>  Una volta completata l'installazione, nel ruolo **PUBLIC** è disponibile l'autorizzazione **CONNECT** per tutti gli endpoint ad eccezione di **Connessione amministrativa dedicata**. Questa situazione è normale e, generalmente, non deve essere modificata (l'accesso viene controllato con l'autorizzazione **CONNECT SQL** che viene concessa automaticamente in caso di creazione di nuovi account di accesso).  
  
### Per ulteriori informazioni  
 [Sicurezza di SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
  