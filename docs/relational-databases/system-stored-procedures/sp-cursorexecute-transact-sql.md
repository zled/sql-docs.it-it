---
title: sp_cursorexecute (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cursorexecute
- sp_cursorexecute_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_cursor_execute
ms.assetid: 6a204229-0a53-4617-a57e-93d4afbb71ac
caps.latest.revision: "7"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2a84f385e37a1b7a6af10beb891c1317523eb482
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spcursorexecute-transact-sql"></a>sp_cursorexecute (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea e popola un cursore in base al piano di esecuzione creato da sp_cursorprepare. Questa procedura, insieme a sp_cursorprepare, svolge la stessa funzione di sp_cursoropen, ma viene suddivisa in due fasi. è possibile richiamare sp_cursorexecute specificando ID = 4 in un pacchetto del flusso TDS.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_cursorexecute prepared_handle, cursor  
    [ , scrollopt[ OUTPUT ]  
    [ , ccopt[ OUTPUT ]  
    [ ,rowcount OUTPUT [ ,bound param][,...n]]]]]  
```  
  
## <a name="arguments"></a>Argomenti  
 *prepared_handle*  
 L'istruzione preparata *gestire* valore restituito da sp_cursorprepare. *prepared_handle* è un parametro obbligatorio che richiede un **int** valore di input.  
  
 *cursor*  
 Identificatore del cursore generato da SQL Server. *cursore* è un parametro obbligatorio che deve essere fornito su tutte le routine successive che agiscono sul cursore, ad esempio sp_cursorfetch  
  
 *scrollopt*  
 Opzione di scorrimento. *scrollopt* è un parametro facoltativo che richiede un **int** valore di input. Il sp_cursorexecute*scrollopt* parametro presenta le stesse opzioni di valore come quelle per sp_cursoropen.  
  
> [!NOTE]  
>  Il valore PARAMETERIZED_STMT non è supportato.  
  
> [!IMPORTANT]  
>  Se un *scrollopt* valore non è specificato, il valore predefinito è KEYSET indipendentemente dal valore *scrollopt* valore specificato in sp_cursorprepare.  
  
 *ccopt*  
 Opzione del controllo della valuta. *ccopt* è un parametro facoltativo che richiede un **int** valore di input. Il sp_cursorexecute*ccopt* parametro presenta le stesse opzioni di valore come quelle per sp_cursoropen.  
  
> [!IMPORTANT]  
>  Se un *ccopt* valore non è specificato, il valore predefinito è OPTIMISTIC indipendentemente dal valore *ccopt* valore specificato in sp_cursorprepare.  
  
 *conteggio delle righe*  
 Parametro facoltativo che indica il numero di righe del buffer di recupero da utilizzare con AUTO_FETCH. Il valore predefinito è 20 righe. *conteggio delle righe* si comporta in modo diverso quando assegnato come valore di input rispetto a un valore restituito.  
  
|Come valore di input|Come valore restituito|  
|--------------------|---------------------|  
|Quando in cui viene specificato AUTO_FETCH con i cursori FAST_FORWARD *rowcount* rappresenta il numero di righe da inserire nel buffer di recupero.|Rappresenta il numero di righe nel set di risultati. Quando il *scrollopt* viene specificato il valore AUTO_FETCH, *rowcount* restituisce il numero di righe recuperate nel buffer di recupero.|  
  
 *bound_param*  
 Indica l'utilizzo facoltativo di parametri aggiuntivi.  
  
> [!NOTE]  
>  I parametri dopo il quinto vengono passati insieme sul piano dell'istruzione come parametri di input.  
  
## <a name="code-return-value"></a>Valore restituito del codice  
 *conteggio delle righe* potrebbe restituire i valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|-1|Numero di righe non note.|  
|-n|Un popolamento asincrono è attivo.|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="scrollopt-and-ccopt-parameters"></a>Parametri scrollopt e ccopt  
 *scrollopt* e *ccopt* sono utili quando vengono sostituiti i piani memorizzati nella cache per la cache del server, vale a dire che l'handle preparato che identifica l'istruzione deve essere ricompilato. Il *scrollopt* e *ccopt* i valori dei parametri devono corrispondere ai valori inviati nella richiesta originale a sp_cursorprepare.  
  
> [!NOTE]  
>  PARAMETERIZED_STMT non deve essere assegnato a *scrollopt*.  
  
 Se non si riesce a fornire valori corrispondenti, i piani verranno ricompilati impedendo le operazioni di preparazione ed esecuzione.  
  
## <a name="rpc-and-tds-considerations"></a>Considerazioni su RPC e TDS  
 Per richiedere che vengano restituiti metadati sull'elenco di selezione del cursore nel flusso TDS, è possibile impostare il flag di input RPC RETURN_METADATA su 1.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_cursoropen &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorfetch &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
