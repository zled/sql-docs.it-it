---
title: AUTORIZZAZIONI (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PERMISSIONS_TSQL
- PERMISSIONS
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], verifying
- current permission status
- users [SQL Server], permissions status
- checking permission status
- security [SQL Server], permissions
- verifying permission status
- testing permissions
- PERMISSIONS function
ms.assetid: 81625a56-b160-4424-91c5-1ce8b259a8e6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d1d8b8fff2313559c2a076ed761d0792fafd5001
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="permissions-transact-sql"></a>PERMISSIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un valore contenente una mappa di bit che indica le autorizzazioni per le istruzioni, gli oggetti o le colonne associati all'utente corrente.  
  
 **Importante** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] utilizzare [fn_my_permissions](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md) e [Has_Perms_By_Name](../../t-sql/functions/has-perms-by-name-transact-sql.md) invece. L'utilizzo della funzione PERMISSIONS può comportare una riduzione delle prestazioni.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PERMISSIONS ( [ objectid [ , 'column' ] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *ObjectID*  
 ID di un'entità a sicurezza diretta. Se *objectid* viene omesso, il valore bitmap include le autorizzazioni di istruzione per l'utente corrente; in caso contrario, la mappa di bit include le autorizzazioni per l'entità a protezione diretta per l'utente corrente. L'entità a sicurezza diretta specificata deve essere inclusa nel database corrente. Utilizzare il [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md) funzione per determinare il *objectid* valore.  
  
 **'** *colonna* **'**  
 Nome facoltativo di una colonna di cui si desidera ottenere informazioni sulle autorizzazioni. La colonna deve essere un nome di colonna valido nella tabella specificata da *objectid*.  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 È possibile utilizzare l'istruzione PERMISSIONS per determinare se l'utente corrente dispone delle autorizzazioni necessarie per eseguire un'istruzione o per concedere un'autorizzazione a un altro utente.  
  
 Le informazioni restituite sono mappe di 32 bit.  
  
 I 16 bit inferiori indicano autorizzazioni concesse all'utente e autorizzazioni valide per i gruppi di Windows o per i ruoli predefiniti del server di cui l'utente corrente è membro. Ad esempio, un valore restituito di 66 (valore esadecimale 0x42), se non si *objectid* è specificato, indica che l'utente disponga dell'autorizzazione per eseguire le istruzioni di BACKUP DATABASE (valore decimale 64) e di CREATE TABLE (valore decimale 2).  
  
 I 16 bit superiori indicano le autorizzazioni che l'utente può concedere ad altri utenti tramite l'istruzione GRANT. Questi bit vengono interpretati esattamente come i 16 bit inferiori descritti nelle tabelle riportate di seguito, con la sola differenza che sono spostati a sinistra di 16 bit, ovvero moltiplicati per 65536. Ad esempio, 0x8 (valore decimale 8) è il bit che indica l'autorizzazione INSERT quando un *objectid* specificato. 0x80000 (valore decimale 524288) indica invece la capacità di concedere l'autorizzazione INSERT tramite l'istruzione GRANT in quanto 524288 = 8 x 65536.  
  
 A causa dell'appartenenza ai ruoli è possibile che un utente che non dispone delle autorizzazioni necessarie per eseguire un'istruzione sia comunque in grado di concedere tale autorizzazione a un altro utente.  
  
 Nella tabella seguente vengono descritti i bit utilizzati per le autorizzazioni di istruzione (*objectid* non è specificato).  
  
|Bit (dec)|Bit (hex)|Autorizzazione per le istruzioni|  
|-----------------|-----------------|--------------------------|  
|1|0x1|CREATE DATABASE (solo per il database master)|  
|2|0x2|CREATE TABLE|  
|4|0x4|CREATE PROCEDURE|  
|8|0x8|CREATE VIEW|  
|16|0x10|CREATE RULE|  
|32|0x20|CREATE DEFAULT|  
|64|0x40|BACKUP DATABASE|  
|128|0x80|BACKUP LOG|  
|256|0x100|Riservato|  
  
 La tabella seguente illustra i bit utilizzati per autorizzazioni per gli oggetti che vengono restituite quando solo *objectid* specificato.  
  
|Bit (dec)|Bit (hex)|Autorizzazione per le istruzioni|  
|-----------------|-----------------|--------------------------|  
|1|0x1|SELECT ALL|  
|2|0x2|UPDATE ALL|  
|4|0x4|REFERENCES ALL|  
|8|0x8|INSERT|  
|16|0x10|DELETE|  
|32|0x20|EXECUTE (solo procedure)|  
|4096|0x1000|SELECT ANY (almeno una colonna)|  
|8192|0x2000|UPDATE ANY|  
|16384|0x4000|REFERENCES ANY|  
  
 La tabella seguente illustra i bit utilizzati per autorizzazioni per gli oggetti a livello di colonna che vengono restituite quando entrambi *objectid* e vengono specificati di colonna.  
  
|Bit (dec)|Bit (hex)|Autorizzazione per le istruzioni|  
|-----------------|-----------------|--------------------------|  
|1|0x1|SELECT|  
|2|0x2|UPDATE|  
|4|0x4|REFERENCES|  
  
 Un valore NULL viene restituito quando un parametro specificato è NULL o non valido (ad esempio, un *objectid* o una colonna che non esiste). I valori in bit delle autorizzazioni non applicabili, ad esempio l'autorizzazione EXECUTE (bit 0x20) per una tabella, non sono definiti.  
  
 Per determinare i vari set di bit della mappa di bit restituita dalla funzione PERMISSIONS, utilizzare l'operatore AND bit per bit (&).  
  
 Per ottenere un elenco delle autorizzazioni per un utente del database corrente, è inoltre possibile eseguire la stored procedure di sistema sp_helprotect.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-the-permissions-function-with-statement-permissions"></a>A. Utilizzo della funzione PERMISSIONS con le autorizzazioni per le istruzioni  
 Nell'esempio seguente si determina se l'utente corrente può eseguire l'istruzione `CREATE TABLE`.  
  
```  
IF PERMISSIONS()&2=2  
   CREATE TABLE test_table (col1 INT)  
ELSE  
   PRINT 'ERROR: The current user cannot create a table.';  
```  
  
### <a name="b-using-the-permissions-function-with-object-permissions"></a>B. Utilizzo della funzione PERMISSIONS con le autorizzazioni per gli oggetti  
 Nell'esempio seguente si determina se l'utente corrente può inserire una riga di dati nella tabella `Address` del database `AdventureWorks2012`.  
  
```  
IF PERMISSIONS(OBJECT_ID('AdventureWorks2012.Person.Address','U'))&8=8   
   PRINT 'The current user can insert data into Person.Address.'  
ELSE  
   PRINT 'ERROR: The current user cannot insert data into Person.Address.';  
```  
  
### <a name="c-using-the-permissions-function-with-grantable-permissions"></a>C. Utilizzo della funzione PERMISSIONS con autorizzazioni che possono essere concesse  
 Nell'esempio seguente si determina se l'utente corrente può concedere a un altro utente l'autorizzazione INSERT per la tabella `Address` del database `AdventureWorks2012`.  
  
```  
IF PERMISSIONS(OBJECT_ID('AdventureWorks2012.Person.Address','U'))&0x80000=0x80000  
   PRINT 'INSERT on Person.Address is grantable.'  
ELSE  
   PRINT 'You may not GRANT INSERT permissions on Person.Address.';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Object_id &#40; Transact-SQL &#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_helprotect &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [Funzioni di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  
