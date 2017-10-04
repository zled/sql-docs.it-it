---
title: ELIMINARE il formato di FILE esterno (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8cf9009b-59f9-4aac-bef1-dcf2cf0708b2
caps.latest.revision: 12
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 25719f7617cbb75b1b9467a00c392f703a9710ac
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-external-file-format-transact-sql"></a>ELIMINARE il formato di FILE esterno (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Rimuove un formato di file esterno PolyBase.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Drop an external file format  
DROP EXTERNAL FILE FORMAT external_file_format_name  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *external_file_format_name*  
 Il nome del formato di file esterno da eliminare.  
  
## <a name="metadata"></a>Metadati  
 Per visualizzare un elenco di formati di file esterni, utilizzare il [sys.external_file_formats &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md) vista di sistema.  
  
```  
SELECT * FROM sys.external_file_formats;  
```  
  
## <a name="permissions"></a>Permissions  
 È necessario modificare qualsiasi formato di FILE esterno.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Eliminazione di un formato di file esterni non rimuove i dati esterni.  
  
## <a name="locking"></a>Utilizzo di blocchi  
 Acquisisce un blocco condiviso per l'oggetto formato di file esterno.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-basic-syntax"></a>A. Utilizzando la sintassi di base  
  
```  
DROP EXTERNAL FILE FORMAT myfileformat;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-using-basic-syntax"></a>B. Utilizzando la sintassi di base  
  
```  
DROP EXTERNAL FILE FORMAT myfileformat;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  


