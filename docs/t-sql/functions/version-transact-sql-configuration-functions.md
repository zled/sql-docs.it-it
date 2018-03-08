---
title: '@@VERSION (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@VERSION'
- '@@VERSION_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@VERSION function'
- current SQL Server installation information
- versions [SQL Server], @@VERSION
- processors [SQL Server], types
ms.assetid: 385ba80e-7c28-41a5-9cdb-5648f3785983
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 9f2a03af933d739760944f72aaea935e8bb3e682
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40version---transact-sql-configuration-functions"></a>&#x40;&#x40;Versione - funzioni Transact SQL configurazione
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce informazioni sul sistema e sulla build dell'installazione corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
@@VERSION  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar**  
  
## <a name="remarks"></a>Osservazioni  
 Il @@VERSION risultati vengono presentati come una stringa di tipo nvarchar. È possibile utilizzare il [SERVERPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/serverproperty-transact-sql.md) per recuperare i singoli valori delle proprietà.  
  
 Per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono restituite le informazioni seguenti.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Versione  
  
-   Architettura del processore  
  
-   Data di compilazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Dichiarazione di copyright  
  
-   Edizione di[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]   
  
-   Versione del sistema operativo  
  
 Per [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] vengono restituite le informazioni seguenti.  
  
-   Edizione - "Database SQL di Windows Azure"  
  
-   Livello di prodotto - "(CTP)" o "(RTM)"  
  
-   Versione del prodotto  
  
-   Data di compilazione  
  
-   Dichiarazione di copyright  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-return-the-current-version-of-includessnoversionincludesssnoversion-mdmd"></a>R: restituire la versione corrente di[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Nell'esempio seguente vengono restituite le informazioni sulla versione relative all'installazione corrente.  
  
```  
SELECT @@VERSION AS 'SQL Server Version';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-return-the-current-version-of-includessdwincludesssdw-mdmd"></a>B. Restituire la versione corrente di[!INCLUDE[ssDW](../../includes/ssdw-md.md)]  
  
```  
SELECT @@VERSION AS 'SQL Server PDW Version';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)  
  
  

