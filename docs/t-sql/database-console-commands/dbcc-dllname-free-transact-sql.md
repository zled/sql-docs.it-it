---
title: DBCC nomedll (FREE) (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbcc_dllname_(FREE)_TSQL
- dllname
- dbcc dllname (FREE)
- FREE
- dbcc_dllname(FREE)_TSQL
- FREE_TSQL
- dllname_TSQL
- dbcc dllname(FREE)
dev_langs: TSQL
helpviewer_keywords:
- DLL unloading [SQL Server]
- DBCC dllname (FREE)
- freeing DLLs
- unloading DLLs
ms.assetid: 1eb71c17-fe15-430b-8916-e4e312dcf9c0
caps.latest.revision: "27"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ad6b900d45ef1c87c0aca0d961685c68a72a33d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-dllname-free-transact-sql"></a>DBCC dllname (FREE) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Scarica la stored procedure estesa specificata DLL dalla memoria.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
```sql
DBCC <dllname> ( FREE ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argomenti  
 \<*dllname*>  
 Nome della DLL da scaricare dalla memoria.  
  
 WITH NO_INFOMSGS  
 Disattiva tutti i messaggi informativi.  
  
## <a name="remarks"></a>Osservazioni
Quando si esegue una stored procedure estesa, la DLL rimane caricata nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fino alla chiusura del server. Questa istruzione consente di scaricare una DLL dalla memoria senza chiudere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per visualizzare i file DLL attualmente caricati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], eseguire **sp_helpextendedproc**
  
## <a name="result-sets"></a>Set di risultati  
Quando viene specificata una DLL valida, DBCC *NomeDLL* (FREE) restituisce:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Autorizzazioni  
È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** o al ruolo predefinito del database **db_owner** .
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente si presuppone che `xp_sample` viene implementata come xp_sample.dll ed è stata eseguita. DBCC \< *NomeDLL*> (FREE) Scarica il file xp_sample.dll associato il `xp_sample` procedure estesa.
  
```sql  
DBCC xp_sample (FREE);  
```  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Caratteristiche dell'esecuzione di stored procedure estese](../../relational-databases/extended-stored-procedures-programming/execution-characteristics-of-extended-stored-procedures.md)  
[sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)  
[sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
[sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)  
[Scaricamento di una DLL di stored procedure estesa](../../relational-databases/extended-stored-procedures-programming/unloading-an-extended-stored-procedure-dll.md)
  
  
