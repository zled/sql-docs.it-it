---
title: MSSQL_ENG020596 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c512a34d2eacd44c6f03e5bc9b72f48f5f1676d6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167031"
---
# <a name="mssqleng020596"></a>MSSQL_ENG020596
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|20596|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|L'agente anonimo può essere eliminato solo da '%s' e dai membri del ruolo db_owner.|  
  
## <a name="explanation"></a>Spiegazione  
 Non si dispone di autorizzazioni sufficienti per eliminare l'agente della sottoscrizione anonima. L'account di accesso usato per chiamare [sp_dropanonymousagent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql) deve essere un membro del ruolo predefinito del server **sysadmin** nel server di distribuzione o del ruolo predefinito del database **db_owner** nel database di distribuzione oppure l'utente deve essere lo stesso che ha avviato la prima esecuzione dell'agente.  
  
## <a name="user-action"></a>Azione dell'utente  
 Accedere con le credenziali appropriate ed eseguire **sp_dropanonymousagent**.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)  
  
  
