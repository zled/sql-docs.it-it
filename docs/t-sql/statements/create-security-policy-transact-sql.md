---
title: CREARE i criteri di sicurezza (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SECURITY_POLICY_TSQL
- CREATE SECURITY
- SECURITY
- CREATE_SECURITY_POLICY_TSQL
- CREATE_SECURITY_TSQL
- SECURITY POLICY
- SECURITY_TSQL
- CREATE SECURITY POLICY
dev_langs:
- TSQL
helpviewer_keywords:
- RLS
- CREATE SECURITY POLICY statement
- Row-Level Security
ms.assetid: d6ab70ee-0fa2-469c-96f6-a3c16d673bc8
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 53292dc3f9f5cbd36913276496084d4648f13520
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-security-policy-transact-sql"></a>CREARE i criteri di sicurezza (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Crea un criterio di sicurezza per la sicurezza a livello di riga.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```     
CREATE SECURITY POLICY [schema_name. ] security_policy_name    
    { ADD [ FILTER | BLOCK ] } PREDICATE tvf_schema_name.security_predicate_function_name   
      ( { column_name | arguments } [ , …n] ) ON table_schema_name. table_name    
      [ <block_dml_operation> ] , [ , …n] 
    [ WITH ( STATE = { ON | OFF }  [,] [ SCHEMABINDING = { ON | OFF } ] ) ]  
    [ NOT FOR REPLICATION ] 
[;]  
  
<block_dml_operation>  
    [ { AFTER { INSERT | UPDATE } }   
    | { BEFORE { UPDATE | DELETE } } ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *security_policy_name*  
 Nome del criterio di sicurezza. I nomi dei criteri sicurezza devono essere conformi alle regole per gli identificatori e devono essere univoci all'interno del database e rispetto al relativo schema.  
  
 *schema_name*  
 Nome dello schema a cui appartiene il criterio di sicurezza. *schema_name* è necessario a causa di associazione allo schema.  
  
 [FILTRO | BLOCCO]  
 Il tipo del predicato di sicurezza per la funzione associata alla tabella di destinazione. I predicati del filtro filtrano automaticamente le righe che sono disponibili per le operazioni di lettura. Predicati di blocco in modo esplicito le operazioni di scrittura di blocco che violano la funzione di predicato.  
  
 *tvf_schema_name.security_predicate_function_name*  
 Funzione con valori di tabella inline che verrà usata come predicato e che verrà applicata durante l'esecuzione di query su una tabella di destinazione. È possibile definire al massimo un predicato di sicurezza per una specifica operazione DML su una determinata tabella. La funzione con valori di tabella inline deve essere stata creata con l'opzione SCHEMABINDING.  
  
 { *column_name* | *argomenti* }  
 Espressione o nome di colonna usato come parametro per la funzione di predicato di sicurezza. Tutte le colonne nella tabella di destinazione possono essere usate come argomenti per la funzione di predicato. È possibile usare espressioni che includono valori letterali, valori builtin ed espressioni che usano operatori aritmetici.  
  
 *table_schema_name.TABLE_NAME*  
 Tabella di destinazione a cui verrà applicato il predicato di sicurezza. Una singola tabella per una specifica operazione DML possono fare riferimento più criteri di sicurezza disabilitati, ma solo uno può essere abilitato in qualsiasi momento.  
  
 *\<block_dml_operation >* la specifica operazione DML per cui verrà applicato il predicato di blocco. Specifica dopo che il predicato verrà valutato i valori delle righe dopo l'operazione DML (INSERT o UPDATE) eseguita. Specifica prima che il predicato verrà valutato i valori delle righe prima che l'operazione DML venga eseguita (UPDATE o DELETE). Se non è stata specificata alcuna operazione, il predicato verrà applicate a tutte le operazioni.  
  
 [STATO = {ON | **OFF** }]  
 Abilita o disabilita il criterio di sicurezza per l'applicazione dei relativi predicati di sicurezza alle tabelle di destinazione. Se non specificato, il criterio di sicurezza creato è abilitato.  
  
 [SCHEMABINDING = {ON | OFF}]  
 Indica se tutte le funzioni di predicato nei criteri devono essere create con l'opzione SCHEMABINDING. Per impostazione predefinita, è necessario creare tutte le funzioni con l'opzione SCHEMABINDING.  
  
 NOT FOR REPLICATION  
 Indica che il criterio di sicurezza non deve essere eseguito quando un agente di replica modifica l'oggetto di destinazione. Per altre informazioni, vedere [Controllare il comportamento di trigger e vincoli durante la sincronizzazione &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md).  
  
 [*table_schema_name*.] *table_name*  
 Tabella di destinazione a cui verrà applicato il predicato di sicurezza. A una singola tabella possono fare riferimento più criteri di sicurezza disabilitati, ma è possibile abilitarne solo uno.  
  
## <a name="remarks"></a>Osservazioni  
 Quando si utilizzano le funzioni di predicato con tabelle con ottimizzazione per la memoria, è necessario includere **SCHEMABINDING** e utilizzare il **WITH NATIVE_COMPILATION** hint per la compilazione.  
  
 I predicati di blocco vengono valutati dopo l'esecuzione dell'operazione DML corrispondente. Pertanto, una query READ UNCOMMITTED possa vedere valori temporanei che sarà possibile eseguire il rollback.  
  
## <a name="permissions"></a>Permissions  
 Richiede l'autorizzazione ALTER ANY SECURITY POLICY e l'autorizzazione ALTER per lo schema.  
  
 Inoltre, per ogni predicato che viene aggiunto sono richieste le autorizzazioni seguenti:  
  
-   Le autorizzazioni SELECT e REFERENCES per la funzione usata come predicato.  
  
-   L'autorizzazione REFERENCES per la tabella di destinazione associata al criterio.  
  
-   L'autorizzazione REFERENCES per ogni colonna della tabella di destinazione usata come argomento.  
  
## <a name="examples"></a>Esempi  
 Gli esempi seguenti illustrano l'uso della sintassi di **CREATE SECURITY POLICY** . Per un esempio di uno scenario di criteri di sicurezza completa, vedere [sicurezza a livello di riga](../../relational-databases/security/row-level-security.md).  
  
### <a name="a-creating-a-security-policy"></a>A. Creazione di un criterio di sicurezza  
 La sintassi seguente crea un criterio di sicurezza con un predicato del filtro per la tabella Customer e lascia il criterio di sicurezza disabilitato.  
  
```  
CREATE SECURITY POLICY [FederatedSecurityPolicy]   
ADD FILTER PREDICATE [rls].[fn_securitypredicate]([CustomerId])   
ON [dbo].[Customer];  
```  
  
### <a name="b-creating-a-policy-that-affects-multiple-tables"></a>B. Creazione di un criterio che interessa più tabelle  
 La sintassi seguente crea un criterio di sicurezza con tre predicati del filtro per tre tabelle diverse e abilita il criterio di sicurezza.  
  
```  
CREATE SECURITY POLICY [FederatedSecurityPolicy]   
ADD FILTER PREDICATE [rls].[fn_securitypredicate1]([CustomerId])   
    ON [dbo].[Customer],  
ADD FILTER PREDICATE [rls].[fn_securitypredicate1]([VendorId])   
    ON [dbo].[ Vendor],  
ADD FILTER PREDICATE [rls].[fn_securitypredicate2]([WingId])   
    ON [dbo].[Patient]  
WITH (STATE = ON);  
```  
  
### <a name="c-creating-a-policy-with-multiple-types-of-security-predicates"></a>C. Creazione di un criterio con più tipi di predicati di sicurezza  
 Aggiunta di un predicato del filtro sia un predicato di blocco alla tabella Sales.  
  
```  
CREATE SECURITY POLICY rls.SecPol  
    ADD FILTER PREDICATE rls.tenantAccessPredicate(TenantId) ON dbo.Sales,  
    ADD BLOCK PREDICATE rls.tenantAccessPredicate(TenantId) ON dbo.Sales AFTER INSERT;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza a livello di riga](../../relational-databases/security/row-level-security.md)   
 [ALTER SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-security-policy-transact-sql.md)   
 [DROP SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-security-policy-transact-sql.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [Sys. security_predicates &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)  
  
  


