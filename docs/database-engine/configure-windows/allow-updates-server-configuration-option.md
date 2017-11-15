---
title: Opzione di configurazione del server allow updates | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4cbf1454658cc74e2b4bd1c6bf44acdd7c2b25ad
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="allow-updates-server-configuration-option"></a>Opzione di configurazione del server allow updates
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa opzione è ancora presente nella stored procedure **sp_configure** , sebbene la relativa funzionalità non sia disponibile in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'impostazione non ha alcun effetto. Gli aggiornamenti diretti delle tabelle di sistema non sono supportati.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 La modifica dell'opzione **allow updates** provocherà l'esito negativo dell'istruzione RECONFIGURE. È necessario eliminare le modifiche apportate all'opzione **allow updates** in tutti gli script.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
