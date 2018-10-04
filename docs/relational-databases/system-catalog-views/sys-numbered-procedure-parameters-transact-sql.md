---
title: numbered_procedure_parameters (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- numbered_procedure_parameters_TSQL
- sys.numbered_procedure_parameters_TSQL
- numbered_procedure_parameters
- sys.numbered_procedure_parameters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.numbered_procedure_parameters catalog view
ms.assetid: a441d46d-1f30-41c2-8d94-e9442f59786e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 437b25af01544a1df6197a0d63e21ae2f7bee605
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47824239"
---
# <a name="sysnumberedprocedureparameters-transact-sql"></a>sys.numbered_procedure_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni parametro di una stored procedure numerata. Quando si crea una stored procedure numerata, alla procedura di base è associato il numero 1. Alle successive procedure sono associati i numeri 2, 3 e così via. **numbered_procedure_parameters** contiene le definizioni dei parametri per tutte le successive procedure, dalla numero 2 e versioni successive. In questa vista non sono visualizzati i parametri per la stored procedure di base (numero 1). La stored procedure di base è simile a una stored procedure non numerata. Pertanto, i relativi parametri sono rappresentati nel [Sys. Parameters (Transact-SQL)](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md).  
  
> [!IMPORTANT]  
>  Le stored procedure numerate sono deprecate. pertanto non è consigliabile utilizzarle. Un evento DEPRECATION_ANNOUNCEMENT viene generato quando viene compilata una query che utilizza questa vista del catalogo.  
  
> [!NOTE]  
>  I parametri XML e CLR non sono supportati per le stored procedure numerate.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID dell'oggetto a cui appartiene il parametro.|  
|**procedure_number**|**smallint**|Numero della procedura nell'oggetto, maggiore o uguale a 2.|  
|**name**|**sysname**|Nome del parametro. È univoco all'interno **procedure_number**.|  
|**parameter_id**|**int**|ID del parametro. È univoco all'interno di **procedure_number**.|  
|**system_type_id**|**tinyint**|ID del tipo di sistema del parametro|  
|**user_type_id**|**int**|ID del tipo di parametro, come definito dall'utente.|  
|**max_length**|**smallint**|Lunghezza massima del parametro in byte.<br /><br /> -1 = Il tipo di dati della colonna è varchar(max), nvarchar(max) o varbinary(max).|  
|**Precisione**|**tinyint**|Precisione del parametro se numerica. In caso contrario 0.|  
|**Scalabilità**|**tinyint**|Scala del parametro se numerica. In caso contrario 0.|  
|**is_output**|**bit**|1 = Il parametro è un parametro di output o restituito. In caso contrario 0|  
|**is_cursor_ref**|**bit**|1 = Il parametro è un parametro di riferimento a un cursore.|  
  
> [!NOTE]  
>  I parametri XML e CLR non sono supportati per le stored procedure numerate.  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
