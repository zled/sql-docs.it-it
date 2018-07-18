---
title: MSSQLSERVER_7911 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 7911 (Database Engine error)
ms.assetid: dd8390f3-0f77-4fb2-ba94-631a56e42bc6
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 39e32ca27fdbcb085b9f0e7e626a61e8dd061fe0
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37418790"
---
# <a name="mssqlserver7911"></a>MSSQLSERVER_7911
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|7911|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC2_REPAIR_PAGE_DEALLOCATED|  
|Testo del messaggio|Correzione: la pagina P_ID è stata deallocata all'oggetto con ID O_ID, indice con ID I_ID, partizione con ID PN_ID, unità allocazione con ID A_ID (tipo TYPE).|  
  
## <a name="explanation"></a>Spiegazione  
 Si tratta di un messaggio informativo generato dall'istruzione REPAIR in cui viene indicato che una pagina è stata deallocata dalla matrice di slot a pagina singola di una mappa di allocazione degli indici (IAM, Index Allocation Map).  
  
## <a name="user-action"></a>Azione dell'utente  
 None  
  
  
