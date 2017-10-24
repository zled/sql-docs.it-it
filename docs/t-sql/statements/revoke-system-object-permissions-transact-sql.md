---
title: REVOCARE autorizzazioni per gli oggetti di sistema (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- REVOKE statement, system objects
- permissions [SQL Server], system objects
ms.assetid: 84983238-dd7d-45bd-99bb-52c9d8e96a87
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17b371e839d27c065628def8a7be56e6bef650a0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-system-object-permissions-transact-sql"></a>REVOKE - autorizzazioni per oggetti di sistema (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Revoca le autorizzazioni per oggetti di sistema come stored procedure, stored procedure estese, funzioni e viste a un'entità.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
REVOKE { SELECT | EXECUTE } ON [sys.]system_object FROM principal   
```  
  
## <a name="arguments"></a>Argomenti  
 [**sys.** ] .  
 Il **sys** qualificatore è obbligatorio solo quando si fa riferimento a viste del catalogo e viste a gestione dinamica.  
  
 *system_object*  
 Specifica l'oggetto per cui viene revocata l'autorizzazione.  
  
 *entità*  
 Specifica l'entità da cui viene revocata l'autorizzazione.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile utilizzare questa istruzione per revocare le autorizzazioni per particolari stored procedure, stored procedure estese, funzioni con valori di tabella, funzioni scalari, viste, viste del catalogo, viste di compatibilità, viste INFORMATION_SCHEMA, viste a gestione dinamica e tabelle di sistema installate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ognuno di questi oggetti di sistema esiste come record univoco nel database delle risorse (**mssqlsystemresource**). Il database delle risorse è di sola lettura. Un collegamento all'oggetto viene esposto come un record di **sys** schema di ogni database.  
  
 I nomi di procedure non qualificati vengono risolti dal processo predefinito di risoluzione dei nomi nel database delle risorse. Pertanto, il **sys.** qualificatore è obbligatorio solo quando si specificano viste del catalogo e viste a gestione dinamica.  
  
> [!CAUTION]  
>  La revoca di autorizzazioni per gli oggetti di sistema causerà errori nelle applicazioni che dipendono da tali oggetti. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilizza le viste del catalogo e potrebbe funzionare in modo imprevisto se si modificano le autorizzazioni predefinite per le viste del catalogo.  
  
 Non è supportata la revoca di autorizzazioni per i trigger e le colonne di oggetti di sistema.  
  
 Le autorizzazioni per gli oggetti di sistema vengono mantenute in caso di aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Gli oggetti di sistema sono visibili nella vista del catalogo [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md) .  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene revocata l'autorizzazione `EXECUTE` per `sp_addlinkedserver` al ruolo `public`.  
  
```  
REVOKE EXECUTE ON sys.sp_addlinkedserver FROM public;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. system_objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)   
 [Sys. database_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [GRANT-autorizzazioni per gli oggetti di sistema &#40; Transact-SQL &#41;](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)   
 [NEGARE autorizzazioni per gli oggetti di sistema &#40; Transact-SQL &#41;](../../t-sql/statements/deny-system-object-permissions-transact-sql.md)  
  
  

