---
title: HASHBYTES (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/29/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HASHBYTES_TSQL
- HASHBYTES
dev_langs:
- TSQL
helpviewer_keywords:
- hash input
- HASHBYTES
ms.assetid: 0ea6a4d1-313e-4f70-b939-dd2cd570f6d6
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4826936736685a46e8df8604339a7d4a878981ee
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="hashbytes-transact-sql"></a>HASHBYTES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce l'hash MD2, MD4, MD5, SHA1 o SHA2 del relativo input in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
HASHBYTES ( '<algorithm>', { @input | 'input' } )  
  
<algorithm>::= MD2 | MD4 | MD5 | SHA | SHA1 | SHA2_256 | SHA2_512   
```  
  
## <a name="arguments"></a>Argomenti  
 **'**\<algoritmo >**'**  
 Identifica l'algoritmo di hash da utilizzare per eseguire l'hashing dell'input. Si tratta di un argomento obbligatorio in assenza di impostazioni predefinite. Le virgolette singole sono obbligatorie. A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], tutti gli algoritmi diversi da SHA2_256 e SHA2_512 sono deprecati. Algoritmi meno recenti (sconsigliato) continueranno a funzionare, ma viene generato un evento di deprecazione.  
  
 **@input**  
 Specifica una variabile contenente i dati di cui eseguire l'hashing. **@input**è **varchar**, **nvarchar**, o **varbinary**.  
  
 **'** *input* **'**  
 Specifica un'espressione che restituisce un carattere o una stringa binaria di cui eseguire l'hashing.  
  
 L'output è conforme allo standard dell'algoritmo, ovvero 128 bit (16 byte) per MD2, MD4 e MD5 e 160 bit (20 byte) per SHA e SHA1; 256 bit (32 byte) per SHA2_256 e 512 bit (64 byte) per SHA2_512.  
  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Per [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] e consentita in precedenza, i valori di input sono limitati a 8.000 byte.  
  
## <a name="return-value"></a>Valore restituito  
 **varbinary** (numero massimo di 8000 byte)  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-return-the-hash-of-a-variable"></a>R: restituire l'hash di una variabile  
 Nell'esempio seguente viene restituito il `SHA1` hash di **nvarchar** dati archiviati nella variabile `@HashThis`.  
  
```  
DECLARE @HashThis nvarchar(4000);  
SET @HashThis = CONVERT(nvarchar(4000),'dslfdkjLK85kldhnv$n000#knf');  
SELECT HASHBYTES('SHA1', @HashThis);  
  
```  
  
### <a name="b-return-the-hash-of-a-table-column"></a>B: restituire l'hash di una colonna di tabella  
 Nell'esempio seguente viene restituito l'hash SHA1 dei valori della colonna `c1` nella tabella `Test1`.  
  
```  
CREATE TABLE dbo.Test1 (c1 nvarchar(50));  
INSERT dbo.Test1 VALUES ('This is a test.');  
INSERT dbo.Test1 VALUES ('This is test 2.');  
SELECT HASHBYTES('SHA1', c1) FROM dbo.Test1;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
-------------------------------------------  
0x0E7AAB0B4FF0FD2DFB4F0233E2EE7A26CD08F173  
0xF643A82F948DEFB922B12E50B950CEE130A934D6  
  
(2 row(s) affected)  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di un algoritmo di crittografia](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
  

