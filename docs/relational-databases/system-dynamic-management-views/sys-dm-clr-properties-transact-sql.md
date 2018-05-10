---
title: sys.dm_clr_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_properties
- sys.dm_clr_properties_TSQL
- dm_clr_properties_TSQL
- dm_clr_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_properties dynamic management view
ms.assetid: 220d062f-d117-46e7-a448-06fe48db8163
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e648dc76c88bbacd81256063053d22fa17a268f6
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmclrproperties-transact-sql"></a>sys.dm_clr_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Restituisce una riga per ogni proprietà associata all'integrazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con Common Language Runtime (CLR), inclusi la versione e lo stato del CLR hosted. Il CLR hosted viene inizializzato tramite l'esecuzione di [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md), [ALTER ASSEMBLY](../../t-sql/statements/alter-assembly-transact-sql.md), o [DROP ASSEMBLY](../../t-sql/statements/drop-assembly-transact-sql.md) istruzioni, oppure eseguire qualsiasi routine CLR, tipo o del trigger. Il **Sys.dm clr_properties** vista non specifica se l'esecuzione del codice CLR utente è stata abilitata nel server. Esecuzione del codice CLR utente è abilitato tramite il [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) stored procedure con il [clr abilitato](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) opzione impostato su 1.  
  
 Il **Sys.dm clr_properties** vista contiene il **nome** e **valore** colonne. Ogni riga della vista include dettagli su una proprietà del CLR hosted. È possibile utilizzare questa vista per raccogliere informazioni sul CLR hosted, ad esempio la directory di installazione di CLR, la versione di CLR e lo stato corrente del CLR hosted. La vista consente inoltre di determinare se il codice dell'integrazione con CLR non funziona a causa di problemi relativi all'installazione di CLR nel computer server.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|Nome della proprietà.|  
|**Valore**|**nvarchar(128)**|Valore della proprietà.|  
  
## <a name="properties"></a>Proprietà  
 Il **directory** proprietà indica la directory che è stato installato .NET Framework per il server. Nel computer server possono essere presenti più installazioni di .NET Framework. Il valore di questa proprietà identifica l'installazione utilizzata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Il **versione** proprietà indica la versione di .NET Framework e CLR hosted nel server.  
  
 Il **Sys.dm clr_properties** vista a gestione dinamica può restituire sei diversi valori per il **stato** proprietà, che riflette lo stato del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR hosted. ovvero:  
  
-   Mscoree is not loaded.  
  
-   Mscoree is loaded.  
  
-   Locked CLR version with mscoree.  
  
-   CLR is initialized.  
  
-   CLR initialization permanently failed.  
  
-   CLR is stopped.  
  
 Il **Mscoree non caricato** e **viene caricato Mscoree** stati indicano l'avanzamento dell'inizializzazione del CLR hosted all'avvio del server e non probabilmente essere visualizzati.  
  
 Il **versione CLR bloccato con mscoree** stato può essere visualizzato in cui il CLR hosted non è in uso e, pertanto, non è ancora stato inizializzato. Il CLR hosted viene inizializzato alla prima esecuzione di un'istruzione DDL (ad esempio [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)) o un oggetto di database gestito viene eseguito.  
  
 Il **CLR viene inizializzato** stato indica che il CLR hosted è stato inizializzato correttamente. Si noti che questo stato non indica se l'esecuzione del codice CLR utente è stata abilitata. Se l'esecuzione del codice CLR utente viene prima abilitata e quindi disabilitata utilizzando la [!INCLUDE[tsql](../../includes/tsql-md.md)] [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) stored procedure, il valore di stato verrà comunque essere **CLR viene inizializzato**.  
  
 Il **inizializzazione di Common Language Runtime in modo permanente non è riuscita** stato indica che CLR hosted inizializzazione non riuscita. Le possibili cause sono la scarsa disponibilità di memoria o un errore nell'handshake host tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il CLR. In questo caso verrà generato il messaggio di errore 6512 o 6513.  
  
 Il **CLR viene arrestato stato** viene visualizzato solo se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in fase di arresto.  
  
## <a name="remarks"></a>Osservazioni  
 Le proprietà e i valori di questa vista potrebbero cambiare nelle versioni future di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a causa di miglioramenti della funzionalità di integrazione CLR.  
  
## <a name="permissions"></a>Autorizzazioni  
  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   

## <a name="examples"></a>Esempi  
 L'esempio seguente recupera informazioni relative al CLR hosted:  
  
```  
SELECT name, value   
FROM sys.dm_clr_properties;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative a Common Language Runtime &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
