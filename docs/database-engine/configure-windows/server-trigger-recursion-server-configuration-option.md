---
title: Opzione di configurazione del server server trigger recursion | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0e5ae4e8696a70146f956de173a8f245f720db75
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47608955"
---
# <a name="server-trigger-recursion-server-configuration-option"></a>Opzione di configurazione del server server trigger recursion
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  L'opzione **server trigger recursion** consente di specificare se consentire o meno l'attivazione ricorsiva di trigger a livello del server. Se l'opzione è impostata su 1 (ON), i trigger a livello del server possono essere attivati in modo ricorsivo. Se è impostata su 0 (OFF ), i trigger non possono essere attivati in modo ricorsivo. Con questa impostazione viene impedita solo la ricorsione diretta. Per disabilitare anche la ricorsione indiretta, impostare l'opzione **nested triggers** su 0. Il valore predefinito è 1 (ON). L'impostazione diventa effettiva immediatamente senza dover riavviare il server.  
  
 Per altre informazioni, vedere [Creazione di trigger annidati](../../relational-databases/triggers/create-nested-triggers.md).  
  
## <a name="see-also"></a>Vedere anche  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
