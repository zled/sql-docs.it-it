---
title: float e real (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- float
- real_TSQL
- real
- float_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- numeric data type, floating point
- float data type
- floating point data [SQL Server]
- real data type
ms.assetid: 08ea66b7-624e-4d8b-86bc-750ff76cdfc5
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 913aa9c71234d1b170a14f9707be82d45b1cd5b8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="float-and-real-transact-sql"></a>float e real (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Tipi di dati numerici approssimati da utilizzare con dati numerici a virgola mobile. I dati a virgola mobile sono approssimati. Pertanto, non tutti i valori nell'intervallo del tipo di dati possono essere rappresentati in modo esatto. Il sinonimo ISO per **reale** è **float (24)**.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
**float** [ **(***n***)** ] dove  *n*  è il numero di bit utilizzati per archiviare la mantissa del **float** numero in notazione scientifica e, pertanto determina la precisione e dimensioni di archiviazione. Se  *n*  è specificato, deve essere un valore compreso tra **1** e **53**. Il valore predefinito di  *n*  è **53**.
  
|*n*valore|Precisione|Dimensioni dello spazio di archiviazione|  
|---|---|---|
|**1-24**|7 cifre|4 byte|  
|**25-53**|15 cifre|8 byte|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]considera  *n*  come uno dei due valori possibili. Se **1**<=n<=**24**,  *n*  viene trattato come **24**. Se **25**<=n<=**53**,  *n*  viene trattato come **53**.  
  
Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **float**[**(n)**] tipo di dati conforme allo standard ISO per tutti i valori di  *n*  da **1** tramite **53**. Il sinonimo **valore a precisione doppia** è **float (53)**.
  
## <a name="remarks"></a>Osservazioni  
  
|Tipo di dati|Intervallo|Archiviazione|  
|---|---|---|
|**float**|Da - 1,79E+308 a -2,23E-308, 0 e da 2,23E-308 a 1,79E+308|Dipende dal valore di*n*|  
|**real**|Da - 3,40E + 38 a -1,18E - 38, 0 e da 1,18E - 38 a 3,40E + 38|4 byte|  
  
##  <a name="converting-float-and-real-data"></a>Conversione di dati float e real  
I valori di **float** vengono troncati quando vengono convertiti in qualsiasi tipo integer.
  
Quando si desidera eseguire la conversione da **float** o **reale** per dati di tipo carattere, utilizzando la funzione di stringa STR è in genere più utile di CAST (). STR infatti garantisce un maggiore controllo sul formato. Per ulteriori informazioni, vedere [STR &#40; Transact-SQL &#41; ](../../t-sql/functions/str-transact-sql.md) e [funzioni &#40; Transact-SQL &#41; ](../../t-sql/functions/functions.md).
  
Conversione di **float** i valori che utilizzano la notazione scientifica per **decimale** o **numerico** è limitata ai valori di precisione a 17 cifre solo. Tutti i valori con precisione maggiore di 17 vengono arrotondati a zero.
  
## <a name="see-also"></a>Vedere anche
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Conversione tipo di dati &#40; motore di Database &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
