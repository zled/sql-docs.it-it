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
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- READTEXT_TSQL
- READTEXT
dev_langs: TSQL
helpviewer_keywords:
- column reading [SQL Server]
- READTEXT statement
- reading columns
ms.assetid: 91b69853-1381-4306-8343-afdb73105738
caps.latest.revision: "27"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 17d233bf75593d8b27a458120dbcb2035bc7d2ec
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="readtext-transact-sql"></a>READTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Legge **testo**, **ntext**, o **immagine** valori da un **testo**, **ntext**, o **immagine**  colonna, a partire dall'offset specificato e il numero specificato di byte di lettura.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare il [SOTTOSTRINGA](../../t-sql/functions/substring-transact-sql.md) funzione alternativa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
READTEXT { table.column text_ptr offset size } [ HOLDLOCK ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *tabella* **.** *column*  
 Nome di una tabella e di una colonna in cui leggere i valori. Nomi di tabella e colonna devono essere conformi alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md). È necessario specificare i nomi della tabella e della colonna, mentre il nome del database e il nome del proprietario sono facoltativi.  
  
 *text_ptr*  
 Puntatore di testo valido. *text_ptr* deve essere **Binary (16)**.  
  
 *offset*  
 È il numero di byte (quando il **testo** o **immagine** vengono utilizzati tipi di dati) o caratteri (quando il **ntext** viene utilizzato il tipo di dati) da ignorare prima di iniziare a leggere la **testo**, **immagine**, o **ntext** dati.  
  
 *size*  
 È il numero di byte (quando il **testo** o **immagine** vengono utilizzati tipi di dati) o caratteri (quando il **ntext** viene utilizzato il tipo di dati) di dati da leggere. Se *dimensioni* è 0, 4 KB di dati viene letto.  
  
 HOLDLOCK  
 Impedisce la lettura del valore del testo fino alla fine della transazione. Gli altri utenti possono leggere il valore, ma non possono modificarlo.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il [TEXTPTR](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md) funzione per ottenere un oggetto valido *text_ptr* valore. L'istruzione TEXTPTR restituisce un puntatore al **testo**, **ntext**, o **immagine** colonna nella riga specificata o al **testo**, **ntext** , o **immagine** colonna nell'ultima riga restituita dalla query se viene restituita più di una riga. Poiché TEXTPTR restituisce una stringa binaria di 16 byte, è consigliabile dichiarare una variabile locale in cui archiviare il puntatore di testo e utilizzare quindi la variabile con l'istruzione READTEXT. Per ulteriori informazioni sulla dichiarazione di una variabile locale, vedere [DECLARE @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-local-variable-transact-sql.md).  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i puntatori di testo all'interno di righe possono esistere, ma possono essere non validi. Per ulteriori informazioni sul **testo nella riga** opzione, vedere [sp_tableoption &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Per ulteriori informazioni su come invalidare i puntatori di testo, vedere [sp_invalidate_textptr &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
 Il valore di @@TEXTSIZE funzione sostituisce le dimensioni specificate per READTEXT se è inferiore alle dimensioni specificate per READTEXT. Il @@TEXTSIZE funzione specifica il limite sul numero di byte di dati da restituire impostato dall'istruzione SET TEXTSIZE. Per ulteriori informazioni sull'impostazione della sessione TEXTSIZE, vedere [SET TEXTSIZE &#40; Transact-SQL &#41; ](../../t-sql/statements/set-textsize-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni per l'istruzione READTEXT vengono assegnate per impostazione predefinita agli utenti con autorizzazioni SELECT per la tabella specificata. Le autorizzazioni sono trasferibili, ovvero vengono trasferite insieme alle autorizzazioni SELECT.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono letti i caratteri compresi tra il secondo e il ventiseiesimo carattere della colonna `pr_info` della tabella `pub_info`.  
  
> [!NOTE]  
>  Per eseguire questo esempio, è necessario installare il **pubs** database di esempio.  
  
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
  
  
