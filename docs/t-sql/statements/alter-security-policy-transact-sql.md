---
title: MODIFICARE il criterio di sicurezza (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SECURITY_POLICY_TSQL
- ALTER SECURITY POLICY
- ALTER_SECURITY_TSQL
- ALTER SECURITY
dev_langs: TSQL
helpviewer_keywords: ALTER SECURITY POLICY statement
ms.assetid: a8efc37e-113d-489c-babc-b914fea2c316
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0b420b7b73af8f32d2de9dac39cc4f57b41680c7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-security-policy-transact-sql"></a>MODIFICARE il criterio di sicurezza (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Modifica un criterio di sicurezza.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```tsql  
ALTER SECURITY POLICY schema_name.security_policy_name   
    (  
        { ADD { FILTER | BLOCK } PREDICATE tvf_schema_name.security_predicate_function_name   
           ( { column_name | arguments } [ , …n ] ) ON table_schema_name.table_name   
           [ <block_dml_operation> ]  }   
        | { ALTER { FILTER | BLOCK } PREDICATE tvf_schema_name.new_security_predicate_function_name   
             ( { column_name | arguments } [ , …n ] ) ON table_schema_name.table_name   
           [ <block_dml_operation> ] }  
        | { DROP { FILTER | BLOCK } PREDICATE ON table_schema_name.table_name }   
        | [ <additional_add_alter_drop_predicate_statements> [ , ...n ] ]  
    )    [ WITH ( STATE = { ON | OFF } ]  
    [ NOT FOR REPLICATION ]  
[;]  
  
<block_dml_operation>  
    [ { AFTER { INSERT | UPDATE } }   
    | { BEFORE { UPDATE | DELETE } } ]  
```  
  
## <a name="arguments"></a>Argomenti  
 security_policy_name  
 Nome del criterio di sicurezza. I nomi dei criteri sicurezza devono essere conformi alle regole per gli identificatori e devono essere univoci all'interno del database e rispetto al relativo schema.  
  
 schema_name  
 Nome dello schema a cui appartiene il criterio di sicurezza. *schema_name* è necessario a causa di associazione allo schema.  
  
 [FILTRO | BLOCCO]  
 Il tipo del predicato di sicurezza per la funzione associata alla tabella di destinazione. I predicati del filtro filtrano automaticamente le righe che sono disponibili per le operazioni di lettura. Predicati di blocco in modo esplicito le operazioni di scrittura di blocco che violano la funzione di predicato.  
  
 tvf_schema_name.security_predicate_function_name  
 Funzione con valori di tabella inline che verrà usata come predicato e che verrà applicata durante l'esecuzione di query su una tabella di destinazione. È possibile definire al massimo un predicato di sicurezza per una specifica operazione DML su una determinata tabella. La funzione con valori di tabella inline deve essere stata creata con l'opzione SCHEMABINDING.  
  
 { column_name | arguments }  
 Espressione o nome di colonna usato come parametro per la funzione di predicato di sicurezza. Tutte le colonne nella tabella di destinazione possono essere usate come argomenti per la funzione di predicato. È possibile usare espressioni che includono valori letterali, valori builtin ed espressioni che usano operatori aritmetici.  
  
 *table_schema_name.TABLE_NAME*  
 Tabella di destinazione a cui verrà applicato il predicato di sicurezza. Una singola tabella per una specifica operazione DML possono fare riferimento più criteri di sicurezza disabilitati, ma solo uno può essere abilitato in qualsiasi momento.  
  
 *\<block_dml_operation >*  
 La specifica operazione DML per cui verrà applicato il predicato di blocco. Specifica dopo che il predicato verrà valutato i valori delle righe dopo l'operazione DML (INSERT o UPDATE) eseguita. Specifica prima che il predicato verrà valutato i valori delle righe prima che l'operazione DML venga eseguita (UPDATE o DELETE). Se non è stata specificata alcuna operazione, il predicato verrà applicate a tutte le operazioni.  
  
 È possibile modificare l'operazione per il quale verrà applicato un predicato di blocco, perché l'operazione viene utilizzato per identificare in modo univoco il predicato. In alternativa, è necessario eliminare il predicato e aggiungerne uno nuovo per la nuova operazione.  
  
 WITH ( STATE = { ON | OFF } )  
 Abilita o disabilita il criterio di sicurezza per l'applicazione dei relativi predicati di sicurezza alle tabelle di destinazione. Se non specificato, il criterio di sicurezza creato è disabilitato.  
  
 NOT FOR REPLICATION  
 Indica che il criterio di sicurezza non deve essere eseguito quando un agente di replica modifica l'oggetto di destinazione. Per altre informazioni, vedere [Controllare il comportamento di trigger e vincoli durante la sincronizzazione &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md).  
  
 table_schema_name.table_name  
 Tabella di destinazione a cui verrà applicato il predicato di sicurezza. A una singola tabella possono fare riferimento più criteri di sicurezza disabilitati, ma è possibile abilitarne solo uno.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione ALTER SECURITY POLICY è nell'ambito di una transazione. L'esecuzione del rollback della transazione comporta il rollback anche per l'istruzione.  
  
 Quando si utilizzano le funzioni di predicato con tabelle con ottimizzazione per la memoria, è necessario includere i criteri di sicurezza **SCHEMABINDING** e utilizzare il **WITH NATIVE_COMPILATION** hint per la compilazione. L'argomento SCHEMABINDING non può essere modificato con l'istruzione ALTER perché si applica a tutti i predicati. Per modificare l'associazione allo schema è necessario eliminare e ricreare i criteri di sicurezza.  
  
 I predicati di blocco vengono valutati dopo l'esecuzione dell'operazione DML corrispondente. Pertanto, una query READ UNCOMMITTED possa vedere valori temporanei che sarà possibile eseguire il rollback.  
  
## <a name="permissions"></a>Permissions  
 Richiede l'autorizzazione ALTER ANY SECURITY POLICY.  
  
 Inoltre, per ogni predicato che viene aggiunto sono richieste le autorizzazioni seguenti:  
  
-   Le autorizzazioni SELECT e REFERENCES per la funzione usata come predicato.  
-   L'autorizzazione REFERENCES per la tabella di destinazione associata al criterio.  
-   L'autorizzazione REFERENCES per ogni colonna della tabella di destinazione usata come argomento.  
  
## <a name="examples"></a>Esempi  
 Negli esempi seguenti viene illustrato l'utilizzo del **ALTER SECURITY POLICY** sintassi. Per un esempio di uno scenario di criteri di sicurezza completa, vedere [sicurezza a livello di riga](../../relational-databases/security/row-level-security.md).  
  
### <a name="a-adding-an-additional-predicate-to-a-policy"></a>A. Aggiunta di un altro predicato a un criterio  
 La sintassi seguente modifica un criterio di sicurezza, aggiungendo un predicato del filtro per la tabella `mytable`.  
  
```  
ALTER SECURITY POLICY pol1   
    ADD FILTER PREDICATE schema_preds.SecPredicate(column1)   
    ON myschema.mytable;  
```  
  
### <a name="b-enabling-an-existing-policy"></a>B. Abilitazione di un criterio esistente  
 L'esempio seguente usa la sintassi di ALTER per abilitare un criterio di sicurezza.  
  
```  
ALTER SECURITY POLICY pol1 WITH ( STATE = ON );  
```  
  
### <a name="c-adding-and-dropping-multiple-predicates"></a>C. Aggiunta ed eliminazione di più predicati  
 La sintassi seguente modifica un criterio di sicurezza, aggiungendo i predicati del filtro per le tabelle `mytable1` e `mytable3` e rimuovendo il predicato del filtro per la tabella `mytable2`.  
  
```  
ALTER SECURITY POLICY pol1  
ADD FILTER PREDICATE schema_preds.SecPredicate1(column1)   
    ON myschema.mytable1,  
DROP FILTER PREDICATE   
    ON myschema.mytable2,  
ADD FILTER PREDICATE schema_preds.SecPredicate2(column2, 1)   
    ON myschema.mytable3;  
```  
  
### <a name="d-changing-the-predicate-on-a-table"></a>D. Modifica il predicato in una tabella  
 La sintassi seguente modifica il predicato del filtro esistente nella tabella mytable per farla diventare la funzione SecPredicate2.  
  
```  
ALTER SECURITY POLICY pol1  
    ALTER FILTER PREDICATE schema_preds.SecPredicate2(column1)  
        ON myschema.mytable;  
```  
  
### <a name="e-changing-a-block-predicate"></a>E. La modifica di un predicato di blocco  
 Modifica la funzione di predicato di blocco per un'operazione su una tabella.  
  
```  
ALTER SECURITY POLICY rls.SecPol  
    ALTER BLOCK PREDICATE rls.tenantAccessPredicate_v2(TenantId) 
    ON dbo.Sales AFTER INSERT;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza a livello di riga](../../relational-databases/security/row-level-security.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [DROP SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-security-policy-transact-sql.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [Sys. security_predicates &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)  
  
  
