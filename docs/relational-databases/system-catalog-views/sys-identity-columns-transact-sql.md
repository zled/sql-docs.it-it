---
title: Sys. identity_columns (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- identity_columns
- sys.identity_columns
- sys.identity_columns_TSQL
- identity_columns_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.identity_columns catalog view
ms.assetid: 97ee01e6-9c9e-4fd9-884b-68b4084669d5
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2669f1373bedec1256d3071b9fe1f85b7c8dab8f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysidentitycolumns-transact-sql"></a>sys.identity_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contiene una riga per ogni colonna Identity.  
  
 Il **Sys. identity_columns** visualizzazione ereditate le righe di **Columns** visualizzazione. Il **Sys. identity_columns** vista restituisce le colonne di **Sys. Columns** vista, più il **seed_value**, **increment_value**, **last_value**, e **is_not_for_replication** colonne. Per altre informazioni, vedere [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**\<colonne ereditate da Sys. Columns >**||Il **Sys. identity_columns** vista restituisce tutte le colonne di **Columns** visualizzazione. Vengono inoltre restituite le colonne aggiuntive descritte di seguito. Per una descrizione delle colonne che la **Sys. identity_columns** visualizzazione erediti da **Columns**, vedere [Columns &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).|  
|**seed_value**|**sql_variant**|Valore di inizializzazione per la colonna Identity. Il tipo di dati del valore di inizializzazione è uguale al tipo di dati della colonna.|  
|**increment_value**|**sql_variant**|Valore di incremento per la colonna Identity. Il tipo di dati del valore di inizializzazione è uguale al tipo di dati della colonna.|  
|**last_value**|**sql_variant**|Ultimo valore generato per la colonna Identity. Il tipo di dati del valore di inizializzazione è uguale al tipo di dati della colonna.|  
|**is_not_for_replication**|**bit**|Per la colonna Identity è dichiarata l'opzione NOT FOR REPLICATION.|  
  
> [!NOTE]  
>  Per creare un numero a incremento automatico da usare in più tabelle o da chiamare dalle applicazioni senza fare riferimento ad alcuna tabella, vedere [Numeri di sequenza](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Domande frequenti sull'esecuzione di query nel catalogo di sistema di SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
