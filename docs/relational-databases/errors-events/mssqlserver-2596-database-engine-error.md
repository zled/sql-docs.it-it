---
title: MSSQLSERVER_2596 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d0c54732eabe0289f7b8389c26b6f27a80e3b8ea
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47767169"
---
# <a name="mssqlserver2596"></a>MSSQLSERVER_2596
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2596|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_DATABASE_IN_READ_ONLY_MODE|  
|Testo del messaggio|L'istruzione di correzione non è stata elaborata. Il database non può essere in modalità sola lettura.|  
  
## <a name="explanation"></a>Spiegazione  
Il messaggio indica che il database è in modalità sola lettura. Non è possibile implementare correzioni quando un database si trova in tale modalità.  
  
## <a name="user-action"></a>Azione dell'utente  
Impostare il database per l'accesso in lettura/scrittura utilizzando ALTER DATABASE e quindi eseguire nuovamente il comando DBCC.  
  
## <a name="see-also"></a>Vedere anche  
[ALTER DATABASE &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
  
