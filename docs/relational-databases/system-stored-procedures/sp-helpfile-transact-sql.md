---
title: sp_helpfile (Transact-SQL) | Microsoft Docs
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
- sp_helpfile
- sp_helpfile_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpfile
ms.assetid: 1546e0ae-5a99-4e01-9eb9-d147fa65884c
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 74acb22b50ce918f070c817cb8954b46e47bb876
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43023839"
---
# <a name="sphelpfile-transact-sql"></a>sp_helpfile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce i nomi fisici e gli attributi dei file associati al database corrente. Utilizzare questa stored procedure per determinare i nomi dei file da collegare o scollegare dal server.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpfile [ [ @filename= ] 'name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@filename =** ] **'***nome***'**  
 Nome logico di qualsiasi file nel database corrente. *nome* viene **sysname**, con un valore predefinito è NULL. Se *nome* viene omesso, vengono restituiti gli attributi di tutti i file nel database corrente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome logico del file.|  
|**fileid**|**smallint**|Identificatore numerico del file. Non viene restituito se *name* omette *.*|  
|**Nome del file**|**nchar(260)**|Nome fisico del file.|  
|**filegroup**|**sysname**|Filegroup a cui appartiene il file.<br /><br /> NULL = Il file è un file di log. Questo tipo di file non viene mai incluso in un filegroup.|  
|**size**|**nvarchar(15)**|Dimensione del file in kilobyte.|  
|**maxsize**|**nvarchar(15)**|Dimensioni massime consentite per il file. Se questo campo include il valore UNLIMITED, le dimensioni del file possono aumentare fino a riempire il disco.|  
|**aumento delle dimensioni**|**nvarchar(15)**|Incremento per l'aumento delle dimensioni del file. Indica la quantità di spazio aggiunta al file ogni volta che è richiesto spazio aggiuntivo.<br /><br /> 0 = la dimensione del file è fissa e non aumenterà.|  
|**Utilizzo**|**varchar(9)**|Per file di dati, il valore è **'solo data'** e per il file di log è il valore **'di log solo'**.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sui file nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfile;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database le Stored procedure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfilegroup-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Filegroup e file di database](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
