---
title: MSSQLSERVER_2518 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a4fc661059240f626c9f61e3b81f4a80350680fa
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425061"
---
# <a name="mssqlserver2518"></a>MSSQLSERVER_2518
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2518|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED|  
|Testo del messaggio|ID oggetto O_ID (oggetto "O_NAME"): impossibile verificare colonne calcolate e tipi definiti dall'utente per questo oggetto perché Common Language Runtime (CLR) è disabilitato.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo messaggio informativo indica che Query Processor non è riuscito a fornire a DBCC un oggetto interno per consentire la restituzione delle colonne calcolate e dei tipi CLR (Common Language Runtime) definiti dall'utente. Il problema si verifica perché CLR è incluso in una delle colonne, ma non è attivato. L'oggetto interno è incluso in tutte le colonne. Pertanto, l'impossibilità di restituire una singola colonna impedisce la creazione dell'oggetto interno. Ciò significa che non verrà controllata la correttezza delle colonne calcolate o che quest'ultime non verranno utilizzate durante il controllo DBCC della consistenza tra indici e tabelle di base.  
  
## <a name="user-action"></a>Azione dell'utente  
 Attivare CLR ed eseguire nuovamente l'istruzione DBCC.  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitazione dell'integrazione con CLR](../clr-integration/clr-integration-enabling.md)  
  
  
