---
title: FORMATMESSAGE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FORMATMESSAGE
- FORMATMESSAGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmessages system table
- sys.messages catalog view
- FORMATMESSAGE function
- messages [SQL Server], formats
- errors [SQL Server], formats
ms.assetid: 83f18102-2035-4a87-acd0-8d96d03efad5
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 071f6def07baf0b74919fd5ce93e65494877dda0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="formatmessage-transact-sql"></a>FORMATMESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Costruisce un messaggio da un messaggio in sys. Messages esistente o da una stringa specificata. La funzionalità di FORMATMESSAGE è simile a quella dell'istruzione RAISERROR. Tuttavia, mentre RAISERROR stampa il messaggio immediatamente, FORMATMESSAGE restituisce il messaggio modificato per ulteriori elaborazioni.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
FORMATMESSAGE ( { msg_number  | ' msg_string ' } , [ param_value [ ,...n ] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *msg_number*  
 È l'ID del messaggio archiviato in sys. Messages. Se *msg_number* è < = 13000 oppure se il messaggio non esiste in sys. Messages, viene restituito NULL.  
  
 *msg_string*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 È che una stringa racchiusa tra virgolette singole e valore del parametro contiene segnaposto. Il messaggio di errore può contenere un massimo di 2.047 caratteri. Se contiene più di 2.048 caratteri, vengono visualizzati solo i primi 2.044 e vengono aggiunti tre punti a indicare che il messaggio è stato troncato. I parametri di sostituzione utilizzano un maggior numero di caratteri rispetto a quanto viene visualizzato nell'output a causa della gestione dell'archiviazione interna.  Per informazioni sulla struttura di una stringa di messaggio e l'utilizzo di parametri nella stringa, vedere la descrizione del *argomento msg_str* argomento [RAISERROR &#40; Transact-SQL &#41; ](../../t-sql/language-elements/raiserror-transact-sql.md).  
  
 *param_value*  
 Valore del parametro da utilizzare nel messaggio. È possibile specificare più di un valore di parametro. È necessario specificare i valori nell'ordine in cui le variabili di segnaposto sono elencate nel messaggio. Il numero di valori massimo consentito è 20.  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar**  
  
## <a name="remarks"></a>Osservazioni  
 In modo analogo all'istruzione RAISERROR, l'istruzione FORMATMESSAGE modifica il messaggio mediante la sostituzione delle variabili di segnaposto con i valori di parametro specificati. Per ulteriori informazioni sui segnaposti supportati nei messaggi di errore e il processo di modifica, vedere [RAISERROR &#40; Transact-SQL &#41; ](../../t-sql/language-elements/raiserror-transact-sql.md).  
  
 L'istruzione FORMATMESSAGE esegue la ricerca del messaggio nella lingua corrente dell'utente. Se non esiste una versione localizzata del messaggio, viene utilizzata la versione inglese (Stati Uniti).  
  
 Per i messaggi localizzati, i parametri specificati devono corrispondere ai segnaposti del parametro nella versione inglese (Stati Uniti). Ovvero, il parametro 1 nella versione localizzata deve corrispondere al parametro 1 nella versione inglese (Stati Uniti), il parametro 2 deve corrispondere al parametro 2 e così via.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-example-with-a-message-number"></a>A. Esempio con un numero di messaggio  
 Nell'esempio seguente viene utilizzato un messaggio di replica `20009` archiviati in sys. Messages come, "l'articolo"%s"non è stato possibile aggiungere per la pubblicazione"%s"." FORMATMESSAGE sostituisce i valori `First Variable` e `Second Variable` per i segnaposti dei parametri. La stringa risultante, "l'articolo 'First Variable' non è stato possibile aggiungere alla pubblicazione 'Second Variable'.", viene archiviato nella variabile locale `@var1`.  
  
```  
SELECT text FROM sys.messages WHERE message_id = 20009 AND language_id = 1033;  
DECLARE @var1 VARCHAR(200);   
SELECT @var1 = FORMATMESSAGE(20009, 'First Variable', 'Second Variable');   
SELECT @var1;  
```  
  
### <a name="b-example-with-a-message-string"></a>B. Esempio con una stringa di messaggio  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Nell'esempio seguente accetta una stringa come input.  
  
```  
SELECT FORMATMESSAGE('This is the %s and this is the %s.', 'first variable', 'second variable') AS Result;  
```  
  
 Restituisce:`This is the first variable and this is the second variable.`  
  
### <a name="c-additional-message-string-formatting-examples"></a>C. Stringa di messaggio aggiuntivo gli esempi di formattazione  
 Nell'esempio seguente mostrano un'ampia gamma di opzioni di formattazione.  
  
```  
SELECT FORMATMESSAGE('Signed int %i, %d %i, %d, %+i, %+d, %+i, %+d', 5, -5, 50, -50, -11, -11, 11, 11);  
SELECT FORMATMESSAGE('Signed int with leading zero %020i', 5);  
SELECT FORMATMESSAGE('Signed int with leading zero 0 %020i', -55);  
SELECT FORMATMESSAGE('Unsigned int %u, %u', 50, -50);  
SELECT FORMATMESSAGE('Unsigned octal %o, %o', 50, -50);  
SELECT FORMATMESSAGE('Unsigned hexadecimal %x, %X, %X, %X, %x', 11, 11, -11, 50, -50);  
SELECT FORMATMESSAGE('Unsigned octal with prefix: %#o, %#o', 50, -50);  
SELECT FORMATMESSAGE('Unsigned hexadecimal with prefix: %#x, %#X, %#X, %X, %x', 11, 11, -11, 50, -50);  
SELECT FORMATMESSAGE('Hello %s!', 'TEST');  
SELECT FORMATMESSAGE('Hello %20s!', 'TEST');  
SELECT FORMATMESSAGE('Hello %-20s!', 'TEST');  
SELECT FORMATMESSAGE('Hello %20s!', 'TEST');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [GENERA &#40; Transact-SQL &#41;](../../t-sql/language-elements/throw-transact-sql.md)   
 [sp_addmessage &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [Funzioni di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [RAISERROR &#40; Transact-SQL &#41;](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  

