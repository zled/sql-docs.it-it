---
title: Errori di sistema imprevisti | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: dde1e7592a3af09900cd656d7b6faafeab88f27d
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2018
ms.locfileid: "51512666"
---
# <a name="unexpected-system-failures"></a>Errori di sistema imprevisti
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Questa regola consente di controllare l'evento SYSTEM 6008 nel registro eventi del computer. Questo evento indica un arresto del sistema imprevisto. Il sistema potrebbe essere instabile e non fornire la stabilità e l'integrità necessarie per ospitare un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Determinare immediatamente la causa dei riavvii imprevisti del server oppure spostare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un altro computer.  
  
  
