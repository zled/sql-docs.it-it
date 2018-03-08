---
title: nchar e nvarchar (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nvarchar data type
- nchar data type
ms.assetid: 81ee5637-ee31-4c4d-96d0-56c26a742354
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4c3f2e9ad1d63992be8f4e4a4c65d821fae73389
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="nchar-and-nvarchar-transact-sql"></a>nchar e nvarchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Tipi di dati che sono a lunghezza fissa, carattere **nchar**, o a lunghezza variabile, **nvarchar**, set di dati Unicode e l'utilizzo di UNICODE UCS-2 caratteri.
  
## <a name="arguments"></a>Argomenti  
**nchar** [(n)]  
Dati di tipo string a lunghezza fissa Unicode. *n*definisce la lunghezza della stringa e deve essere un valore compreso tra 1 e 4.000. Le dimensioni di archiviazione sono pari al doppio  *n*  byte. Quando la tabella codici delle regole di confronto utilizza caratteri a byte doppio, le dimensioni di archiviazione sono ancora  *n*  byte. A seconda della stringa, le dimensioni di archiviazione  *n*  byte possono essere minore del valore specificato per  *n* . I sinonimi di ISO per **nchar** sono **char national** e **caratteri nazionali**...
  
**nvarchar** [(n | **max** )]  
Dati di tipo string a lunghezza variabile Unicode. *n*definisce la lunghezza della stringa e può essere un valore compreso tra 1 e 4.000. **max** indica che le dimensioni massime di archiviazione sono 2 ^ 31-1 caratteri, (2 GB). Le dimensioni di archiviazione, espresse in byte, sono pari al doppio della lunghezza effettiva dei dati immessi + 2 byte. I sinonimi di ISO per **nvarchar** sono **national char varying** e **variabile di caratteri nazionali**.
  
## <a name="remarks"></a>Osservazioni  
Quando  *n*  non è specificato nella definizione dei dati o istruzione di dichiarazione di variabile, la lunghezza predefinita è 1. Quando  *n*  non è specificato con la funzione CAST, la lunghezza predefinita è 30.
  
Utilizzare **nchar** quando le dimensioni delle voci della colonna sono pressoché simili.
  
Utilizzare **nvarchar** quando le dimensioni delle voci della colonna sono pressoché variare notevolmente.
  
**sysname** è un tipo di dati definito dall'utente di sistema che è funzionalmente equivalente a **nvarchar (128)**, ad eccezione del fatto che non è nullable. **sysname** viene utilizzato per fare riferimento a nomi di oggetto di database.
  
Gli oggetti che utilizzano **nchar** o **nvarchar** vengono assegnate le regole di confronto predefinite del database, a meno che non viene assegnato un regole di confronto specifiche tramite la clausola COLLATE.
  
SET ANSI_PADDING è sempre attivo per **nchar** e **nvarchar**. SET ANSI_PADDING OFF non è valida per il **nchar** o **nvarchar** tipi di dati.
  
Prefisso costanti di stringa di caratteri Unicode con la lettera N. Senza il prefisso N, la stringa viene convertita la tabella codici predefinita del database. La tabella codici predefinita potrebbe non riconoscere certi caratteri.
 
> [!NOTE]  
>  Quando un prefisso di una costante di stringa con la lettera N, la conversione implicita comporterà una stringa Unicode se la costante da convertire non supera la lunghezza massima per un tipo di dati stringa Unicode (4000). In caso contrario, la conversione implicita comporterà un Unicode valori di grandi dimensioni (max).
  
> [!WARNING]  
>  Ogni valore non null **varchar (max)** o **nvarchar (max)** colonna richiede 24 byte di allocazione fissa aggiuntiva che concorre il limite di riga di 8.060 byte durante un'operazione di ordinamento. Questo può creare un limite al numero di non null implicito **varchar (max)** o **nvarchar (max)** colonne che possono essere create in una tabella. Non vengono segnalati errori particolari (oltre il normale avviso che indica che le dimensioni massime per le righe superano il valore massimo consentito di 8060 byte) durante la creazione della tabella o l'inserimento dei dati. Queste dimensioni delle righe eccessive possono causare errori (ad esempio, l'errore 512) durante le normali operazioni, ad esempio un aggiornamento della chiave dell'indice cluster o l'ordinamento del set di colonne completo, che gli utenti non possono prevedere finché non eseguono un'operazione.  
  
## <a name="converting-character-data"></a>Conversione dei dati di tipo carattere  
Per informazioni sulla conversione di dati di tipo carattere, vedere [char e varchar &#40; Transact-SQL &#41; ](../../t-sql/data-types/char-and-varchar-transact-sql.md).
  
## <a name="examples"></a>Esempi  
  
```sql
CREATE TABLE dbo.MyTable  
(  
  MyNCharColumn nchar(15)  
,MyNVarCharColumn nvarchar(20)
  
);  
  
GO  
INSERT INTO dbo.MyTable VALUES (N'Test data', N'More test data');  
GO  
SELECT MyNCharColumn, MyNVarCharColumn  
FROM dbo.MyTable;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
MyNCharColumn   MyNVarCharColumn  
--------------- --------------------  
Test data       More test data  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[Ad esempio &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)  
[SET ANSI_PADDING &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Regole di confronto e supporto Unicode](../../relational-databases/collations/collation-and-unicode-support.md)
  
  
