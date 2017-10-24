---
title: TEXTVALID (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTVALID_TSQL
- TEXTVALID
dev_langs:
- TSQL
helpviewer_keywords:
- invalid text pointers [SQL Server]
- valid text pointers [SQL Server]
- TEXTVALID function
- checking text pointers
- text-pointer values
- verifying text pointers
ms.assetid: 9411c349-b59b-4740-a270-92f91d81ad23
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 279022316af7e3a396c7089f48933281264f900f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="text-and-image-functions---textvalid-transact-sql"></a>Testo e immagine funzioni - TEXTVALID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Oggetto **testo**, **ntext**, o **immagine** funzione che controlla se un puntatore di testo specifico è valido.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Non è disponibile una funzionalità alternativa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
TEXTVALID ( 'table.column' ,text_ ptr )  
```  
  
## <a name="arguments"></a>Argomenti  
 *table*  
 Nome della tabella che si desidera utilizzare.  
  
 *colonna*  
 Nome della colonna che si desidera utilizzare.  
  
 *text_ptr*  
 Puntatore di testo che si desidera controllare.  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 Restituisce 1 se il puntatore è valido e 0 in caso contrario. Si noti che l'identificatore per il **testo** la colonna deve contenere il nome della tabella. Non è possibile utilizzare UPDATETEXT, WRITETEXT o READTEXT senza un puntatore di testo valido.  
  
 Le istruzioni e funzioni seguenti sono utili anche quando si lavora con **testo**, **ntext**, e **immagine** dati.  
  
|Funzione o istruzione|Description|  
|---------------------------|-----------------|  
|PATINDEX**(**'*modello %**'***,** *espressione***)**|Restituisce la posizione di carattere della stringa di caratteri specificato in **testo** e **ntext** colonne.|  
|DATALENGTH**(***espressione***)**|Restituisce la lunghezza dei dati in **testo**, **ntext**, e **immagine** colonne.|  
|SET TEXTSIZE|Restituisce il limite, in byte, del **testo**, **ntext**, o **immagine** dati da restituire con un'istruzione SELECT.|  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene stabilito se esiste un puntatore di testo valido per ogni valore della colonna `logo` della tabella `pub_info`.  
  
> [!NOTE]  
>  Per eseguire questo esempio, è necessario installare il **pubs** database.  
  
```  
USE pubs;  
GO  
SELECT pub_id, 'Valid (if 1) Text data'   
   = TEXTVALID ('pub_info.logo', TEXTPTR(logo))   
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id Valid (if 1) Text data   
------ ----------------------   
0736   1                        
0877   1                        
1389   1                        
1622   1                        
1756   1                        
9901   1                        
9952   1                        
9999   1                        
  
(8 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DATALENGTH &#40; Transact-SQL &#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [SET TEXTSIZE &#40; Transact-SQL &#41;](../../t-sql/statements/set-textsize-transact-sql.md)   
 [Testo e immagine funzioni &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [TEXTPTR &#40; Transact-SQL &#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)  
  
  

