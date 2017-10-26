---
title: '@@OPTIONS (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@OPTIONS'
- '@@OPTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- SET statement, current SET options
- '@@OPTIONS function'
- current SET options
ms.assetid: 3d5c7f6e-157b-4231-bbb4-4645a11078b3
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 9480ffeffa83650b5cf44ad51547c36d5563b13b
ms.contentlocale: it-it
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40options-transact-sql"></a>&#x40;&#x40;opzioni (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sulle opzioni SET correnti.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
@@OPTIONS  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **integer**  
  
## <a name="remarks"></a>Osservazioni  
 Le opzioni possono provenire dall'uso del **impostare** comando o dal **opzioni utente sp_configure** valore. I valori della sessione configurati con il **impostare** comando override il **sp_configure** opzioni. Molti strumenti, come ad esempio [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], configurano automaticamente le opzioni impostate. Ogni utente dispone di un @@OPTIONS funzione che rappresenta la configurazione.  
  
 Tramite l'istruzione SET è possibile modificare le opzioni di linguaggio e di esecuzione delle query per una sessione utente specifica. **@@OPTIONS**  può solo rilevare le opzioni sono impostate su ON o OFF.  
  
 Il **@@OPTIONS**  funzione restituisce una mappa di bit delle opzioni, convertita in base 10 integer (decimale). Le impostazioni di bit vengono archiviate nei percorsi descritti in una tabella nell'argomento [configurare l'opzione di configurazione Server user options](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md).  
  
 Per decodificare il **@@OPTIONS**  valore, convertire il valore restituito dalla **@@OPTIONS**  in formato binario e quindi cercare i valori della tabella nel [configurare le opzioni utente Server Opzione di configurazione](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md). Ad esempio, se `SELECT @@OPTIONS;` restituisce il valore `5496`, usare la calcolatrice Windows (**calc.exe**) per convertire il valore decimale `5496` in formato binario. Il risultato è `1010101111000`. La maggior parte dei caratteri destra (binario 1, 2 e 4) sono 0, che indica che i primi tre elementi della tabella sono disattivate. Consultando la tabella, si noterà che sono quelli **DISABLE_DEF_CNST_CHK** e **IMPLICIT_TRANSACTIONS**, e **CURSOR_CLOSE_ON_COMMIT**. L'elemento successivo (**ANSI_WARNINGS** nel `1000` posizione) si trova in. Continuare a lavorare a sinistra se la mappa di bit e verso il basso nell'elenco di opzioni. Quando le opzioni più a sinistra sono 0, che sono state troncate dalla conversione dei tipi. La mappa di bit `1010101111000` è in realtà `001010101111000` per rappresentare tutte e 15 le opzioni.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-demonstration-of-how-changes-affect-behavior"></a>A. Dimostrazione di come le modifiche influiscono sul comportamento  
 Nell'esempio seguente viene illustrata la differenza nel comportamento di concatenazione con due diverse impostazioni del **CONCAT_NULL_YIELDS_NULL** opzione.  
  
```  
SELECT @@OPTIONS AS OriginalOptionsValue;  
SET CONCAT_NULL_YIELDS_NULL OFF;  
SELECT 'abc' + NULL AS ResultWhen_OFF, @@OPTIONS AS OptionsValueWhen_OFF;  
  
SET CONCAT_NULL_YIELDS_NULL ON;  
SELECT 'abc' + NULL AS ResultWhen_ON, @@OPTIONS AS OptionsValueWhen_ON;  
```  
  
### <a name="b-testing-a-client-nocount-setting"></a>B. Test di un'impostazione NOCOUNT del client  
 L'esempio seguente imposta `NOCOUNT``ON` , quindi verifica il valore di `@@OPTIONS`. Il `NOCOUNT``ON` opzione impedisce il messaggio sul numero di righe interessate venga rinviato al client richiedente per ogni istruzione in una sessione. Il valore di `@@OPTIONS` viene impostato su `512` (0x0200), che rappresenta l'opzione NOCOUNT. In questo esempio viene verificato se l'opzione NOCOUNT è stata abilitata nel client. Ciò può risultare utile, ad esempio, per tenere traccia delle differenze di esecuzione in un client.  
  
```  
SET NOCOUNT ON  
IF @@OPTIONS & 512 > 0   
RAISERROR ('Current user has SET NOCOUNT turned on.', 1, 1)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di configurazione &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Configurare l'opzione di configurazione del server user options](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md)  
  
  

