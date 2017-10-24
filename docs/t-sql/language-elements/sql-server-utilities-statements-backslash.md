---
title: (Barra rovesciata) (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- '\_TSQL'
- '\'
dev_langs:
- TSQL
helpviewer_keywords:
- backwhack
- backslash
- excape character
- hack character
- '\ (backslash)'
- backslant
- bash
- reverse slant
- slosh
- reversed virgule
- line continuation character
- reverse solidus
ms.assetid: c97fbb20-3d12-4d0b-9b52-62a229bc83c0
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 011025d20b6341b9fa43b25f6c14c91a135a6ffa
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-utilities-statements---backslash"></a>Istruzioni delle utilità SQL Server - barra rovesciata
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vengono forniti comandi che non sono [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni, ma che vengono riconosciuti dal **sqlcmd** e **osql** utilità e [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Editor di codice. Questi comandi possono essere utilizzati per facilitare la leggibilità e l'esecuzione di batch e script.  
  
\ suddivide una stringa lunga costante in due o più righe per migliorare la leggibilità.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
<first section of string> \  
<continued section of string>  
```  
  
## <a name="arguments"></a>Argomenti  
 \<prima sezione della stringa >  
 Inizio di una stringa.  
  
 \<continua sezione della stringa >  
 Continuazione di una stringa.  
  
## <a name="remarks"></a>Osservazioni  
 Questo comando restituisce le prime sezioni e quelle successive della stringa come un'unica stringa, senza la barra rovesciata.  
  
 La barra rovesciata non costituisce un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)], Si tratta di un comando riconosciuto dal **sqlcmd** e **osql** utilità e [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Editor di codice.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono utilizzati una barra rovesciata e un ritorno a capo per suddividere la stringa in due righe.  
  
```  
SELECT 'abc\  
def' AS ColumnResult;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ColumnResult  
 ------------  
 abcdef
 ```    
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [&#40; divisione &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/divide-transact-sql.md)   
 [&#40; dividere EQUALS &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [Composta operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  

