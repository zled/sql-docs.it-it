---
title: WRITETEXT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WRITETEXT_TSQL
- WRITETEXT
dev_langs:
- TSQL
helpviewer_keywords:
- replacing data
- WRITETEXT statement
- updating data [SQL Server]
- nonlogged updating
- minimally logged updating [SQL Server]
- overwriting data
- data updates [SQL Server], WRITETEXT statement
ms.assetid: 80c252fd-a8b8-4a2e-888a-059081ed4109
caps.latest.revision: 52
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5bf092ec05c2ae07864c12f092cf8b98f97234fa
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="writetext-transact-sql"></a>WRITETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente l'aggiornamento interattivo con registrazione minima di un oggetto esistente **testo**, **ntext**, o **immagine** colonna. WRITETEXT sovrascrive completamente tutti i dati esistenti nella colonna interessata. Non è possibile utilizzare WRITETEXT su **testo**, **ntext**, e **immagine** colonne nelle viste.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare i tipi di dati di valori di grandi dimensioni e **.** Clausola di scrittura del [aggiornamento](../../t-sql/queries/update-transact-sql.md) istruzione alternativa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
WRITETEXT [BULK]  
  { table.column text_ptr }  
  [ WITH LOG ] { data }  
```  
  
## <a name="arguments"></a>Argomenti  
 BULK  
 Consente agli strumenti di caricamento di caricare un flusso di dati binario. Il flusso deve essere fornito dallo strumento a livello di protocollo TDS. Se il flusso di dati non è presente, Query Processor ignora l'opzione BULK.  
  
> [!IMPORTANT]  
>  È consigliabile che l'opzione BULK non venga utilizzata nelle applicazioni basate su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa opzione potrebbe essere modificata o rimossa in una prossima versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *tabella* **.column**  
 È il nome della tabella e **testo**, **ntext**, o **immagine** colonna da aggiornare. Nomi di tabella e colonna devono essere conformi alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md). I nomi del database e del proprietario sono facoltativi.  
  
 *text_ptr*  
 È un valore che contiene il puntatore per il **testo**, **ntext**, o **immagine** dati. *text_ptr* deve essere **Binary (16)**. Per creare un puntatore di testo, eseguire un [inserire](../../t-sql/statements/insert-transact-sql.md) o [aggiornamento](../../t-sql/queries/update-transact-sql.md) istruzione con dati non null per il **testo**, **ntext**, o **immagine** colonna.  
  
 WITH LOG  
 Argomento ignorato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La registrazione è definita dal modello di recupero attivo nel database.  
  
 *dati*  
 Effettivi **testo**, **ntext** o **immagine** dati da archiviare. *dati* può essere un valore letterale o un parametro. La lunghezza massima del testo che può essere inserito in modo interattivo tramite WRITETEXT è di circa 120 KB per **testo**, **ntext**, e **immagine** dati.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare WRITETEXT per sostituire **testo**, **ntext**, e **immagine** dati e UPDATETEXT per modificare **testo**, **ntext**, e **immagine** dati. UPDATETEXT risulta più flessibile in quanto viene modificata solo una parte di un **testo**, **ntext**, o **immagine** colonna anziché l'intera colonna.  
  
 Per prestazioni ottimali è consigliabile che **testo**, **ntext**, e **immagine** dati essere inseriti o aggiornati in dimensioni blocco multiple di 8040 byte.  
  
 Se il modello di recupero con registrazione minima o in blocco, **testo**, **ntext**, e **immagine** operazioni che utilizzano WRITETEXT sono operazioni con registrazione minima quando i nuovi dati sono inserire o aggiungere.  
  
> [!NOTE]  
>  La registrazione minima non viene utilizzata in caso di aggiornamento di valori esistenti.  
  
 Per consentire la corretta esecuzione di WRITETEXT, è necessario che la colonna includa un puntatore di testo valido.  
  
 Se la tabella non ha text in row, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di risparmiare spazio evitando l'inizializzazione **testo** colonne quando vengono aggiunti valori null impliciti o espliciti **testo** possono includere colonne con INSERT e nessun puntatore di testo ottenere per questi valori null. Per inizializzare **testo** colonne su NULL, utilizzare l'istruzione UPDATE. Se la tabella include testo all'interno delle righe, non è necessario inizializzare la colonna di tipo text per i valori Null ed è sempre possibile ottenere un puntatore di testo.  
  
 La funzione ODBC SQLPutData è più veloce e Usa la memoria dinamica minore rispetto a WRITETEXT. Questa funzione è possibile inserire fino a 2 gigabyte di **testo**, **ntext**, o **immagine** dati.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], nella riga puntatori di testo **testo**, **ntext**, o **immagine** possono esistere, ma potrebbe non essere valido. Per informazioni sull'opzione text in row, vedere [sp_tableoption &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Per informazioni su come invalidare i puntatori di testo, vedere [sp_invalidate_textptr &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione UPDATE per la tabella specificata. L'autorizzazione è trasferibile in caso di trasferimento dell'autorizzazione UPDATE.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente il puntatore di testo viene inserito nella variabile locale `@ptrval` e quindi `WRITETEXT` inserisce la nuova stringa di testo nella riga indicata da `@ptrval`.  
  
> [!NOTE]  
>  Per eseguire questo esempio, è necessario installare il database di esempio pubs.  
  
```  
USE pubs;  
GO  
ALTER DATABASE pubs SET RECOVERY SIMPLE;  
GO  
DECLARE @ptrval binary(16);  
SELECT @ptrval = TEXTPTR(pr_info)   
FROM pub_info pr, publishers p  
WHERE p.pub_id = pr.pub_id   
   AND p.pub_name = 'New Moon Books'  
WRITETEXT pub_info.pr_info @ptrval 'New Moon Books (NMB) has just released another top ten publication. With the latest publication this makes NMB the hottest new publisher of the year!';  
GO  
ALTER DATABASE pubs SET RECOVERY SIMPLE;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [UPDATETEXT &#40; Transact-SQL &#41;](../../t-sql/queries/updatetext-transact-sql.md)  
  
  
