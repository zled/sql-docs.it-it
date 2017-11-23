---
title: float e real (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- float
- real_TSQL
- real
- float_TSQL
dev_langs: TSQL
helpviewer_keywords:
- numeric data type, floating point
- float data type
- floating point data [SQL Server]
- real data type
ms.assetid: 08ea66b7-624e-4d8b-86bc-750ff76cdfc5
caps.latest.revision: "40"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5f955e5d367a17602959f5294f9fb5d393b186b5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="float-and-real-transact-sql"></a>float e real (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

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
  
Conversione di **float** i valori che utilizzano la notazione scientifica per **decimale** o **numerico** è limitata ai valori di precisione a 17 cifre solo. Qualsiasi valore < 5E-18 arrotondato per difetto a 0.
  
## <a name="see-also"></a>Vedere anche
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Conversione tipo di dati &#40; motore di Database &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
