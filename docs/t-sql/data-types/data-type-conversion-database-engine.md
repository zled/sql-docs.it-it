---
title: Tipo di dati conversione (motore di Database) | Documenti Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CAST function
- converting data types [SQL Server]
- CONVERT function
- data types [SQL Server], converting
- implicit data type conversions
- explicit data type conversions [SQL Server]
- converting data types [SQL Server], about converting data types
ms.assetid: ffacf45e-a488-48d0-9bb0-dcc7fd365299
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 811eacd3dc0cbbd622fc6eac6ad91a6e740554f4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="data-type-conversion-database-engine"></a>Conversione di tipi di dati (motore di Database)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

I tipi di dati possono essere convertiti negli scenari seguenti:
-   Quando i dati di un oggetto vengono spostati, confrontati o combinati con i dati di un altro oggetto, può essere necessario convertirli nel tipo di dati del secondo oggetto.  
-   Quando i dati da un [!INCLUDE[tsql](../../includes/tsql-md.md)] colonna dei risultati, codice restituito o parametro di output viene spostato in una variabile di programma, i dati devono essere convertiti dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del tipo di dati di sistema per il tipo di dati della variabile.  
  
Le conversioni del tipo di dati supportate tra una variabile di applicazione e una colonna del set di risultati, un codice restituito, un parametro o un marcatore di parametro di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono definite dall'API di database.
  
## <a name="implicit-and-explicit-conversion"></a>Conversioni implicite ed esplicite
I tipi di dati possono essere convertiti in modo implicito o esplicito.
  
Le conversioni implicite non sono visibili all'utente. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] converte automaticamente i dati da un tipo all'altro. Ad esempio, quando un **smallint** viene confrontato con un **int**, **smallint** viene implicitamente convertito in **int** prima del confronto. Consente di passare.
  
**GETDATE ()** converte in modo implicito in stile di data 0. **SYSDATETIME()** converte in modo implicito in stile di data 21.
  
Nelle conversioni esplicite vengono utilizzate le funzioni CAST e CONVERT.
  
Il [CAST e CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md) funzioni convertono un valore (una variabile locale, una colonna o un'altra espressione) da un tipo di dati a un altro. Ad esempio, la funzione `CAST` seguente converte il valore numerico `$157.27` nella stringa di caratteri `'157.27'`:
  
```sql
CAST ( $157.27 AS VARCHAR(10) )  
```  
  
Utilizzare CAST invece di CONVERT per rendere il codice di programma [!INCLUDE[tsql](../../includes/tsql-md.md)] compatibile con lo standard ISO. Utilizzare CONVERT invece di CAST per trarre vantaggio dalla funzionalità degli stili disponibile in CONVERT.
  
Nella figura seguente vengono illustrate le conversioni di tipi di dati esplicite e implicite consentite per i tipi di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questi includono **xml**, **bigint**, e **sql_variant**. Nessuna conversione implicita in un'assegnazione dal **sql_variant** tipo di dati, ma non esiste conversione implicita a **sql_variant**.
  
![Tabella di conversione di tipi di dati](../../t-sql/data-types/media/lrdatahd.png "tabella di conversione di tipi di dati")
  
## <a name="data-type-conversion-behaviors"></a>Funzionamento della conversione del tipo di dati
Alcune conversioni implicite ed esplicite non sono supportate quando si converte il tipo di dati di un oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un altro tipo di dati. Ad esempio, un **nchar** valore non può essere convertito in un **immagine** valore. Un **nchar** può essere convertito solo in **binario** tramite una conversione esplicita, una conversione implicita a **binario** non è supportata. Tuttavia, un **nchar** può essere convertito in modo esplicito o implicito **nvarchar**.
  
Negli argomenti seguenti viene descritto il funzionamento della conversione dei tipi di dati corrispondenti:
  
 - [binary e varbinary &#40;Transact-SQL&#41;](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)  
 - [datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)  
 - [Money e smallmoney &#40; Transact-SQL &#41;](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)  
 - [bit &#40; Transact-SQL &#41;](../../t-sql/data-types/bit-transact-sql.md)  
 - [datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
 - [smalldatetime &#40; Transact-SQL &#41;](../../t-sql/data-types/smalldatetime-transact-sql.md)  
 - [char e varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md)  
 - [Decimal e numeric &#40; Transact-SQL &#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)  
 - [sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)  
 - [date &#40;Transact-SQL&#41;](../../t-sql/data-types/date-transact-sql.md)  
 - [float e real &#40; Transact-SQL &#41;](../../t-sql/data-types/float-and-real-transact-sql.md)  
 - [tempo &#40; Transact-SQL &#41;](../../t-sql/data-types/time-transact-sql.md)  
 - [DateTime &#40; Transact-SQL &#41;](../../t-sql/data-types/datetime-transact-sql.md)  
 - [int, bigint, smallint e tinyint &#40; Transact-SQL &#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)  
 - [uniqueidentifier &#40; Transact-SQL &#41;](../../t-sql/data-types/uniqueidentifier-transact-sql.md)  
  
###  <a name="converting-data-types-by-using-ole-automation-stored-procedures"></a>Conversione del tipo di dati mediante stored procedure di automazione OLE  
Poiché in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono utilizzati tipi di dati [!INCLUDE[tsql](../../includes/tsql-md.md)] e nell'automazione OLE vengono utilizzati tipi di dati [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], i dati che vengono trasferiti da un sistema all'altro devono essere convertiti tramite le stored procedure di automazione OLE.
  
Nella tabella seguente vengono descritte le conversioni dei tipi di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nei tipi di dati [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].
  
|Tipo di dati di SQL Server|Tipo di dati di Visual Basic|  
|--------------------------|----------------------------|  
|**Char**, **varchar**, **testo**, **nvarchar**, **ntext**|**String**|  
|**decimale**, **numerico**|**String**|  
|**bit**|**Boolean**|  
|**binario**, **varbinary**, **immagine**|Unidimensionale **byte** matrice|  
|**int**|**Long**|  
|**smallint**|**Valore intero**|  
|**tinyint**|**Byte**|  
|**float**|**Double**|  
|**real**|**Singolo**|  
|**money**, **smallmoney**|**Currency**|  
|**DateTime**, **smalldatetime**|**Data**|  
|Qualsiasi tipo impostato su NULL|**Variant** impostato su Null|  
  
Tutti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i valori vengono convertiti in un singolo [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] valore ad eccezione di **binario**, **varbinary**, e **immagine** valori. Questi valori vengono convertiti in un oggetto unidimensionale **byte** matrice [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. Questa matrice con un intervallo di **Byte (**0 per *lunghezza*1**)** in *lunghezza* è il numero di byte nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  **binario**, **varbinary**, o **immagine** valori.
  
Di seguito sono riportate le conversioni dai tipi di dati [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] nei tipi di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
|Tipo di dati di Visual Basic|Tipo di dati di SQL Server|  
|----------------------------|--------------------------|  
|**Long**, **intero**, **Byte**, **booleano**, **oggetto**|**int**|  
|**Double**, **singolo**|**float**|  
|**Currency**|**money**|  
|**Data**|**datetime**|  
|**Stringa** con 4000 caratteri o meno|**varchar**/**nvarchar**|  
|**Stringa** con più di 4000 caratteri|**testo**/**ntext**|  
|Unidimensionale **byte** matrice con 8000 byte o meno|**varbinary**|  
|Unidimensionale **byte** matrice con più di 8000 byte.|**image**|  
  
## <a name="see-also"></a>Vedere anche
[Stored procedure di automazione &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[COLLATE &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)
  
  
