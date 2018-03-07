---
title: Nome delle regole di confronto di SQL Server (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], SQL collations
- SQL collations
- names [SQL Server], collations
ms.assetid: 56483d24-add7-483d-9b96-c6fda460ddbc
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0c0c0aee8f1d0b0694f60477b69f4a364a6918ff
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-collation-name-transact-sql"></a>Nome delle regole di confronto di SQL Server (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Singola stringa che specifica il nome regole di confronto per le regole di confronto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono supportate le regole di confronto di Windows. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è inoltre supportato un numero limitato (<80) di regole di confronto definite regole di confronto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sviluppate prima che le regole di confronto di Windows venissero supportate in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le regole di confronto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono ancora supportate per la compatibilità con le versioni precedenti, ma è consigliabile non utilizzarle per nuovi progetti di sviluppo. Per ulteriori informazioni sulle regole di confronto di Windows, vedere [windows_collation_name &#40; Transact-SQL &#41; ](../../t-sql/statements/windows-collation-name-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
<SQL_collation_name> :: =   
SQL_SortRules[_Pref]_CPCodepage_<ComparisonStyle>  
  
<ComparisonStyle> ::=  
_CaseSensitivity_AccentSensitivity | _BIN  
```  
  
## <a name="arguments"></a>Argomenti  
 *SortRules*  
 Stringa che identifica l'alfabeto o la lingua di cui vengono applicate le regole di ordinamento quando si specifica l'ordinamento del dizionario, ad esempio Latin1_General o Polish.  
  
 **PREF**  
 Specifica come preferenza l'uso del maiuscolo. Anche se nel confronto non viene applicata la distinzione tra maiuscole e minuscole, la versione maiuscola di una lettera precede la versione minuscola, se non vengono applicate altre distinzioni.  
  
 *Codepage*  
 Numero composto da 1 a 4 cifre che identifica la tabella codici usata dalle regole di confronto. **Cp1** specifica la tabella codici 1252, per tutte le altre tabelle codici il numero di pagina di codice completo è specificato. Ad esempio, **CP1251** specifica la tabella codici 1251 e **CP850** specifica la tabella codici 850.  
  
 *CaseSensitivity*  
 **CI** specifica tra maiuscole e minuscole, **CS** specifica tra maiuscole e minuscole.  
  
 *AccentSensitivity*  
 **AI** specifica accentati, **AS** specifica accentati.  
  
 **BIN**  
 Specifica che deve essere usato il tipo di ordinamento binario.  
  
## <a name="remarks"></a>Osservazioni  
 Per elencare le regole di confronto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supportati dal server, eseguire la query seguente.  
  
```  
SELECT * FROM sys.fn_helpcollations()   
WHERE name LIKE 'SQL%';  
```  

>  [!NOTE]  
>  Per l'ID di ordine di ordinamento 80, usare una delle regole di confronto di finestra con la tabella codici di 1250, ordinamento binario. ad esempio Albanian_BIN, Croatian_BIN, Czech_BIN, Romanian_BIN, Slovak_BIN, Slovenian_BIN.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [Costanti &#40; Transact-SQL &#41;](../../t-sql/data-types/constants-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [tabella &#40; Transact-SQL &#41;](../../t-sql/data-types/table-transact-sql.md)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)  
  
  
