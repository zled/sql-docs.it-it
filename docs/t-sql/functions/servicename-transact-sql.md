---
title: '@@SERVICENAME (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@SERVICENAME_TSQL'
- '@@SERVICENAME'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@SERVICENAME function'
- names [SQL Server], registry keys
- registry keys [SQL Server]
ms.assetid: 5b0b35be-50ae-411d-a607-bf7464b73624
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 457749a5374f208e78cf26f495fdf026779a80f4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052089"
---
# <a name="x40x40servicename-transact-sql"></a>&#x40;&#x40;SERVICENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Restituisce il nome della chiave del Registro di sistema in base a cui viene eseguito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La funzione @@SERVICENAME restituisce MSSQLSERVER se l'istanza corrente è l'istanza predefinita. Restituisce invece il nome dell'istanza se si tratta di un'istanza denominata.  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
@@SERVICENAME  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguito come servizio denominato MSSQLServer.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'utilizzo di `@@SERVICENAME`.  
  
```  
SELECT @@SERVICENAME AS 'Service Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Service Name                    
------------------------------  
MSSQLSERVER                     
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di configurazione &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Gestire il servizio Motore di database](../../database-engine/configure-windows/manage-the-database-engine-services.md)  
  
  
