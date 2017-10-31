---
title: ALTER CREDENTIAL (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/19/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER CREDENTIAL
- ALTER_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- passwords [SQL Server], credentials
- credentials [SQL Server], ALTER CREDENTIAL statement
- modifying credentials
- authentication [SQL Server], credentials
- ALTER CREDENTIAL statement
ms.assetid: b08899a6-c09e-4af4-91aa-a978ada79264
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d183da3fef3f2802803d4dc9771dbc72e601321a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-credential-transact-sql"></a>ALTER CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le proprietà di una credenziale.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER CREDENTIAL credential_name WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *credential_name*  
 Specifica il nome della credenziale che si desidera modificare.  
  
 IDENTITÀ **='***identity_name***'**  
 Specifica il nome dell'account da utilizzare per la connessione all'esterno del server.  
  
 SEGRETO **='***secret***'**  
 Specifica il segreto richiesto per l'autenticazione in uscita. *segreto* è facoltativo.  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene modificata una credenziale, i valori della proprietà *identity_name* e *secret* vengono reimpostate. Se l'argomento facoltativo SECRET viene omesso, il valore del segreto archiviato verrà impostato su NULL.  
  
 Il segreto viene crittografato tramite la chiave master del servizio. Se la chiave master del servizio viene rigenerata, il segreto verrà crittografato nuovamente tramite la nuova chiave master del servizio.  
  
 Informazioni sulle credenziali sono visibili nella **credentials** vista del catalogo.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER ANY CREDENTIAL. Se la credenziale è una credenziale di sistema, è richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-the-password-of-a-credential"></a>A. Modifica della password di una credenziale  
 Nell'esempio seguente viene modificato il segreto archiviato nella credenziale denominata `Saddles`. La credenziale include l'account di accesso di Windows `RettigB` e la relativa password. La nuova password viene aggiunta alla credenziale tramite la clausola SECRET.  
  
```  
ALTER CREDENTIAL Saddles WITH IDENTITY = 'RettigB',   
    SECRET = 'sdrlk8$40-dksli87nNN8';  
GO  
```  
  
### <a name="b-removing-the-password-from-a-credential"></a>B. Rimozione della password da una credenziale  
 Nell'esempio seguente la password viene rimossa da una credenziale denominata `Frames`. La credenziale include l'account di accesso di Windows `Aboulrus8` e una password. Dopo l'esecuzione dell'istruzione, la credenziale includerà una password NULL perché l'opzione SECRET è stata omessa.  
  
```  
ALTER CREDENTIAL Frames WITH IDENTITY = 'Aboulrus8';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Credenziali &#40; motore di Database &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [DROP CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-credential-transact-sql.md)   
 [ALTER DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

