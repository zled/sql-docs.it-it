---
title: CURRENT_REQUEST_ID (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CURRENT_REQUEST_ID_TSQL
- CURRENT_REQUEST_ID
dev_langs:
- TSQL
helpviewer_keywords:
- CURRENT_REQUEST_ID
ms.assetid: 949f6e5f-bf5f-49d6-a763-c443d1d51fe2
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 606597ee99c8939d7e0cb098f7279402c0f512af
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="currentrequestid-transact-sql"></a>CURRENT_REQUEST_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Restituisce l'ID della richiesta corrente nella la sessione corrente.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CURRENT_REQUEST_ID()  
```  
  
## <a name="return-types"></a>Tipi restituiti
**smallint**
  
## <a name="remarks"></a>Osservazioni  
Per trovare informazioni precise sulla sessione corrente e la richiesta corrente, utilizzare @@SPID e current_request_id (), rispettivamente.
  
## <a name="see-also"></a>Vedere anche
[@@SPID &#40;Transact-SQL&#41;](../../t-sql/functions/spid-transact-sql.md)
  
  

