---
title: UPDATETEXT (Transact-SQL) | Documenti Microsoft
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
- UPDATETEXT
- UPDATETEXT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- text updates [SQL Server]
- updating data [SQL Server]
- data updates [SQL Server], UPDATETEXT statement
- UPDATETEXT statement
ms.assetid: d73c28ee-3972-4afd-af8d-ebbbd9e50793
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 49bd324f97f6ba1d2e8a8120bb502199b4ca0f06
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="updatetext-transact-sql"></a>UPDATETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiorna un'esistente **testo**, **ntext**, o **immagine** campo. Utilizzare UPDATETEXT per modificare solo una parte di un **testo**, **ntext**, o **immagine** colonna nella stessa posizione. Utilizzare WRITETEXT per aggiornare e sostituire un intero **testo**, **ntext**, o **immagine** campo.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare i tipi di dati di valori di grandi dimensioni e **.** Clausola di scrittura del [aggiornamento](../../t-sql/queries/update-transact-sql.md) istruzione alternativa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
UPDATETEXT [BULK] { table_name.dest_column_name dest_text_ptr }  
  { NULL | insert_offset }  
     { NULL | delete_length }  
     [ WITH LOG ]  
     [ inserted_data  
    | { table_name.src_column_name src_text_ptr } ]  
```  
  
## <a name="arguments"></a>Argomenti  
 BULK  
 Consente agli strumenti di caricamento di caricare un flusso di dati binario. Il flusso deve essere fornito dallo strumento a livello di protocollo TDS. Se il flusso di dati non è presente, Query Processor ignora l'opzione BULK.  
  
> [!IMPORTANT]  
>  È consigliabile che l'opzione BULK non venga utilizzata nelle applicazioni basate su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa opzione potrebbe essere modificata o rimossa in una prossima versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *TABLE_NAME* **.** *dest_column_name*  
 È il nome della tabella e **testo**, **ntext**, o **immagine** colonna da aggiornare. I nomi di tabella e i nomi di colonna devono essere conformi alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md). I nomi del database e del proprietario sono facoltativi.  
  
 *dest_text_ptr*  
 È un puntatore di testo valore (restituito dalla funzione TEXTPTR) che punta al **testo**, **ntext**, o **immagine** dati da aggiornare. *dest_text_ptr* deve essere **binario (**16**)**.  
  
 *insert_offset*  
 Posizione iniziale in base zero dell'aggiornamento. Per **testo** o **immagine** colonne *insert_offset* è il numero di byte da ignorare dall'inizio della colonna esistente prima di inserire nuovi dati. Per **ntext** colonne *insert_offset*è il numero di caratteri (ogni **ntext** carattere utilizza 2 byte). Esistente **testo**, **ntext**, o **immagine** dati a partire da questa posizione iniziale in base zero viene spostati a destra per liberare spazio per i nuovi dati. Il valore 0 inserisce i nuovi dati all'inizio dei dati esistenti. Il valore NULL accoda i nuovi dati al valore dei dati esistenti.  
  
 *delete_length*  
 Lunghezza dei dati da eliminare dalla esistente **testo**, **ntext**, o **immagine** colonna, a partire dal *insert_offset* posizione. Il *delete_length*valore è espresso in byte per **testo** e **immagine** colonne e in caratteri per **ntext** colonne. Ogni **ntext** carattere utilizza 2 byte. Il valore 0 non elimina alcun dato. Un valore NULL elimina tutti i dati di *insert_offset* posizione alla fine dell'oggetto esistente **testo** o **immagine** colonna.  
  
 WITH LOG  
 La registrazione è definita dal modello di recupero attivo nel database.  
  
 *inserted_data*  
 I dati da inserire nella esistente **testo**, **ntext**, o **immagine** colonna il *insert_offset* percorso. Si tratta di un singolo **char**, **nchar**, **varchar**, **nvarchar**, **binario**,  **varbinary**, **testo**, **ntext**, o **immagine** valore. *inserted_data* può essere un valore letterale o una variabile.  
  
 *table_name.src_column_name*  
 È il nome della tabella e **testo**, **ntext**, o **immagine** colonna utilizzata come origine dei dati inseriti. I nomi delle tabelle e delle colonne devono essere conformi alle regole per gli identificatori.  
  
 *src_text_ptr*  
 È un puntatore di testo valore (restituito dalla funzione TEXTPTR) che punta a un **testo**, **ntext**, o **immagine** colonna utilizzata come origine dei dati inseriti.  
  
> [!NOTE]  
>  *scr_text_ptr* valore non deve essere identico *dest_text_ptr*valore.  
  
## <a name="remarks"></a>Osservazioni  
 I dati inseriti possono essere una singola *inserted_data* costante, nome della tabella, il nome di colonna o puntatore di testo.  
  
|Operazione di aggiornamento|Parametri di UPDATETEXT|  
|-------------------|---------------------------|  
|Sostituzione di dati esistenti|Specificare un valore diverso da null *insert_offset* valore, un diverso da zero *delete_length* valore e i nuovi dati da inserire.|  
|Eliminazione di dati esistenti|Specificare un valore diverso da null *insert_offset* valore e un diverso da zero *delete_length*. Non specificare nuovi dati da inserire.|  
|Inserimento di nuovi dati|Specificare il *insert_offset* valore, un *delete_length* pari a 0 e i nuovi dati da inserire.|  
  
 Per prestazioni ottimali è consigliabile che **testo**, **ntext** e **immagine** dati da inserire o aggiornare in blocchi con dimensioni che sono multipli di 8.040 byte.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puntatori di testo nella riga **testo**, **ntext**, o **immagine** possono esistere, ma potrebbe non essere valido. Per informazioni sull'opzione text in row, vedere [sp_tableoption &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Per informazioni su come invalidare i puntatori di testo, vedere [sp_invalidate_textptr &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
 Per inizializzare **testo** colonne su NULL, utilizzare WRITETEXT; UPDATETEXT inizializza **testo** colonne da una stringa vuota.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione UPDATE per la tabella specificata.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente il puntatore di testo viene inserito nella variabile locale `@ptrval`, quindi viene eseguita l'istruzione `UPDATETEXT` per aggiornare un errore di ortografia.  
  
> [!NOTE]  
>  Per eseguire l'esempio, è necessario installare il database pubs.  
  
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
UPDATETEXT pub_info.pr_info @ptrval 88 1 'b';  
GO  
ALTER DATABASE pubs SET RECOVERY FULL;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [READTEXT &#40; Transact-SQL &#41;](../../t-sql/queries/readtext-transact-sql.md)   
 [TEXTPTR &#40; Transact-SQL &#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)   
 [WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)  
  
  

