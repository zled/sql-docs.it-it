---
title: MSSQLSERVER_8712 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 91c0ec4ff0bb2c824e454f04a0e743c059e098e9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47638059"
---
# <a name="mssqlserver8712"></a>MSSQLSERVER_8712
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|8712|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|USEPLAN_ERR_NO_INDEX|  
|Testo del messaggio|L'indice '%.*ls' specificato nell'hint USE PLAN non esiste. Specificare un indice esistente o creare un indice con il nome specificato.|  
  
## <a name="explanation"></a>Spiegazione  
Un indice specificato nell'hint USE PLAN non esiste.  
  
## <a name="user-action"></a>Azione dell'utente  
Verificare che tutti gli indici specificati nell'hint USE PLAN esistano.  
  
## <a name="see-also"></a>Vedere anche  
[Hint di query &#40;Transact-SQL&#41;](~/t-sql/queries/hints-transact-sql-query.md)  
[Guide di piano](~/relational-databases/performance/plan-guides.md)  
  
