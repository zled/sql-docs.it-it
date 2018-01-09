---
title: LOCALDB_ERROR_INSUFFICIENT_BUFFER | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ff67bda8-7e5c-4b06-8d7b-9985b6059a98
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 64c0af99f9586c46d969b61415c27021d76378b0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="localdberrorinsufficientbuffer"></a>LOCALDB_ERROR_INSUFFICIENT_BUFFER
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|276|  
|Origine evento|Runtime database locale di SQL Server 12.0|  
|Componente|API di Runtime database locale|  
|Testo del messaggio|Dimensioni del buffer passato al metodo API dell'istanza del database locale non sufficienti.|  
  
## <a name="explanation"></a>Spiegazione  
 Buffer di input troppo corto. Troncamento non necessario.  
  
## <a name="user-action"></a>Azione dell'utente  
 Fornire un buffer con la dimensione specificata.  
  
  
