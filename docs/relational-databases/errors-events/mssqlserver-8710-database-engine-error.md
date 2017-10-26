---
title: MSSQLSERVER_8710 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
caps.latest.revision: 8
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8b4444dc2ed1b239670c75321ec3a0e1401122a0
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver8710"></a>MSSQLSERVER_8710
  
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
  

