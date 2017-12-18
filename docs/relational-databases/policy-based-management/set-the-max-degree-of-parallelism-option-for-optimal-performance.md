---
title: Impostare l'opzione relativa al massimo grado di parallelismo per ottenere prestazioni ottimali | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: be61dbbd6902f4e8268182727086bce8fc6bb5b9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Impostazione dell'opzione relativa al massimo grado di parallelismo per ottenere prestazioni ottimali
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questa regola consente di determinare se l'opzione relativa al massimo grado di parallelismo (MAXDOP) sia un valore maggiore di 8. L'impostazione di questa opzione su un valore maggiore provoca in genere un utilizzo indesiderato delle risorse e una riduzione delle prestazioni.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione relativa al massimo grado di parallelismo su 8 o su un valore inferiore utilizzando sp_configure.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Articolo 329204 della Microsoft Knowledge Base](http://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Configurare l'opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
