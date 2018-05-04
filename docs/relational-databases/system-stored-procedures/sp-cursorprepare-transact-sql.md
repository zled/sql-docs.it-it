---
title: sp_cursorprepare (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor_prepare
ms.assetid: 6207e110-f4bf-4139-b3ec-b799c9cb3ad7
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 38f5b276554f749990e73f5c1561a7dadcf3f805
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spcursorprepare-transact-sql"></a>sp_cursorprepare (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Compila il batch o l'istruzione del cursore in un piano di esecuzione, ma non crea il cursore. L'istruzione compilata può essere utilizzata in un secondo momento da sp_cursorexecute. Questa procedura, insieme a sp_cursorexecute, svolge la stessa funzione di sp_cursoropen, ma viene suddivisa in due fasi. è possibile richiamare sp_cursorprepare specificando ID = 3 in un pacchetto del flusso TDS.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_cursorprepare prepared_handle OUTPUT, params , stmt , options  
    [ , scrollopt[ , ccopt]]  
```  
  
## <a name="arguments"></a>Argomenti  
 *prepared_handle*  
 Un Server di SQL preparato generato da *gestire* identificatore che restituisce un valore intero.  
  
> [!NOTE]  
>  *prepared_handle* viene fornito successivamente a una routine sp_cursorexecute per aprire un cursore. Dopo essere stato creato, un handle esiste fino a quando non si esegue la disconnessione o fino a quando non viene rimosso in modo esplicito tramite la routine sp_cursorunprepare.  
  
 *Params*  
 Identifica le istruzioni con parametri. Il *params* definizione delle variabili viene sostituita per i marcatori di parametro nell'istruzione. *params* è un parametro obbligatorio che richiede un **ntext**, **nchar**, o **nvarchar** valore di input. Immettere un valore NULL se l'istruzione non è con parametri.  
  
> [!NOTE]  
>  Utilizzare un **ntext** stringa come input quando *stmt* è con parametri e *scrollopt* valore PARAMETERIZED_STMT è impostata su ON.  
  
 *stmt*  
 Definisce il set di risultati del cursore. Il *stmt* parametro è obbligatorio e richiede un **ntext**, **nchar** o **nvarchar** valore di input.  
  
> [!NOTE]  
>  Le regole per specificare il *stmt* valore sono uguali a quelle per sp_cursoropen, con l'eccezione che il *stmt* deve essere di tipo di dati string **ntext**.  
  
 *options*  
 Parametro facoltativo tramite cui viene restituita una descrizione delle colonne dei set di risultati del cursore. *le opzioni* richiede le seguenti condizioni **int** valore di input.  
  
|Value|Description|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
 *scrollopt*  
 Opzione di scorrimento. *scrollopt* è un parametro facoltativo che richiede uno dei seguenti **int** valori di input.  
  
|Value|Description|  
|-----------|-----------------|  
|0x0001|KEYSET|  
|0x0002|DYNAMIC|  
|0x0004|FORWARD_ONLY|  
|0x0008|STATIC|  
|0x10|FAST_FORWARD|  
|0x1000|PARAMETERIZED_STMT|  
|0x2000|AUTO_FETCH|  
|0x4000|AUTO_CLOSE|  
|0x8000|CHECK_ACCEPTED_TYPES|  
|0x10000|KEYSET_ACCEPTABLE|  
|0x20000|DYNAMIC_ACCEPTABLE|  
|0x40000|FORWARD_ONLY_ACCEPTABLE|  
|0x80000|STATIC_ACCEPTABLE|  
|0x100000|FAST_FORWARD_ACCEPTABLE|  
  
 Poiché il valore richiesto potrebbe non essere appropriato per il cursore definito da *stmt*, questo parametro funge sia da input e output. In questi casi, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assegna un valore appropriato.  
  
 *ccopt*  
 Opzioni del controllo della concorrenza. *ccopt* è un parametro facoltativo che richiede uno dei seguenti **int** valori di input.  
  
|Value|Description|  
|-----------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS (precedentemente noto come LOCKCC)|  
|0x0004|**OTTIMISTICA** (precedentemente noto come OPTCC)|  
|0x0008|OPTIMISTIC (precedentemente noto come OPTCCVAL)|  
|0x2000|ALLOW_DIRECT|  
|0x4000|UPDT_IN_PLACE|  
|0x8000|CHECK_ACCEPTED_OPTS|  
|0x10000|READ_ONLY_ACCEPTABLE|  
|0x20000|SCROLL_LOCKS_ACCEPTABLE|  
|0x40000|OPTIMISTIC_ACCEPTABLE|  
|0x80000|OPTIMISITC_ACCEPTABLE|  
  
 Come con *scrollpt*, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possibile assegnare un valore diverso da quello richiesto.  
  
## <a name="remarks"></a>Osservazioni  
 Il parametro di stato RPC è uno degli elementi seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|0|Esito positivo|  
|0x0001|Failure|  
|1FF6|Non è stato possibile restituire metadati.<br /><br /> Nota: Il motivo è che l'istruzione non produce un set di risultati. è ad esempio, un'istruzione INSERT o DDL.|  
  
## <a name="examples"></a>Esempi  
 Quando *stmt* è con parametri e *scrollopt* valore PARAMETERIZED_STMT è impostata su ON, il formato della stringa è il seguente:  
  
 {  *\<nome della variabile locale > * *\<tipo di dati >* } [,... *n* ]  
  
## <a name="see-also"></a>Vedere anche  
 [sp_cursorexecute &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorexecute-transact-sql.md)   
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorunprepare &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorunprepare-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
