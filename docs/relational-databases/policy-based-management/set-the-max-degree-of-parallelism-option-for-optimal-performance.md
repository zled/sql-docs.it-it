---
title: Impostare l'opzione relativa al massimo grado di parallelismo per ottenere prestazioni ottimali | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
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
ms.openlocfilehash: 6efd8d390f0f468b8e4236190e58d52acc043a62
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Impostazione dell'opzione relativa al massimo grado di parallelismo per ottenere prestazioni ottimali
  Questa regola consente di determinare se l'opzione relativa al massimo grado di parallelismo (MAXDOP) sia un valore maggiore di 8. L'impostazione di questa opzione su un valore maggiore provoca in genere un utilizzo indesiderato delle risorse e una riduzione delle prestazioni.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione relativa al massimo grado di parallelismo su 8 o su un valore inferiore utilizzando sp_configure.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Articolo 329204 della Microsoft Knowledge Base](http://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Configurare l'opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
