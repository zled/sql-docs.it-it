---
title: Impostare l'opzione relativa al massimo grado di parallelismo per ottenere prestazioni ottimali | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 90093d7b9969930045e8c302182cf318e92e6939
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37162352"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Impostazione dell'opzione relativa al massimo grado di parallelismo per ottenere prestazioni ottimali
  Questa regola consente di determinare se l'opzione relativa al massimo grado di parallelismo (MAXDOP) sia un valore maggiore di 8. L'impostazione di questa opzione su un valore maggiore provoca in genere un utilizzo indesiderato delle risorse e una riduzione delle prestazioni.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione relativa al massimo grado di parallelismo su 8 o su un valore inferiore utilizzando sp_configure.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Articolo 329204 della Microsoft Knowledge Base](http://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Configurare l'opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
