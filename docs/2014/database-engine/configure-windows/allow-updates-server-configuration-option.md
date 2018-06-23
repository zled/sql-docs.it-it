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
ms.topic: article
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
caps.latest.revision: 31
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 739b7aec3e30374fe16f700f6dcfc30bd763f024
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156260"
---
# <a name="allow-updates-server-configuration-option"></a>Opzione di configurazione del server allow updates
  Questa opzione è ancora presente nella stored procedure **sp_configure** , sebbene la relativa funzionalità non sia disponibile in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'impostazione non ha alcun effetto. Gli aggiornamenti diretti delle tabelle di sistema non sono supportati.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 La modifica dell'opzione **allow updates** provocherà l'esito negativo dell'istruzione RECONFIGURE. È necessario eliminare le modifiche apportate all'opzione **allow updates** in tutti gli script.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  