---
title: MSSQLSERVER_17128 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4e3f897039ce723eecc7c4fc2779bb9ad0d8e3aa
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver17128"></a>MSSQLSERVER_17128
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17128|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|INIT_NOBUFSPACE|  
|Testo del messaggio|initdata: memoria non disponibile per i buffer del kernel.|  
  
## <a name="explanation"></a>Spiegazione  
Non è stato possibile eseguire le allocazioni o le prenotazioni iniziali di memoria per il pool di buffer. SQL Server viene chiuso.  
  
## <a name="user-action"></a>Azione dell'utente  
Questo errore si verifica in genere quando SQL Server viene avviato in un computer con requisiti di sistema estremamente inferiori rispetto a quelli minimi necessari.  
  
