---
title: Opzione di configurazione del server allow updates | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a9acdfa9668a49ed5e0c67a932bacc1ccee1ac6b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196111"
---
# <a name="allow-updates-server-configuration-option"></a>Opzione di configurazione del server allow updates
  Questa opzione è ancora presente nella stored procedure **sp_configure** , sebbene la relativa funzionalità non sia disponibile in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'impostazione non ha alcun effetto. Gli aggiornamenti diretti delle tabelle di sistema non sono supportati.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 La modifica dell'opzione **allow updates** provocherà l'esito negativo dell'istruzione RECONFIGURE. È necessario eliminare le modifiche apportate all'opzione **allow updates** in tutti gli script.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
