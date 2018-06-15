---
title: MSSQLSERVER_9001 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a5b1ca50c3a80186911cadd109cdf387023da122
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34324682"
---
# <a name="mssqlserver9001"></a>MSSQLSERVER_9001
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|9001|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LOG_NOT_AVAIL|  
|Testo del messaggio|Il log per il database '%.*ls' non è disponibile. Controllare il registro eventi per i messaggi di errore correlati. Risolvere eventuali errori e riavviare il database.|  
  
## <a name="explanation"></a>Spiegazione  
Il log del database è stato messo offline. In genere questa situazione implica un errore irreversibile per cui è necessario riavviare il database.  
  
## <a name="user-action"></a>Azione dell'utente  
Diagnosticare altri errori e riavviare l'istanza di SQL Server qualora il riavvio non sia già stato eseguito automaticamente.  
  
