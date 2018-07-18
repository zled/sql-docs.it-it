---
title: MSSQLSERVER_3437 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 3437 (Database Engine error)
ms.assetid: b38216e2-b650-43bd-97af-061d54f60031
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 96a65f6ee852fa08df1b032606220d32abb3acb7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425330"
---
# <a name="mssqlserver3437"></a>MSSQLSERVER_3437
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|3437|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|NODTC|  
|Testo del messaggio|Errore durante il recupero del database '%.*ls'. Impossibile connettersi a Microsoft Distributed Transaction Coordinator (MS DTC) per controllare lo stato di avanzamento della transazione %S_XID. Correggere MS DTC, quindi eseguire nuovamente il recupero.|  
  
## <a name="explanation"></a>Spiegazione  
 Una o più transazioni distribuite in cui viene utilizzato [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) sono risultate incomplete alla chiusura del database. Non è stato possibile recuperare il database perché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in grado di connettersi a MS DTC per completare le transazioni o eseguirne il rollback.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per recuperare il database, è necessario risolvere dapprima il problema relativo a MS DTC. Per analizzare il problema relativo a MS DTC, esaminare i registri eventi di Windows. Se non è possibile risolvere il problema e recuperare il database, ripristinare un backup del database.  
  
  
