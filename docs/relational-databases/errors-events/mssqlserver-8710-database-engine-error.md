---
title: MSSQLSERVER_8710 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
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
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f96172d7cb0ae2eddd1da57fd3caebf527270fae
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver8710"></a>MSSQLSERVER_8710
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|MSSQLSERVER|  
|ID evento|8710|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|QUERY2_CUBE_ILLEGAL_AGG_FUNC|  
|Testo del messaggio|Le funzioni di aggregazione utilizzate con query CUBE, ROLLUP o GROUPING SET devono supportare l'unione di aggregazioni secondarie. Per risolvere il problema, rimuovere la funzione di aggregazione o scrivere la query utilizzando UNION ALL nelle clausole GROUP BY.|  
  
## <a name="explanation"></a>Spiegazione  
Una funzione di aggregazione è stata utilizzata con CUBE, ROLLUP o GROUPING SETS che non forniscono un metodo per unire aggregazioni secondarie.  
  
## <a name="user-action"></a>Azione dell'utente  
Per risolvere il problema, rimuovere la funzione di aggregazione o scrivere la query utilizzando UNION ALL nelle clausole GROUP BY.  
  
