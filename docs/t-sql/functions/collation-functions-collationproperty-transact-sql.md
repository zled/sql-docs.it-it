---
title: COLLATIONPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 76baefbaf0fc156d782c705e8a81683770bedc68
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="collation-functions---collationproperty-transact-sql"></a>Funzioni delle regole di confronto - COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce la proprietà delle regole di confronto specificate in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>Argomenti  
*nome_regole_di_confronto*  
Nome delle regole di confronto. *collation_name* è di tipo **nvarchar(128)** e non dispone di valore predefinito.
  
*property*  
Proprietà regole di confronto. *property* è **varchar(128)**. I valori possibili sono i seguenti:
  
|Nome proprietà|Description|  
|---|---|
|**CodePage**|Tabella codici non Unicode delle regole di confronto. Vedere [Appendix G DBCS/Unicode Mapping Tables](https://msdn.microsoft.com/en-us/library/cc194886.aspx) (Appendice G - Tabelle di mapping DBCS/Unicode) e [Appendix H Code Pages](https://msdn.microsoft.com/en-us/library/cc195051.aspx) (Appendice H - Tabelle codici) per la conversione e la visualizzazione dei mapping dei caratteri di questi valori.|  
|**LCID**|Identificatore delle impostazioni locali (LCID) di Windows per le regole di confronto. Vedere [LCID Structure](https://msdn.microsoft.com/en-us/library/cc233968.aspx) (Struttura LCID) per la conversione di questi valori (sarà necessario convertire prima **varbinary**).|  
|**ComparisonStyle**|Stile di confronto di Windows per le regole di confronto. Restituisce 0 per tutte le regole di confronto binarie, sia (\_BIN) che (\_BIN2), e anche quando tutte le proprietà sono sensibili. Valori della maschera di bit:<br /><br /> Ignora maiuscole/minuscole: 1<br /><br /> Ignora accento : 2<br /><br /> Ignora Kana : 65536<br /><br /> Ignora larghezza: 131072<br /><br /> Nota: anche se ha effetto sul comportamento di confronto, l'opzione con distinzione tra selettori di variazione (\_VSS) non è rappresentata in questo valore.|  
|**Versione**|Versione delle regole di confronto, derivata dal campo relativo alla versione dell'ID delle regole di confronto. Restituisce un valore intero compreso tra 0 e 3.<br /><br /> Le regole di confronto con "140" nel nome restituiscono 3.<br /><br /> Le regole di confronto con "100" nel nome restituiscono 2.<br /><br /> Le regole di confronto con "90" nel nome restituiscono 1.<br /><br /> Tutte le altre regole di confronto restituiscono 0.|  
  
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
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>Vedere anche
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  

