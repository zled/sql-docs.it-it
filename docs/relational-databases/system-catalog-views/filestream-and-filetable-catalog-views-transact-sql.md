---
title: FileStream e viste del catalogo FileTable (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], catalog views
ms.assetid: 2c83a4a7-720b-4435-a3b5-788c29f56949
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9fcd323c157d43d0dad1546004f79f8e5affd60c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="filestream-and-filetable-catalog-views-transact-sql"></a>Viste del catalogo Filestream e FileTable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In questa sezione vengono descritte le viste del catalogo correlate alla caratteristica FileTable.  
  
## <a name="filestream-and-filetable-catalog-views-transact-sql"></a>FileStream e filetable viste del catalogo (Transact-SQL)
 [sys.database_filestream_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md)  
 Consente di visualizzare informazioni sul livello di accesso non transazionale a dati FILESTREAM in tabelle FileTable abilitato. Contiene una riga per ogni database nell'istanza di SQL Server.  
  
 [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql.md)  
 Contiene un elenco degli oggetti definiti dal sistema correlati a tabelle FileTable. Contiene una riga per ogni oggetto definito dal sistema.  
  
 [sys.filetables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filetables-transact-sql.md)  
 Restituisce una riga per ogni tabella FileTable. Eredita da **Sys. Tables**.  

## <a name="see-also"></a>Vedere anche
[FileStream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Tabelle Filetable](../../relational-databases/blob/filetables-sql-server.md)
<br>[FileStream e viste a gestione dinamica FileTable (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[FileStream e FileTable sistema Stored procedure (Transact-SQL)](../system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)
  
  
