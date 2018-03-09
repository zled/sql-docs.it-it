---
title: MSSQLSERVER_5515 | Microsoft Docs
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 5515 (Database Engine error)
ms.assetid: ccd793bc-ba5d-4782-8d72-731fd01fc177
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
robots: noindex,nofollow
ms.workload: Inactive
ms.openlocfilehash: 78b87a2dea7dabd07f8a9c542c3e808511f7118b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver5515"></a>MSSQLSERVER_5515
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|MSSQLSERVER|  
|ID evento|5515|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|FS_OPEN_CONTAINER_FAILED|  
|Testo del messaggio|Impossibile aprire la directory contenitore ''%.*ls'' del file FILESTREAM. Il sistema operativo ha restituito il codice di stato di Windows 0x%x.|  
  
## <a name="explanation"></a>Spiegazione  
La directory contenitore del file FILESTREAM specificata non può essere aperta.  
  
## <a name="user-action"></a>Azione dell'utente  
Per la causa dell'errore, vedere il codice di stato di Windows specifico.  
  
