---
title: PUBLISHINGSERVERNAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PUBLISHINGSERVERNAME_TSQL
- PUBLISHINGSERVERNAME
dev_langs:
- TSQL
helpviewer_keywords:
- PUBLISHINGSERVERNAME function
- Publishers [SQL Server replication], names
ms.assetid: e7c278e5-ab23-419e-ab3e-3bb20b0636df
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 7827b8505caeec43134f75c36cc9dec7190d2663
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33056278"
---
# <a name="replication-functions---publishingservername"></a>Funzioni di replica - PUBLISHINGSERVERNAME
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il nome del server di pubblicazione di origine per un database pubblicato che partecipa a una sessione di mirroring del database. Questa funzione viene eseguita in un'istanza del server di pubblicazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel database di pubblicazione. Utilizzarla per determinare il server di pubblicazione originale del database pubblicato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PUBLISHINGSERVERNAME()  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 La funzione PUBLISHINGSERVERNAME viene utilizzata in tutti i tipi di replica.  
  
 La funzione PUBLISHINGSERVERNAME viene utilizzata quando nel database di pubblicazione esiste una sessione di mirroring del database tra il server di pubblicazione e un'istanza del partner per il mirroring.  
  
 Questa funzione deve essere eseguita nel contesto di un database di pubblicazione. Quando PUBLISHINGSERVERNAME viene eseguita in un database di pubblicazione nell'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del server mirror, viene restituito il nome dell'istanza del server di pubblicazione dal quale ha origine il database pubblicato. Quando la funzione viene eseguita in un database nell'istanza del server mirror non pubblicato o pubblicato dall'istanza del server mirror dopo un failover, viene restituito il nome dell'istanza del server mirror. Quando questa funzione viene eseguita nell'istanza del server di pubblicazione originale, viene restituito il nome del server di pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Mirroring e replica del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)   
 [Funzioni di replica &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/53702dee-de58-47d5-a552-7f32000f77d4)  
  
  
