---
title: Opzione di configurazione del server ft notify bandwidth | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cbd63b35e29b3f27d9327dd29c1ae289bf4d15de
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37974543"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a>Opzione di configurazione del server ft notify bandwidth
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  L'opzione **ft notify bandwidth** consente di specificare la dimensione massima consentita per il pool di buffer di memoria di piccole dimensioni, ovvero dei buffer di memoria di 64 KB. Il valore del parametro *max* specifica il numero massimo di buffer che deve essere gestito in un pool di buffer di piccole dimensioni con lo strumento di gestione della memoria del servizio full-text. Se **max** è uguale a zero, non esiste alcuna limitazione per il numero massimo di buffer consentito in un pool di buffer di piccole dimensioni.  
  
 Il parametro **min** specifica il numero minimo di buffer di memoria che deve essere gestito nel pool di buffer di memoria di piccole dimensioni. In seguito alla richiesta dello strumento di gestione della memoria di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , tutti i pool di buffer in eccesso vengono rilasciati, ma viene mantenuto il numero minimo di buffer. Tuttavia, se il valore **min** è uguale a zero, vengono rilasciati tutti i buffer di memoria.  
  
 In determinati casi il numero di buffer allocati risulta inferiore al valore specificato nel parametro **min** .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Opzione di configurazione del server ft crawl bandwidth](../../database-engine/configure-windows/ft-crawl-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
