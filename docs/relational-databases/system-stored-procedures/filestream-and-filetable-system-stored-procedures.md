---
title: FileStream e FileTable sistema Stored procedure (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-non-specified
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4d7df9111622f1674ecc677a7b2dcd7d22ae564b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="filestream-and-filetable-system-stored-procedures-transact-sql"></a>FileStream e FileTable sistema stored procedure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In questa sezione vengono descritte le stored procedure di sistema per la funzionalità Filestream e FileTable.  

## <a name="filestream-and-filetable-system-stored-procedures"></a>Stored procedure di sistema di FileStream e Filetable
  [sp_filestream_force_garbage_collection (Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)

   Forza il Garbage Collector di FILESTREAM all'esecuzione, eliminando qualsiasi file FILESTREAM non necessario.

  [sp_kill_filestream_non_transacted_handles (Transact-SQL)](filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)

  Consente di chiudere handle di file non transazionali per dati di tabelle FileTable.


## <a name="see-also"></a>Vedere anche
[FileStream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Tabelle Filetable](../../relational-databases/blob/filetables-sql-server.md)
<br>[FileStream e viste a gestione dinamica FileTable (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[FileStream e viste del catalogo FileTable (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
  
  
