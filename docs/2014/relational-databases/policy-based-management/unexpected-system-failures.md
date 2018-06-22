---
title: Errori di sistema imprevisti | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 33b749c8d19803fd45e9e25e01c4e89bb4736684
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062618"
---
# <a name="unexpected-system-failures"></a>Errori di sistema imprevisti
  Questa regola consente di controllare l'evento SYSTEM 6008 nel registro eventi del computer. Questo evento indica un arresto del sistema imprevisto. Il sistema potrebbe essere instabile e non fornire la stabilità e l'integrità necessarie per ospitare un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Determinare immediatamente la causa dei riavvii imprevisti del server oppure spostare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un altro computer.  
  
  