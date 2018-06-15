---
title: sp_pdw_remove_network_credentials (SQL Data Warehouse) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: c12696a2-5939-402b-9866-8a837ca4c0a3
caps.latest.revision: 9
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 78f4dd7ad5c76159413c7dbdd382f6c6cecc3807
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33700234"
---
# <a name="sppdwremovenetworkcredentials-sql-data-warehouse"></a>sp_pdw_remove_network_credentials (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Questa operazione rimuove le credenziali di rete memorizzate nel [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] per accedere a una condivisione di file di rete. Ad esempio, utilizzare questa stored procedure per rimuovere l'autorizzazione per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] eseguire backup e ripristinare le operazioni in un server che si trova all'interno della propria rete.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_remove_network_credentials 'target_server_name'  
```  
  
## <a name="arguments"></a>Argomenti  
 '*target_server_name*'  
 Specifica il nome host del server di destinazione o un indirizzo IP. Le credenziali per accedere a questo server verranno rimosso dal [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Questo non modificare o rimuovere tutte le autorizzazioni nel server di destinazione effettiva gestita dal proprio team.  
  
 *target_server_name* è definito come nvarchar(337).  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede **ALTER SERVER STATE** autorizzazione.  
  
## <a name="error-handling"></a>Gestione degli errori  
 Si verifica un errore se le credenziali di rimozione non riesce sul nodo di controllo e tutti i nodi di calcolo.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Questa stored procedure rimuove l'account NetworkService per le credenziali di rete [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. L'account NetworkService esegue ogni istanza del punto di migrazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del nodo di controllo e i nodi di calcolo. Ad esempio, quando viene eseguita un'operazione di backup, il nodo di controllo e ogni nodo di calcolo utilizzerà le credenziali dell'account NetworkService per accedere al server di destinazione.  
  
## <a name="metadata"></a>Metadati  
 Per elencare tutte le credenziali e per verificare le credenziali sono state rimosse, utilizzare [sys.dm_pdw_network_credentials &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md).  
  
 Per aggiungere le credenziali, utilizzare [sp_pdw_add_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md).  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-remove-credentials-for-performing-a-database-backup"></a>A. Rimuovere le credenziali per l'esecuzione di un backup del database  
 Nell'esempio seguente rimuove credenziali nome utente e password per l'accesso al server di destinazione che contiene un indirizzo IP di 10.192.147.63.  
  
```  
EXEC sp_pdw_remove_network_credentials '10.192.147.63';  
```  
  
  

