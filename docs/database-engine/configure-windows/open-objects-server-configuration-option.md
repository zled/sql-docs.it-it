---
title: "Opzione di configurazione del server open objects | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "open objects - opzione"
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Opzione di configurazione del server open objects
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa opzione è ancora presente in **sp_configure** anche se in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la relativa funzionalità è stata disabilitata. L'impostazione non ha alcun effetto. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il numero degli oggetti di database aperti viene gestito in modo dinamico ed è limitato soltanto dalla memoria disponibile. L'opzione **open objects** è stata mantenuta in **sp_configure** per garantire la compatibilità con le versioni precedenti per gli script esistenti.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## Vedere anche  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  