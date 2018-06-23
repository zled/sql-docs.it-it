---
title: MSSQLSERVER_3452 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b6ef54d9a48826e67d1fbf8b3673a590a2c58962
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168766"
---
# <a name="mssqlserver3452"></a>MSSQLSERVER_3452
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|3452|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|REC_CHECKIDENTITY|  
|Testo del messaggio|Durante il recupero del database '%.*ls' (%d) è stata rilevata una possibile inconsistenza dei valori Identity nella tabella con ID %d. Eseguire DBCC CHECKIDENT ('%.\*ls').|  
  
## <a name="explanation"></a>Spiegazione  
 Durante l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], nel processo di recupero dei valori Identity nel database è stata rilevata un'incoerenza tra i metadati.  
  
## <a name="user-action"></a>Azione dell'utente  
 Eseguire DBCC CHECKIDENT.  
  
  