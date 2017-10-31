---
title: FIRMA DROP (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SIGNATURE
- DROP_SIGNATURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting signatures
- dropping signatures
- DROP SIGNATURE statement
- removing signatures
- signatures [SQL Server]
- digital signatures [SQL Server]
ms.assetid: 8a1fd8c5-0e75-4b2f-9d3c-c296bed56cc7
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 81823a549f608bdcddb631084904fb303a1ddc9f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-signature-transact-sql"></a>DROP SIGNATURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Elimina una firma digitale da una stored procedure, una funzione, un trigger o un assembly.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP [ COUNTER ] SIGNATURE FROM module_name   
    BY <crypto_list> [ ,...n ]  
  
<crypto_list> ::=  
    CERTIFICATE cert_name  
    | ASYMMETRIC KEY Asym_key_name  
```  
  
## <a name="arguments"></a>Argomenti  
 *nome_modulo*  
 Nome di una stored procedure, una funzione, un assembly o un trigger.  
  
 CERTIFICATO *cert_name*  
 Nome di un certificato con cui viene firmato un assembly, una stored procedure, una funzione o un trigger.  
  
 CHIAVE asimmetrica *Asym_key_name*  
 Nome di una chiave asimmetrica con cui viene firmato un assembly, una stored procedure, una funzione o un trigger.  
  
## <a name="remarks"></a>Osservazioni  
 Le informazioni sulle firme sono visibili nella vista di catalogo sys.crypt_properties.  
  
## <a name="permissions"></a>Permissions  
 Sono richieste l'autorizzazione ALTER per l'oggetto e l'autorizzazione CONTROL per il certificato o la chiave asimmetrica. Se una chiave privata associata è protetta tramite una password, è necessario che anche l'utente disponga della password.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente la firma del certificato `HumanResourcesDP` viene rimossa dalla stored procedure `HumanResources.uspUpdateEmployeeLogin`.  
  
```  
USE AdventureWorks2012;  
DROP SIGNATURE FROM HumanResources.uspUpdateEmployeeLogin   
    BY CERTIFICATE HumanResourcesDP;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [crypt_properties &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-crypt-properties-transact-sql.md)   
 [Aggiungi firma &#40; Transact-SQL &#41;](../../t-sql/statements/add-signature-transact-sql.md)  
  
  

