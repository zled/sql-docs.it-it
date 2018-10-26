---
title: nchar e nvarchar (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nvarchar data type
- nchar data type
ms.assetid: 81ee5637-ee31-4c4d-96d0-56c26a742354
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 856f26ac921a1bbe4f467cd11b785ee3868eeac2
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49643889"
---
# <a name="nchar-and-nvarchar-transact-sql"></a>nchar e nvarchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Tipi di dati carattere a lunghezza fissa, **nchar**, o a lunghezza variabile, **nvarchar**. A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], quando si usano regole di confronto abilitate per i [caratteri supplementari (SC)](../../relational-databases/collations/collation-and-unicode-support.md#Supplementary_Characters), questi tipi di dati archiviano l'intera gamma dei dati di tipo carattere [Unicode](../../relational-databases/collations/collation-and-unicode-support.md#Unicode_Defn) e usano la codifica dei caratteri [UTF-16 ](http://www.wikipedia.org/wiki/UTF-16). Se si specificano regole di confronto non SC, questi tipi di dati archiviano solo il subset di dati di tipo carattere supportati dalla codifica dei caratteri [UCS-2](http://www.wikipedia.org/wiki/Universal_Coded_Character_Set#Encoding_forms).
  
## <a name="arguments"></a>Argomenti  
**nchar** [ ( n ) ]  
Dati di tipo stringa a lunghezza fissa. *n* definisce la lunghezza della stringa in coppie di byte e deve essere un valore compreso tra 1 e 4.000. Le dimensioni di archiviazione, espresse in byte, sono pari al doppio di *n*. Per la codifica [UCS-2](http://www.wikipedia.org/wiki/UTF-16#U+0000_to_U+D7FF_and_U+E000_to_U+FFFF), le dimensioni di archiviazione sono pari al doppio di *n* byte e anche il numero di caratteri che possono essere archiviati è *n*. Per la codifica UTF-16, le dimensioni di archiviazione sono ancora pari al doppio di *n* byte, ma il numero di caratteri che possono essere archiviati può essere inferiore a *n* perché i caratteri supplementari usano due coppie di byte, dette anche [coppie di surrogati](http://www.wikipedia.org/wiki/UTF-16#U+010000_to_U+10FFFF). I sinonimi ISO per **nchar** sono **national char** e **national character**.
  
**nvarchar** [ ( n | **max** ) ]  
Dati di tipo stringa a lunghezza variabile. *n* definisce la lunghezza della stringa in coppie di byte e può essere un valore compreso tra 1 e 4.000. **max** indica che le dimensioni di archiviazione massime sono pari a 2^30-1 caratteri (2 GB). Le dimensioni di archiviazione, espresse in byte, sono pari al doppio di *n* byte + 2 byte. Per la codifica [UCS-2](http://www.wikipedia.org/wiki/UTF-16#U+0000_to_U+D7FF_and_U+E000_to_U+FFFF), le dimensioni di archiviazione sono pari al doppio di *n* byte + 2 byte e anche il numero di caratteri che possono essere archiviati è *n*. Per la codifica UTF-16, le dimensioni di archiviazione sono ancora pari al doppio di *n* byte + 2 byte, ma il numero di caratteri che possono essere archiviati può essere inferiore a *n* perché i caratteri supplementari usano due coppie di byte, dette anche [coppie di surrogati](http://www.wikipedia.org/wiki/UTF-16#U+010000_to_U+10FFFF). I sinonimi ISO per **nvarchar** sono **national char varying** e **national character varying**.
  
## <a name="remarks"></a>Remarks  
Se *n* viene omesso in un'istruzione di definizione dei dati o di dichiarazione di variabili, la lunghezza predefinita è 1. Se *n* viene omesso in una funzione CAST, la lunghezza predefinita è 30.

Se si usa **nchar** oppure **nvarchar**, si consiglia di:
- Usare **nchar** quando le dimensioni delle voci di dati delle colonne sono coerenti.  
- Usare **nvarchar** quando le dimensioni delle voci di dati delle colonne presentano notevoli differenze.  
- Usare **nvarchar(max)** quando le dimensioni delle voci di dati delle colonne variano in modo significativo e la lunghezza delle stringhe potrebbe essere superiore a 4.000 coppie di byte.  
  
**sysname** è un tipo di dati di sistema definito dall'utente equivalente dal punto di vista funzionale a **nvarchar(128)**, anche se non ammette valori Null. **sysname** viene usato per fare riferimento a nomi di oggetti di database.
  
Agli oggetti che usano **nchar** o **nvarchar** vengono assegnate le regole di confronto predefinite del database, a meno che non vengano assegnate regole di confronto specifiche tramite la clausola COLLATE.
  
Per **nchar** e **nvarchar** l'opzione SET ANSI_PADDING è sempre impostata su ON. L'opzione SET ANSI_PADDING OFF non è valida per i tipi di dati **nchar** o **nvarchar**.
  
Anteporre la lettera N a costanti di stringa di caratteri Unicode per segnalare input UCS-2 o UTF-16, a seconda che si usino o meno regole di confronto SC. Senza il prefisso N, la stringa viene convertita nella tabella codici predefinita del database che potrebbe non riconoscere certi caratteri. A partire da [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)], quando si usano regole di confronto abilitate per UTF-8, la tabella codici predefinita è in grado di archiviare il set di caratteri UNICODE UTF-8. 
 
> [!NOTE]  
> Quando si usa la lettera N come prefisso di una costante stringa, il risultato della conversione implicita sarà una stringa UCS-2 o UTF-16 se la costante da convertire non supera la lunghezza massima per il tipo di dati stringa nvarchar (4.000). In caso contrario, il risultato della conversione implicita sarà un valore nvarchar (max) di grandi dimensioni.
  
> [!WARNING]  
> Ogni colonna non Null **varchar(max)** o **nvarchar(max)** richiede 24 byte di allocazione fissa aggiuntiva che concorre al raggiungimento del limite delle righe di 8.060 byte durante un'operazione di ordinamento. Questi byte aggiuntivi possono creare un limite implicito al numero di colonne non Null **varchar(max)** o **nvarchar(max)** in una tabella. Non vengono segnalati errori particolari (oltre il normale avviso che indica che le dimensioni massime per le righe superano il valore massimo consentito di 8.060 byte) durante la creazione della tabella o l'inserimento dei dati. Queste grandi dimensioni di riga possono causare errori (ad esempio errore 512) che gli utenti non possono prevedere durante le normali operazioni,  ad esempio l'aggiornamento della chiave di indice cluster o l'ordinamento del set di colonne completo.
  
## <a name="converting-character-data"></a>Conversione dei dati di tipo carattere  
Per informazioni sulla conversione dei dati di tipo carattere, vedere [char e varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md).
  
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
[Set di caratteri a byte singolo e multibyte](/cpp/c-runtime-library/single-byte-and-multibyte-character-sets)  
  
