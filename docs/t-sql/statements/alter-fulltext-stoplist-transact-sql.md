---
title: ALTER FULLTEXT STOPLIST (Transact-SQL) | Documenti Microsoft
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
- ALTER FULLTEXT STOPLIST
- ALTER_FULLTEXT_STOPLIST_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- ALTER FULLTEXT STOPLIST statement
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: f6ad87d5-6a34-435a-8456-8244947c5c83
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 314e41c5b885ee5441dbc4c88db14c22fc50e7b7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-fulltext-stoplist-transact-sql"></a>ALTER FULLTEXT STOPLIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Inserisce o elimina una parola non significativa nell'elenco di parole non significative full-text predefinito del database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER FULLTEXT STOPLIST stoplist_name  
{   
        ADD [N] 'stopword' LANGUAGE language_term    
  | DROP   
    {  
        'stopword' LANGUAGE language_term   
      | ALL LANGUAGE language_term   
      | ALL  
     }  
;  
```  
  
## <a name="arguments"></a>Argomenti  
 *stoplist_name*  
 Nome dell'elenco di parole non significative da modificare. *stoplist_name* può contenere un massimo di 128 caratteri.  
  
 **'** *parola non significativa* **'**  
 Stringa che può essere una parola con un significato linguistico nella lingua specificata o token senza significato linguistico. *parola non significativa* è limitato per la lunghezza massima dei token (64 caratteri). È possibile specificare una parola non significativa come stringa Unicode.  
  
 LINGUA *language_term*  
 Specifica la lingua da associare il *parola non significativa* aggiunto o eliminato.  
  
 *language_term* può essere specificato come stringa, intero o esadecimale corrispondente all'identificatore delle impostazioni locali (LCID) della lingua, come indicato di seguito:  
  
|Formato|Description|  
|------------|-----------------|  
|String|*language_term* corrisponde al **alias** nel valore della colonna di [Sys. syslanguages (Transact-SQL)](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) vista di compatibilità. La stringa deve essere racchiuso tra virgolette singole, come **'***language_term***'**.|  
|Valore intero|*language_term* è l'identificatore LCID della lingua.|  
|Valore esadecimale|*language_term* è 0x seguito dal valore esadecimale del LCID. Il valore esadecimale non deve superare le otto cifre, inclusi gli zeri iniziali. Se il valore è in formato DBCS (Double-Byte Character Set), verrà convertito in Unicode da SQL Server.|  
  
 AGGIUNGERE **'***parola non significativa***'** LANGUAGE *language_term*  
 Aggiunge una parola non significativa di parole non significative per la lingua specificata da LANGUAGE *language_term*.  
  
 Se la combinazione specificata di parola chiave e valore LCID della lingua non è univoca in STOPLIST, viene restituito un errore.  Se il valore LCID non corrisponde a una lingua registrata, viene generato un errore.  
  
 DROP { **'***parola non significativa***'** LANGUAGE *language_term* | Tutti i LANGUAGE *language_term* | TUTTI I}  
 Elimina una parola non significativa dall'elenco di parole non significative.  
  
 **'** *parola non significativa* **'** LANGUAGE *language_term*  
 Elimina la parola non significativa specificata per la lingua specificata da *language_term*.  
  
 Tutti i LANGUAGE *language_term*  
 Elimina tutte le parole non significative per la lingua specificata da *language_term*.  
  
 ALL  
 Elimina tutte le parole non significative dall'elenco di parole non significative.  
  
## <a name="remarks"></a>Osservazioni  
 CREATE FULLTEXT STOPLIST è supportato solo per il livello di compatibilità 100 e superiore. Per i livelli di compatibilità 80 e 90, l'elenco di parole non significative di sistema viene sempre assegnato al database.  
  
## <a name="permissions"></a>Permissions  
 Per designare un elenco di parole non significative come elenco predefinito per il database è necessaria l'autorizzazione ALTER DATABASE. Per modificare in altro modo un elenco di parole non significative, è necessario essere il proprietario di stoplist o l'appartenenza al gruppo di **db_owner** o **db_ddladmin** ruoli predefiniti del database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene modificato un elenco di parole non significative denominato `CombinedFunctionWordList`, aggiungendo la parola 'en', prima per lo spagnolo, quindi per il francese.  
  
```  
ALTER FULLTEXT STOPLIST CombinedFunctionWordList ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST CombinedFunctionWordList ADD 'en' LANGUAGE 'French';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE FULLTEXT STOPLIST &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [DROP FULLTEXT STOPLIST &#40; Transact-SQL &#41;](../../t-sql/statements/drop-fulltext-stoplist-transact-sql.md)   
 [Configurare e gestire parole non significative ed elenchi per la ricerca Full-Text](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [fulltext_stoplists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [Sys.fulltext_stopwords &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)   
 [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)  
  
  

