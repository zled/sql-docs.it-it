---
title: READTEXT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 10/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- READTEXT_TSQL
- READTEXT
dev_langs:
- TSQL
helpviewer_keywords:
- column reading [SQL Server]
- READTEXT statement
- reading columns
ms.assetid: 91b69853-1381-4306-8343-afdb73105738
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c1659dfcc9ca8908ce756eb41b32fd30649decfa
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="readtext-transact-sql"></a>READTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Legge i valori di tipo **text**, **ntext** o **image** da una colonna di tipo **text**, **ntext** o **image** a partire dall'offset specificato e per il numero specificato di byte.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Usare invece la funzione [SUBSTRING](../../t-sql/functions/substring-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
READTEXT { table.column text_ptr offset size } [ HOLDLOCK ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *table* **.** *column*  
 Nome di una tabella e di una colonna in cui leggere i valori. I nomi delle tabelle e delle colonne devono essere conformi alle regole per gli [identificatori](../../relational-databases/databases/database-identifiers.md). È necessario specificare i nomi della tabella e della colonna, mentre il nome del database e il nome del proprietario sono facoltativi.  
  
 *text_ptr*  
 Puntatore di testo valido. *text_ptr* deve essere **binary(16)**.  
  
 *offset*  
 Numero di byte (se vengono usati i tipi di dati **text** o **image**) o caratteri (se viene usato il tipo di dati **ntext**) da ignorare prima di iniziare la lettura dei dati di tipo **text**, **image** o **ntext**.  
  
 *size*  
 Numero di byte (se vengono usati i tipi di dati **text** o **image**) o caratteri (se viene usato il tipo di dati **ntext**) dei dati da leggere. Se *size* è 0, vengono letti 4 KB di dati.  
  
 HOLDLOCK  
 Impedisce la lettura del valore del testo fino alla fine della transazione. Gli altri utenti possono leggere il valore, ma non possono modificarlo.  
  
## <a name="remarks"></a>Remarks  
 Usare la funzione [TEXTPTR](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md) per ottenere un valore *text_ptr* valido. La funzione TEXTPTR restituisce un puntatore alla colonna di tipo **text**, **ntext** o **image** nella riga specificata oppure alla colonna di tipo **text**, **ntext** o **image** nell'ultima riga restituita dalla query se sono state restituite più righe. Poiché TEXTPTR restituisce una stringa binaria di 16 byte, è consigliabile dichiarare una variabile locale in cui archiviare il puntatore di testo e utilizzare quindi la variabile con l'istruzione READTEXT. Per altre informazioni sulla dichiarazione di una variabile locale, vedere [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md).  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i puntatori di testo all'interno di righe possono esistere, ma possono essere non validi. Per altre informazioni sull'opzione **text in row**, vedere [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Per altre informazioni su come invalidare i puntatori di testo, vedere [sp_invalidate_textptr &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
 Il valore della funzione @@TEXTSIZE prevale sulle dimensioni specificate per READTEXT se è minore di queste dimensioni. La funzione @@TEXTSIZE specifica il limite per il numero di byte di dati da restituire impostato dall'istruzione SET TEXTSIZE. Per altre informazioni sull'impostazione della sessione per la funzione TEXTSIZE, vedere [SET TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/statements/set-textsize-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni per l'istruzione READTEXT vengono assegnate per impostazione predefinita agli utenti con autorizzazioni SELECT per la tabella specificata. Le autorizzazioni sono trasferibili, ovvero vengono trasferite insieme alle autorizzazioni SELECT.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono letti i caratteri compresi tra il secondo e il ventiseiesimo carattere della colonna `pr_info` della tabella `pub_info`.  
  
> [!NOTE]  
>  Per eseguire l'esempio, è necessario installare il database di esempio **pubs**.  
  
```  
USE pubs;  
GO  
DECLARE @ptrval varbinary(16);  
SELECT @ptrval = TEXTPTR(pr_info)   
   FROM pub_info pr INNER JOIN publishers p  
      ON pr.pub_id = p.pub_id   
      AND p.pub_name = 'New Moon Books'  
READTEXT pub_info.pr_info @ptrval 1 25;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [@@TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/functions/textsize-transact-sql.md)   
 [UPDATETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/updatetext-transact-sql.md)   
 [WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)  
  
  
