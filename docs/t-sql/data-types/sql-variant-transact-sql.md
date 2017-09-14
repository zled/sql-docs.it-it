---
title: sql_variant (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sql_variant
- sql_variant_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sql_variant comparisons
- storing data [SQL Server], sql_variant
- sql_variant data type
- storage [SQL Server], sql_variant
ms.assetid: 01229779-8bc1-4c7d-890a-8246d4899250
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4eb946d5b6ed5a9c6d33789166327bd2dd25d7c1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="sqlvariant-transact-sql"></a>sql_variant (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Tipo di dati per l'archiviazione di valori per vari tipi di dati supportati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [versione](http://go.microsoft.com/fwlink/p/?LinkId=299658)),[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
sql_variant  
```  
  
## <a name="remarks"></a>Osservazioni  
**sql_variant** può essere utilizzato in colonne, parametri, variabili e i valori restituiti delle funzioni definite dall'utente. **sql_variant** consente a questi oggetti di database per il supporto di valori di altri tipi di dati.
  
Una colonna di tipo **sql_variant** può contenere righe di diversi tipi di dati. Ad esempio, una colonna definita come **sql_variant** può archiviare **int**, **binario**, e **char** valori.
  
**sql_variant** può avere una lunghezza massima pari a 8016 byte. La lunghezza include sia le informazioni sul tipo di base che il valore del tipo di base. La lunghezza massima del valore effettivo del tipo di base è di 8.000 byte.
  
Oggetto **sql_variant** tipo di dati necessario innanzitutto eseguire il cast al valore di tipo di dati di base prima che fanno parte di operazioni quali l'addizione e sottrazione.
  
**sql_variant** può essere assegnato un valore predefinito. A questo tipo di dati è inoltre possibile assegnare NULL come valore sottostante, ma in questo caso ai valori NULL non verrà associato alcun tipo di base. Inoltre, **sql_variant** non può avere un altro **sql_variant** come tipo di base.
  
Una chiave univoca, primaria o esterna può includere colonne di tipo **sql_variant**, ma la lunghezza totale dei valori di dati che costituiscono la chiave di una riga specifica non deve essere maggiore della lunghezza massima di un indice. ovvero 900 byte.
  
Una tabella può includere un numero qualsiasi di **sql_variant** colonne.
  
**sql_variant** non può essere utilizzato in CONTAINSTABLE e FREETEXTTABLE.
  
ODBC non supporta completamente **sql_variant**. Pertanto, le query di **sql_variant** come dati binari vengono restituite le colonne quando si utilizza Provider Microsoft OLE DB per ODBC (MSDASQL). Ad esempio, un **sql_variant** colonna che contiene i dati di stringa di caratteri 'PS2091' viene restituita come 0x505332303931.
  
## <a name="comparing-sqlvariant-values"></a>Confronto di valori sql_variant  
Il **sql_variant** appartiene alla parte superiore dell'elenco gerarchia del tipo di dati per la conversione di tipo di dati. Per **sql_variant** confronti, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordine gerarchico dei tipi di dati verrà raggruppati nelle famiglie di tipi di dati.
  
|Gerarchia dei tipi di dati|Gruppo di tipi di dati|  
|---|---|
|**sql_variant**|**sql_variant**|  
|**datetime2**|Date e Time|  
|**datetimeoffset**|Date e Time|  
|**datetime**|Date e Time|  
|**smalldatetime**|Date e Time|  
|**data**|Date e Time|  
|**time**|Date e Time|  
|**float**|Valori numerici approssimati|  
|**real**|Valori numerici approssimati|  
|**decimal**|Valori numerici esatti|  
|**money**|Valori numerici esatti|  
|**smallmoney**|Valori numerici esatti|  
|**bigint**|Valori numerici esatti|  
|**int**|Valori numerici esatti|  
|**smallint**|Valori numerici esatti|  
|**tinyint**|Valori numerici esatti|  
|**bit**|Valori numerici esatti|  
|**nvarchar**|Unicode|  
|**nchar**|Unicode|  
|**varchar**|Unicode|  
|**char**|Unicode|  
|**varbinary**|Binario|  
|**binary**|Binario|  
|**uniqueidentifier**|**Uniqueidentifier**|  
  
Le regole seguenti si applicano a **sql_variant** confronti:
-   Quando **sql_variant** vengono confrontati i valori di tipi di dati di base diversi e i tipi di dati di base si trovano in data diverse famiglie di tipi, il valore la cui famiglia del tipo di dati è superiore nella gerarchia viene considerato il maggiore dei due valori.  
-   Quando **sql_variant** vengono confrontati i valori di tipi di dati di base diversi e i tipi di dati di base sono della stessa famiglia di tipo di dati, il valore il cui tipo di dati di base inferiore nella gerarchia viene convertito in modo implicito al tipo di dati e viene quindi eseguito il confronto.  
-   Quando **sql_variant** ai valori di **char**, **varchar**, **nchar**, o **nvarchar** sono tipi di dati in confronto, le regole di confronto vengono messe a confronto innanzitutto in base ai criteri seguenti: LCID, versione LCID, flag di confronto e ordinamento ID. Per ognuno di questi criteri il confronto viene eseguito con valori interi e nell'ordine elencato. Se tutti questi criteri sono uguali, i valori effettivi della stringa vengono confrontati in base alle regole di confronto.  
  
## <a name="converting-sqlvariant-data"></a>Conversione di dati sql_variant  
Quando si gestisce il **sql_variant** tipo di dati, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta la conversione implicita di oggetti con altri tipi di dati per il **sql_variant** tipo. Tuttavia, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non consente conversioni implicite da **sql_variant** dati a un oggetto con un altro tipo di dati.
  
## <a name="restrictions"></a>Restrizioni  
Nella tabella seguente sono elencati i tipi di valori che non possono essere archiviati utilizzando **sql_variant**:
  
|||  
|-|-|  
|**varchar(max)**|**varbinary(max)**|  
|**nvarchar(max)**|**xml**|  
|**text**|**ntext**|  
|**image**|**rowversion** (**timestamp**)|  
|**sql_variant**|**geography**|  
|**hierarchyid**|**geometry**|  
|Tipi definiti dall'utente|**datetimeoffset**|  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[SQL_VARIANT_PROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sql-variant-property-transact-sql.md)
  
  
