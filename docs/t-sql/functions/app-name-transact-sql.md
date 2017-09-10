---
title: APP_NAME (Transact-SQL) | Documenti Microsoft
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
- APP_NAME_TSQL
- APP_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- name checking for current session [SQL Server]
- sessions [SQL Server], application names
- applications [SQL Server], names
- current session application names
- APP_NAME function
ms.assetid: e491e192-9b30-4243-bc19-33c133fe08a8
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c4f63ae216bad0269415ac5e0aa57a7543500f0c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="appname-transact-sql"></a>APP_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce il nome dell'applicazione per la sessione corrente, se impostato dall'applicazione.
  
> [!IMPORTANT]  
>  Il nome dell'applicazione viene fornito dal client e non viene verificato in alcun modo. Non utilizzare **nome_app** come parte di un controllo di sicurezza.  
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
  
APP_NAME  ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
**nvarchar (128)**
  
## <a name="remarks"></a>Osservazioni  
Utilizzare **nome_app** quando si desidera eseguire azioni diverse per applicazioni diverse. Ad esempio, per formattare una data in modo diverso per applicazioni diverse o per restituire un messaggio informativo per alcune applicazioni.
  
Per impostare un nome di applicazione in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]nel **Connetti al motore di Database** la finestra di dialogo, fare clic su **opzioni**. Nel **Additional Connection Parameters** scheda, fornire un **app** attributo nel formato`;app='application_name'`
  
## <a name="examples"></a>Esempi  
L'esempio seguente consente di controllare se l'applicazione client che ha avviato il processo è una sessione di `SQL Server Management Studio` e fornisce una data sia nel formato US che ANSI.
  
```sql
USE AdventureWorks2012;  
GO  
IF APP_NAME() = 'Microsoft SQL Server Management Studio - Query'  
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 101) + '.';  
ELSE   
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 102) + '.';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
[Funzioni](../../t-sql/functions/functions.md)
  
  

