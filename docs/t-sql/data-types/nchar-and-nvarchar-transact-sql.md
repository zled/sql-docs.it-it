---
title: nchar e nvarchar (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nvarchar data type
- nchar data type
ms.assetid: 81ee5637-ee31-4c4d-96d0-56c26a742354
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3cfbc8f95367098861dac13b67baca442133d056
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="nchar-and-nvarchar-transact-sql"></a>nchar e nvarchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Tipi di dati carattere che rappresentano dati Unicode a lunghezza fissa, **nchar**, o variabile, **nvarchar**, e in cui viene usato il set di caratteri UNICODE UCS-2.
  
## <a name="arguments"></a>Argomenti  
**nchar** [ ( n ) ]  
Dati di tipo string a lunghezza fissa Unicode. *n* definisce la lunghezza della stringa e deve essere un valore compreso tra 1 e 4.000. Le dimensioni di archiviazione, espresse in byte, sono pari al doppio di *n*. Quando la tabella codici delle regole di confronto usa caratteri a doppio byte, le dimensioni di archiviazione risultano comunque pari a *n* byte. A seconda della stringa, le dimensioni di archiviazione di *n*byte possono essere inferiori al valore specificato per *n*. I sinonimi ISO per **nchar** sono **national char** e **national character**.
  
**nvarchar** [ ( n | **max** ) ]  
Dati di tipo string a lunghezza variabile Unicode. *n* definisce la lunghezza della stringa e può essere un valore compreso tra 1 e 4.000. **max** indica che le dimensioni di archiviazione massime sono di 2^30-1 caratteri.  Le dimensioni di archiviazione massime espresse in byte sono pari a 2 GB. Le dimensioni di archiviazione effettive espresse in byte sono pari al doppio del numero di caratteri immessi + 2 byte. I sinonimi ISO per **nvarchar** sono **national char varying** e **national character varying**.
  
## <a name="remarks"></a>Remarks  
Se *n* viene omesso in un'istruzione di definizione dei dati o di dichiarazione di variabili, la lunghezza predefinita è 1. Se *n* viene omesso in una funzione CAST, la lunghezza predefinita è 30.
  
Usare **nchar** se le dimensioni delle voci della colonna sono pressoché simili.
  
Usare **nvarchar** se le dimensioni delle voci della colonna variano in modo considerevole.
  
**sysname** è un tipo di dati di sistema definito dall'utente equivalente dal punto di vista funzionale a **nvarchar(128)**, anche se non ammette valori Null. **sysname** viene usato per fare riferimento a nomi di oggetti di database.
  
Agli oggetti che usano **nchar** o **nvarchar** vengono assegnate le regole di confronto predefinite del database, a meno che non vengano assegnate regole di confronto specifiche tramite la clausola COLLATE.
  
Per **nchar** e **nvarchar** l'opzione SET ANSI_PADDING è sempre impostata su ON. L'opzione SET ANSI_PADDING OFF non è valida per i tipi di dati **nchar** o **nvarchar**.
  
Usare la lettera N come prefisso per le costanti stringa di caratteri Unicode. Senza il prefisso N, la stringa viene convertita nella tabella codici predefinita del database. La tabella codici predefinita potrebbe non riconoscere certi caratteri.
 
> [!NOTE]  
>  Quando si usa la lettera N come prefisso di una costante stringa, il risultato della conversione implicita sarà una stringa Unicode se la costante da convertire non supera la lunghezza massima per un tipo di dati stringa Unicode (4.000). In caso contrario, il risultato della conversione implicita sarà un valore di grandi dimensioni Unicode (max).
  
> [!WARNING]  
>  Ogni colonna non Null **varchar(max)** o **nvarchar(max)** richiede 24 byte di allocazione fissa aggiuntiva che concorre al raggiungimento del limite delle righe di 8.060 byte durante un'operazione di ordinamento. Questi byte aggiuntivi possono creare un limite implicito al numero di colonne non Null **varchar(max)** o **nvarchar(max)** in una tabella. Non vengono segnalati errori particolari (oltre il normale avviso che indica che le dimensioni massime per le righe superano il valore massimo consentito di 8060 byte) durante la creazione della tabella o l'inserimento dei dati. Queste grandi dimensioni di riga possono causare errori (ad esempio errore 512) che gli utenti non possono prevedere durante le normali operazioni,  ad esempio l'aggiornamento della chiave di indice cluster o l'ordinamento del set di colonne completo.
  
## <a name="converting-character-data"></a>Conversione dei dati di tipo carattere  
Per informazioni sulla conversione dei dati di tipo carattere, vedere [char e varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md).
  
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
[COLLATE &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)  
[SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Regole di confronto e supporto Unicode](../../relational-databases/collations/collation-and-unicode-support.md)
  
  
