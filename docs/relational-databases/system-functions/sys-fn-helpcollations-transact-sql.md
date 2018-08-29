---
title: sys.fn_helpcollations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_helpcollations
- fn_helpcollations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_helpcollations function
- collations [SQL Server], supported
- fn_helpcollations function
ms.assetid: b5082e81-1fee-4e2c-b567-5412eaee41c1
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6ecea015e510bb1597f9bb2d969a4f320ad0b842
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43102605"
---
# <a name="sysfnhelpcollations-transact-sql"></a>sys.fn_helpcollations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce un elenco di tutte le regole di confronto supportate.  
  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
fn_helpcollations ()  
```  
  
## <a name="tables-returned"></a>Tabelle restituite  
 **fn_helpcollations** restituisce le informazioni seguenti.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|nome|**sysname**|Nome standard delle regole di confronto|  
|Description|**nvarchar(1000)**|Descrizione delle regole di confronto|  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono supportate le regole di confronto di Windows. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è inoltre supportato un numero limitato (<80) di regole di confronto definite regole di confronto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sviluppate prima che le regole di confronto di Windows venissero supportate in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le regole di confronto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono ancora supportate per la compatibilità con le versioni precedenti, ma è consigliabile non utilizzarle per nuovi progetti di sviluppo. Per altre informazioni sulle regole di confronto di Windows, vedere [Nome delle regole di confronto di Windows &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md). Per altre informazioni sulle regole di confronto, vedere [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  

## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti tutti i nomi delle regole di confronto che iniziano con la lettera `L` e la cui descrizione è "binary sort".  
  
```  
SELECT Name, Description FROM fn_helpcollations()  
WHERE Name like 'L%' AND Description LIKE '% binary sort';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```   
 Name                   Description  
 -------------------    ------------------------------------  
 Lao_100_BIN            Lao-100, binary sort  
 Latin1_General_BIN     Latin1-General, binary sort  
 Latin1_General_100_BIN Latin1-General-100, binary sort  
 Latvian_BIN            Latvian, binary sort  
 Latvian_100_BIN        Latvian-100, binary sort  
 Lithuanian_BIN         Lithuanian, binary sort  
 Lithuanian_100_BIN     Lithuanian-100, binary sort  
  
 (7 row(s) affected)  
 ```    
  
## <a name="see-also"></a>Vedere anche  
[COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md)   
[COLLATIONPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/collation-functions-collationproperty-transact-sql.md)  
[Supporto delle regole di confronto del database per Azure SQL Data Warehouse](https://azure.microsoft.com/blog/database-collation-support-for-azure-sql-data-warehouse-2)  

