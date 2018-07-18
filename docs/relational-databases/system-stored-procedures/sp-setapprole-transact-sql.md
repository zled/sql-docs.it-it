---
title: sp_setapprole (Transact-SQL) | Documenti Microsoft
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
- sp_setapprole
- sp_setapprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setapprole
ms.assetid: cf0901c0-5f90-42d4-9d5b-8772c904062d
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ac733afa3f8afef74a9d6affb16e0f9dbcd5b4a9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33259058"
---
# <a name="spsetapprole-transact-sql"></a>sp_setapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Attiva le autorizzazioni associate a un ruolo applicazione nel database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_setapprole [ @rolename = ] 'role',  
    [ @password = ] { encrypt N'password' }   
      |  
        'password' [ , [ @encrypt = ] { 'none' | 'odbc' } ]  
        [ , [ @fCreateCookie = ] true | false ]  
    [ , [ @cookie = ] @cookie OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@rolename =** ] **'***ruolo***'**  
 Nome del ruolo applicazione definito nel database corrente. *ruolo* viene **sysname**, non prevede alcun valore predefinito. *ruolo* deve esistere nel database corrente.  
  
 [  **@password =** ] **{crittografare N'***password***'}**  
 Password richiesta per attivare il ruolo applicazione. *password* viene **sysname**, non prevede alcun valore predefinito. *password* è possibile offuscare utilizzando ODBC **crittografare** (funzione). Quando si utilizza il **crittografare** funzione, la password deve essere convertita in una stringa Unicode inserendo **N** prima della virgoletta iniziale.  
  
 L'opzione crittografia non è supportata per le connessioni che utilizzano **SqlClient**.  
  
> [!IMPORTANT]  
>  ODBC **crittografare** funzione non fornisce la crittografia. È consigliabile evitare l'utilizzo di questa funzione per proteggere le password trasmesse in rete. Per informazioni da trasmettere in rete, utilizzare i protocolli SSL o IPSec.  
  
 **@encrypt = 'none'**  
 Indica che non è richiesto l'utilizzo di tecniche di offuscamento. La password viene passata a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come testo normale. Impostazione predefinita.  
  
 **@encrypt= 'odbc'**  
 Specifica che ODBC eseguirà l'offuscamento della password tramite ODBC **crittografare** funzione prima di inviare la password per il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. È possibile specificare questa opzione solo se si utilizza un client ODBC o il provider OLE DB per SQL Server.  
  
 [  **@fCreateCookie =** ] **true** | **false**  
 Specifica se è necessario creare un cookie. **true** viene implicitamente convertito in 1. **false** viene implicitamente convertito in 0.  
  
 [  **@cookie =** ]  **@cookie OUTPUT**  
 Specifica un parametro di output per il cookie. Il cookie viene generato solo se il valore di **@fCreateCookie** è **true**. **varbinary(8000)**  
  
> [!NOTE]  
>  Il parametro **OUTPUT** del cookie per **sp_setapprole** è attualmente documentato come **varbinary(8000)** che rappresenta la lunghezza massima corretta. Tuttavia, l'implementazione corrente restituisce **varbinary(50)**. Le applicazioni devono continuare a riservare **varbinary (8000)** in modo che l'applicazione continua a funzionare correttamente se il cookie restituito dimensioni aumentano in una versione futura.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Dopo un'applicazione attivato utilizzando ruolo **sp_setapprole**, tale ruolo rimane attivo fino a quando l'utente si disconnette dal server o esegue **sp_unsetapprole**. **sp_setapprole** può essere eseguita solo da direct [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni. **sp_setapprole** non può essere eseguita all'interno di un'altra stored procedure o una transazione definita dall'utente.  
  
 Per una panoramica dei ruoli applicazione, vedere [ruoli applicazione](../../relational-databases/security/authentication-access/application-roles.md).  
  
> [!IMPORTANT]  
>  È consigliabile utilizzare sempre una connessione crittografata quando si abilita un ruolo applicazione ed è necessario proteggere la password del ruolo applicazione per la trasmissione in rete.  
>   
>  Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC **crittografare** opzione non è supportata da **SqlClient**. Se è necessario archiviare credenziali, crittografarle con le funzioni CryptoAPI. Il parametro *password* viene archiviato come hash unidirezionale. Per mantenere la compatibilità con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], criteri di complessità delle password non viene applicato da **sp_addapprole**. Per applicare i criteri di complessità delle password, utilizzare [CREATE APPLICATION ROLE](../../t-sql/statements/create-application-role-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza **pubblica** e di conoscere la password per il ruolo.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-activating-an-application-role-without-the-encrypt-option"></a>A. Attivazione di un ruolo applicazione senza l'opzione encrypt  
 Nell'esempio seguente viene attivato il ruolo applicazione `SalesAppRole` con la password non crittografata `AsDeF00MbXX`, creato con autorizzazioni specifiche per l'applicazione utilizzata dall'utente corrente.  
  
```  
EXEC sp_setapprole 'SalesApprole', 'AsDeF00MbXX';  
GO  
```  
  
### <a name="b-activating-an-application-role-with-a-cookie-and-then-reverting-to-the-original-context"></a>B. Attivazione di un ruolo applicazione con un cookie e ripristino del contesto originale  
 Nell'esempio seguente viene attivato il ruolo applicazione `Sales11` con la password `fdsd896#gfdbfdkjgh700mM` e viene creato un cookie. Nell'esempio viene restituito il nome dell'utente corrente e quindi viene ripristinato il contesto originale tramite l'esecuzione di `sp_unsetapprole`.  
  
```  
DECLARE @cookie varbinary(8000);  
EXEC sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.   
GO   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [sp_unsetapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md)  
  
  
