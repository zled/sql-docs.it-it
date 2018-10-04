---
title: Opzione di configurazione del server Affinity64 I/O | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- processor affinity [SQL Server]
- binding processors [SQL Server]
- affinity64 I/O mask option
ms.assetid: d304eae7-5116-40ee-a0fa-0a3c0bc20c01
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7449be34c7697f770b18357c465da41cd57164b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210161"
---
# <a name="affinity64-input-output-mask-server-configuration-option"></a>Opzione di configurazione del server Affinity64 I/O
  L'opzione **affinity64 I/O mask** associa l'I/O su disco di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un subset di CPU specificato, analogamente all'opzione **affinity I/O mask** . Utilizzare **affinity I/O mask** per associare i primi 32 processori e **affinity64 I/O mask** per associare i processori rimanenti nel computer. Se si riconfigura **affinity64 I/O mask**, è necessario riavviare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'opzione è disponibile solo nella versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]a 64 bit.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzione di configurazione del server Affinity Mask I/O](affinity-input-output-mask-server-configuration-option.md)   
 [Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
