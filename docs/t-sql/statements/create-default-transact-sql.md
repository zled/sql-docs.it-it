---
title: CREARE predefinito (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 11/25/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_DEFAULT_TSQL
- CREATE DEFAULT
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], default
- default objects
- CREATE DEFAULT statement
- objects [SQL Server], creating
- DEFAULT definition
ms.assetid: 08475db4-7d90-486a-814c-01a99d783d41
caps.latest.revision: 47
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 71c0f964d245be92fb8d2be19e074fbd34dd616e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-default-transact-sql"></a>CREATE DEFAULT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea un oggetto denominato valore predefinito. Quando è associato a una colonna o a un tipo di dati alias, un valore predefinito specifica il valore che verrà inserito nella colonna a cui è associato l'oggetto (o in tutte le colonne nel caso di un tipo di dati alias) se durante un inserimento non viene specificato in modo esplicito alcun valore.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] In alternativa, utilizzare definizioni di valori predefiniti create con la parola chiave DEFAULT dell'istruzione ALTER TABLE o CREATE TABLE.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE DEFAULT [ schema_name . ] default_name   
AS constant_expression [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *schema_name*  
 Nome dello schema a cui appartiene il valore predefinito.  
  
 *default_name*  
 Nome del valore predefinito. I nomi predefiniti devono essere conformi alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md). Il nome del proprietario del valore predefinito è facoltativo.  
  
 *constant_expression*  
 È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) che contiene solo valori costanti (non può includere i nomi di tutte le colonne o altri oggetti di database). È possibile utilizzare qualsiasi costante, funzione predefinita o espressione matematica, ad eccezione di quelle contenenti tipi di dati alias. Non è consentito l'utilizzo di funzioni definite dall'utente. Racchiudere le costanti carattere e data tra virgolette singole (**'**); valori di valuta, integer e costanti a virgola mobile non richiedono virgolette. I dati binari devono essere preceduti da 0x, mentre i dati di valuta devono essere preceduti dal simbolo di valuta. Il valore predefinito deve essere compatibile con il tipo di dati della colonna.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile creare un nome di valore predefinito solo nel database corrente. I nomi di valore predefinito in un database devono essere univoci per ogni schema. Quando viene creato un valore predefinito, utilizzare **sp_bindefault** e associarla a una colonna o a un tipo di dati alias.  
  
 Se un valore predefinito non è compatibile con la colonna a cui è associato, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un messaggio di errore in corrispondenza dei tentativi di inserimento del valore predefinito. Ad esempio, n/d non può essere utilizzato come valore predefinito per un **numerico** colonna.  
  
 Se la lunghezza del valore predefinito è eccessiva per la colonna a cui è associato, il valore viene troncato.  
  
 Le istruzioni CREATE PROCEDURE non possono essere utilizzate in combinazione con altre istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] in un singolo batch.  
  
 Valore predefinito è necessario eliminarli prima di crearne uno nuovo con lo stesso nome e il valore predefinito deve essere associato mediante l'esecuzione di **sp_unbindefault** prima che venga eliminata.  
  
 Se a una colonna sono associati un valore predefinito e una regola, il valore predefinito non deve violare la regola. Un valore predefinito in conflitto con una regola non viene mai inserito e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un messaggio di errore in corrispondenza di ogni tentativo di immissione del valore predefinito.  
  
 Quando è associato a una colonna, un valore predefinito viene inserito nei casi seguenti:  
  
-   Non è già stato inserito un valore in modo esplicito.  
  
-   Con l'istruzione INSERT è stata specificata la parola chiave DEFAULT VALUES o DEFAULT per l'inserimento di valori predefiniti.  
  
 Se in fase di creazione di una colonna viene specificata la parola chiave NOT NULL e non viene creato alcun valore predefinito, quando un utente non immette una voce nella colonna viene generato un messaggio di errore. Nella tabella seguente vengono descritte le relazioni tra l'esistenza di un valore predefinito e la definizione di una colonna come NULL o NOT NULL. Le voci nella tabella indicano i risultati ottenuti.  
  
|Definizione di colonna|Nessuna voce, nessun valore predefinito|Nessuna voce, valore predefinito|Voce NULL, nessun valore predefinito|Voce NULL, valore predefinito|  
|-----------------------|--------------------------|-----------------------|----------------------------|-------------------------|  
|**NULL**|NULL|predefiniti|NULL|NULL|  
|**NOT NULL**|Errore|predefiniti|errore|errore|  
  
 Per rinominare un valore predefinito, utilizzare **sp_rename**. Per un report a un valore predefinito, utilizzare **sp_help**.  
  
## <a name="permissions"></a>Permissions  
 Per eseguire CREATE DEFAULT, un utente deve disporre come minimo dell'autorizzazione CREATE DEFAULT nel database corrente e dell'autorizzazione ALTER per lo schema in cui viene creato il valore predefinito.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-simple-character-default"></a>A. Creazione di un semplice valore predefinito costituito da una stringa di caratteri  
 Nell'esempio seguente viene creato un valore predefinito costituito dalla stringa di caratteri `unknown`.  
  
```tsql  
USE AdventureWorks2012;  
GO  
CREATE DEFAULT phonedflt AS 'unknown';  
```  
  
### <a name="b-binding-a-default"></a>B. Associazione di un valore predefinito  
 Nell'esempio seguente viene associato il valore predefinito creato nell'esempio A. Il valore predefinito viene utilizzato solo se non vengono specificate voci per la colonna `Phone` della tabella `Contact`. Si noti che omettere una voce è diverso da specificare esplicitamente NULL in un'istruzione INSERT.  
  
 Dato che il valore predefinito `phonedflt` non esiste, l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente ha esito negativo. Questo esempio viene utilizzato solo a scopo illustrativo.  
  
```tsql  
USE AdventureWorks2012;  
GO  
sp_bindefault 'phonedflt', 'Person.PersonPhone.PhoneNumber';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [ELIMINARE predefinito &#40; Transact-SQL &#41;](../../t-sql/statements/drop-default-transact-sql.md)   
 [DROP RULE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-rule-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [sp_bindefault &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_unbindefault &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)  
  
  

