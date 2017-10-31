---
title: COLLATIONPROPERTY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLATIONPROPERTY_TSQL
- COLLATIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], properties
- COLLATIONPROPERTY function
ms.assetid: f5029e74-a1db-4f69-b0f5-5ee920c3311d
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 166a85e5fe33a95cd8a36f221c2a774e4a0a9fb2
ms.contentlocale: it-it
ms.lasthandoff: 10/24/2017

---
# <a name="collation-functions---collationproperty-transact-sql"></a>Funzioni di regole di confronto - COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce la proprietà delle regole di confronto specificate in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>Argomenti  
*collation_name*  
Nome delle regole di confronto. *collation_name* è **nvarchar (128)**, e non dispone di alcun valore predefinito.
  
*proprietà*  
Proprietà regole di confronto. *proprietà* è **varchar (128)**, e può essere uno dei valori seguenti:
  
|Nome proprietà|Description|  
|---|---|
|**CodePage**|Tabella codici non Unicode delle regole di confronto. Vedere [appendice G DBCS/Unicode Mapping delle tabelle](https://msdn.microsoft.com/en-us/library/cc194886.aspx) e [Appendice H tabelle codici](https://msdn.microsoft.com/en-us/library/cc195051.aspx) per convertire questi valori e vedere i mapping dei caratteri.|  
|**LCID**|Identificatore delle impostazioni locali (LCID) di Windows per le regole di confronto. Vedere [struttura LCID](https://msdn.microsoft.com/en-us/library/cc233968.aspx) per convertire questi valori (sarà necessario convertire `VARBINARY` prima).|  
|**ComparisonStyle**|Stile di confronto di Windows per le regole di confronto. Restituisce 0 per tutte le regole di confronto binarie (entrambi `_BIN` e `_BIN2`) nonché quando tutte le proprietà sono riservate. Valori di maschera di bit:<br /><br /> Ignora maiuscole / minuscole: 1<br /><br /> Ignora accento: 2<br /><br /> Ignora Kana: 65536<br /><br /> Ignora larghezza: 131072|  
|**Version**|Versione delle regole di confronto, derivata dal campo relativo alla versione dell'ID delle regole di confronto. Restituisce un valore intero compreso tra 0 e 3.<br /><br /> Regole di confronto con "140" nel nome restituito 3.<br /><br /> Regole di confronto con "100" nel nome restituiscono 2.<br /><br /> Regole di confronto con "90" nel nome restituiscono 1.<br /><br /> Tutte le altre regole di confronto restituiscono 0.|  
  
## <a name="return-types"></a>Tipi restituiti
**sql_variant**
  
## <a name="examples"></a>Esempi  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>Vedere anche
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  


