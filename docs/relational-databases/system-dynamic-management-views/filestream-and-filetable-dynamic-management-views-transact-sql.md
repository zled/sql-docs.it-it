---
title: FileStream e viste a gestione dinamica FileTable (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], dynamic management views
ms.assetid: e50a135d-6644-42a4-a0df-1c7a2b722051
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 240da66536adb16c140e625ccefd99c672f80574
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47794599"
---
# <a name="filestream-and-filetable-dynamic-management-views-transact-sql"></a>DMV per FILESTREAM e tabelle FileTable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  In questa sezione vengono descritti le DMV correlate alle caratteristiche FILESTREAM e FileTable.  
  
## <a name="filestream-dynamic-management-views-and-functions"></a>DMV e funzioni per FILESTREAM  
 [sys.dm_filestream_file_io_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql.md)  
 Consente di visualizzare gli handle di file transazionali attualmente aperti.  
  
 [sys.dm_filestream_file_io_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql.md)  
 Vengono visualizzate le richieste di input e output di file correnti.  
  
## <a name="filetable-dynamic-management-views-and-functions"></a>DMV e funzioni per tabelle FileTable  
 [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md)  
 Consente di visualizzare gli handle di file non transazionali aperti per dati di tabelle FileTable.  

## <a name="see-also"></a>Vedere anche
[FileStream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Tabelle Filetable](../../relational-databases/blob/filetables-sql-server.md)
<br>[Viste del catalogo Filestream e FileTable (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
<br>[Stored procedure di sistema per Filestream e tabelle FileTable (Transact-SQL)](../system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)
  
