---
title: sp_cursorclose (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursor_close_TSQL
- sp_cursor_close
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorclose
ms.assetid: d9b7b44d-cdff-456e-97df-7031a3b9beb6
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: bb3db5049ff370a9dccad98dd7e90efb2e346f0f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33237127"
---
# <a name="spcursorclose-transact-sql"></a>sp_cursorclose (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Chiude e dealloca il cursore e rilascia tutte le risorse associate; vale a dire, viene eliminata la tabella temporanea utilizzata come supporto per i valori KEYSET o STATIC **cursore**. è possibile richiamare sp_cursorclose specificando ID = 9 in un pacchetto del flusso TDS.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_cursorclose cursor  
```  
  
## <a name="arguments"></a>Argomenti  
 *cursor*  
 È un cursore *gestire* valore generato tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e restituito dalla routine sp_cursoropen. *cursore* è un parametro obbligatorio che richiede un' **int** valore di input.  
  
> [!NOTE]  
>  Il valore di input -1 verrà applicato a tutti i cursori della connessione corrente.  
  
## <a name="remarks"></a>Osservazioni  
 *cursore* restituirà messaggi di errore se la procedura è stata eseguita dopo che era stato chiuso il cursore o se viene specificato un handle non valido.  
  
 Lo stato di RPC indica l'esito positivo o negativo complessivo.  
  
 Il conteggio delle righe per DONE è sempre 0.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
