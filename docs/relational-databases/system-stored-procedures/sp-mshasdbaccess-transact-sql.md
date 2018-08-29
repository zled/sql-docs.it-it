---
title: sp_MShasdbaccess (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_MShasdbaccess
- sp_MShasdbaccess_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_MShasdbaccess
ms.assetid: a9a23b90-2c60-4460-80a7-d7e14cc5a6a8
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: be21ad6f70e49f2c89c0903bde127d9d23413edc
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43020549"
---
# <a name="spmshasdbaccess-transact-sql"></a>sp_MShasdbaccess (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza il nome e il proprietario di tutti i database a cui l'utente può accedere.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_MShasdbaccess      
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="permissions"></a>Permissions  
 Eseguire l'autorizzazione viene concessa per il **pubblica** ruolo.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.sysdatabases &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql.md)  
  
  
