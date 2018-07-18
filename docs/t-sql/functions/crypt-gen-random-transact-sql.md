---
title: CRYPT_GEN_RANDOM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CRYPT_GEN_RANDOM_TSQL
- CRYPT_GEN_RANDOM
dev_langs:
- TSQL
helpviewer_keywords:
- CRYPT_GEN_RANDOM function
ms.assetid: b74bd9d4-758e-4b94-89a0-76dcda6d8c42
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a97e2afca882d168f4ca0f6143680f85ccd002ae
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37781042"
---
# <a name="cryptgenrandom-transact-sql"></a>CRYPT_GEN_RANDOM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Questa funzione restituisce un numero generato casualmente di crittografia, generato da CryptoAPI (CAPI). `CRYPT_GEN_RANDOM` restituisce un numero esadecimale di lunghezza pari a un numero specificato di byte.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CRYPT_GEN_RANDOM ( length [ , seed ] )   
```  
  
## <a name="arguments"></a>Argomenti  
*length*  
Lunghezza, in byte, del numero che verrà creato da `CRYPT_GEN_RANDOM`. L'argomento *length* ha un tipo di dati **int** e un intervallo di valori compreso tra 1 e 8000. `CRYPT_GEN_RANDOM` restituisce NULL per un valore **int** non compreso in questo intervallo. 
  
*seed*  
Numero esadecimale facoltativo, da usare come valore di inizializzazione casuale. La lunghezza di *seed* deve corrispondere al valore dell'argomento *length*. L'argomento *seed* ha un tipo di dati **varbinary(8000)**.
  
## <a name="returned-types"></a>Tipi restituiti  
**varbinary(8000)**
  
## <a name="permissions"></a>Autorizzazioni  
Questa funzione è pubblica e non richiede autorizzazioni speciali.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-generating-a-random-number"></a>A. Generazione di un numero casuale  
Questo esempio genera un numero casuale di lunghezza pari a 50 byte:
  
```sql
SELECT CRYPT_GEN_RANDOM(50) ;  
```  
  
Questo esempio genera un numero casuale di lunghezza pari a 4 byte, usando un valore di inizializzazione a 4 byte:
  
```sql
SELECT CRYPT_GEN_RANDOM(4, 0x25F18060) ;  
```  
  
## <a name="see-also"></a>Vedere anche
[RAND &#40;Transact-SQL&#41;](../../t-sql/functions/rand-transact-sql.md)
  
  
