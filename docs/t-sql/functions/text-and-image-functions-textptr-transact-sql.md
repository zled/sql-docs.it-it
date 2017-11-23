---
title: TEXTPTR (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTPTR_TSQL
- TEXTPTR
dev_langs: TSQL
helpviewer_keywords:
- TEXTPTR function
- viewing text pointer values
- text-pointer values
- displaying text pointer values
ms.assetid: 2672b8cb-f747-46f3-9358-9b49b3583b8e
caps.latest.revision: "36"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 109f9bdd06bf27928450c89ad06dc6d93247b881
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="text-and-image-functions---textptr-transact-sql"></a>Testo e immagine funzioni - TEXTPTR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il puntatore di testo restituisce un valore che corrisponde a un **testo**, **ntext**, o **immagine** colonna **varbinary** formato. È possibile utilizzare il valore del puntatore di testo recuperato nelle istruzioni READTEXT, WRITETEXT e UPDATETEXT.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Non è disponibile una funzionalità alternativa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
TEXTPTR ( column )  
```  
  
## <a name="arguments"></a>Argomenti  
 *colonna*  
 È il **testo**, **ntext**, o **immagine** colonna che verrà utilizzato.  
  
## <a name="return-types"></a>Tipi restituiti  
 **varbinary**  
  
## <a name="remarks"></a>Osservazioni  
 Per le tabelle contenenti testo nelle righe, l'istruzione TEXTPTR restituisce un handle per il testo da elaborare. È possibile ottenere un puntatore di testo valido anche se il valore di testo è Null.  
  
 Non è possibile utilizzare la funzione TEXTPTR sulle colonne di viste, ma solo sulle colonne di tabelle. Per utilizzare la funzione TEXTPTR su una colonna di una vista, è necessario impostare il livello di compatibilità su 80 tramite [del livello di compatibilità di ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md). Se la tabella non contiene testo nelle righe e un **testo**, **ntext**, o **immagine** colonna non è stata inizializzata tramite un'istruzione UPDATETEXT, TEXTPTR restituisce un puntatore null.  
  
 Utilizzare TEXTVALID per verificare la presenza di un puntatore di testo. Non è possibile utilizzare UPDATETEXT, WRITETEXT o READTEXT senza un puntatore di testo valido.  
  
 Queste funzioni e istruzioni sono utili anche quando si lavora con **testo**, **ntext**, e **immagine** dati.  
  
|Funzione o istruzione|Description|  
|---------------------------|-----------------|  
|PATINDEX**('***modello %***',** *espressione***)**|Restituisce la posizione di carattere della stringa di caratteri specificato in **testo** o **ntext** colonne.|  
|DATALENGTH**(***espressione***)**|Restituisce la lunghezza dei dati in **testo**, **ntext**, e **immagine** colonne.|  
|SET TEXTSIZE|Restituisce il limite, in byte, del **testo**, **ntext**, o **immagine** dati da restituire con un'istruzione SELECT.|  
|SOTTOSTRINGA**(***text_column*, *avviare*, *lunghezza***)**|Restituisce un **varchar** stringa specificata dall'oggetto *avviare* offset e *lunghezza*. La lunghezza massima è di 8 KB.|  
  
## <a name="examples"></a>Esempi  
  
> [!NOTE]  
>  Per eseguire gli esempi seguenti, è necessario installare il **pubs** database.  
  
### <a name="a-using-textptr"></a>A. Utilizzo di TEXTPTR  
 L'esempio seguente usa il `TEXTPTR` funzione per individuare il **immagine** colonna `logo` associato `New Moon Books` nel `pub_info` tabella del `pubs` database. Il puntatore di testo è inserito in una variabile locale `@ptrval.`  
  
```  
USE pubs;  
GO  
DECLARE @ptrval varbinary(16);  
SELECT @ptrval = TEXTPTR(logo)  
FROM pub_info pr, publishers p  
WHERE p.pub_id = pr.pub_id   
   AND p.pub_name = 'New Moon Books';  
GO  
```  
  
### <a name="b-using-textptr-with-in-row-text"></a>B. Utilizzo di TEXTPTR con testo all'interno di righe  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il puntatore di testo all'interno di righe deve essere utilizzato all'interno di una transazione, come illustrato nell'esempio seguente.  
  
```  
CREATE TABLE t1 (c1 int, c2 text);  
EXEC sp_tableoption 't1', 'text in row', 'on';  
INSERT t1 VALUES ('1', 'This is text.');  
GO  
BEGIN TRAN;  
   DECLARE @ptrval VARBINARY(16);  
   SELECT @ptrval = TEXTPTR(c2)  
   FROM t1  
   WHERE c1 = 1;  
   READTEXT t1.c2 @ptrval 0 1;  
COMMIT;  
```  
  
### <a name="c-returning-text-data"></a>C. Restituzione di dati in formato testo  
 Nell'esempio seguente la colonna `pub_id` e il puntatore di testo a 16 byte della colonna `pr_info` vengono selezionati nella tabella `pub_info`.  
  
```  
USE pubs;  
GO  
SELECT pub_id, TEXTPTR(pr_info)  
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id                                      
------ ----------------------------------   
0736   0x6c0000000000feffb801000001000100   
0877   0x6d0000000000feffb801000001000300   
1389   0x6e0000000000feffb801000001000500   
1622   0x700000000000feffb801000001000900   
1756   0x710000000000feffb801000001000b00   
9901   0x720000000000feffb801000001000d00   
9952   0x6f0000000000feffb801000001000700   
9999   0x730000000000feffb801000001000f00   
  
(8 row(s) affected)  
```  
  
 Nell'esempio seguente viene illustrato come restituire i primi `8000` byte di testo senza utilizzare TEXTPTR.  
  
```  
USE pubs;  
GO  
SET TEXTSIZE 8000;  
SELECT pub_id, pr_info  
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id pr_info                                                                                                                                                                                                                                                           
------ -----------------------------------------------------------------  
0736   New Moon Books (NMB) has just released another top ten publication. With the latest publication this makes NMB the hottest new publisher of the year!                                                                                                             
0877   This is sample text data for Binnet & Hardley, publisher 0877 in the pubs database. Binnet & Hardley is located in Washington, D.C.  
  
This is sample text data for Binnet & Hardley, publisher 0877 in the pubs database. Binnet & Hardley is located in Washi   
1389   This is sample text data for Algodata Infosystems, publisher 1389 in the pubs database. Algodata Infosystems is located in Berkeley, California.  
  
9999   This is sample text data for Lucerne Publishing, publisher 9999 in the pubs database. Lucerne publishing is located in Paris, France.  
  
This is sample text data for Lucerne Publishing, publisher 9999 in the pubs database. Lucerne publishing is located in   
  
(8 row(s) affected)  
```  
  
### <a name="d-returning-specific-text-data"></a>D. Restituzione di dati specifici in formato testo  
 L'esempio seguente viene individuata la `text` colonna (`pr_info`) associata a `pub_id``0736` nel `pub_info` tabella del `pubs` database. Viene innanzitutto dichiarata la variabile locale `@val`. Il puntatore di testo, ovvero una stringa di dati binari di tipo Long, viene quindi inserito in `@val` e passato come parametro all'istruzione `READTEXT`, che restituisce 10 byte a partire dal quinto byte (offset pari a 4).  
  
```  
USE pubs;  
GO  
DECLARE @val varbinary(16);  
SELECT @val = TEXTPTR(pr_info)   
FROM pub_info  
WHERE pub_id = '0736';  
READTEXT pub_info.pr_info @val 4 10;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pr_info                                                                                                                                                                                                                                                           
-----------------------------------------------------------------------  
 is sample  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DATALENGTH &#40; Transact-SQL &#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [READTEXT &#40; Transact-SQL &#41;](../../t-sql/queries/readtext-transact-sql.md)   
 [SET TEXTSIZE &#40; Transact-SQL &#41;](../../t-sql/statements/set-textsize-transact-sql.md)   
 [Testo e immagine funzioni &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [UPDATETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/updatetext-transact-sql.md)   
 [WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)  
  
  
