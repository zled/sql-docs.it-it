---
title: sys.dm_filestream_file_io_handles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_filestream_file_io_handles
- sys.dm_filestream_file_io_handles
- dm_filestream_file_io_handles_TSQL
- sys.dm_filestream_file_io_handles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_filestream_file_io_handle catalog view
ms.assetid: e59632f4-3292-419f-9217-ca375749f1a5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cde19779c178b8064e6b20a3ae39bbfb7f5b96f6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47847159"
---
# <a name="sysdmfilestreamfileiohandles-transact-sql"></a>sys.dm_filestream_file_io_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzati gli handle di file conosciuti dal proprietario dello spazio dei nomi (NSO, Namespace Owner). Gli handle di FileStream che un client ottenuto tramite **OpenSqlFilestream** vengono visualizzati in questa vista.  
  
|colonna|Tipo|Description|  
|------------|----------|-----------------|  
|**handle_context_address**|**varbinary(8)**|Viene mostrato l'indirizzo della struttura NSO interna associata all'handle del client. Ammette i valori Null.|  
|**creation_request_id**|**int**|Viene mostrato un campo della richiesta di I/O REQ_PRE_CREATE utilizzata per creare questo handle. Non ammette i valori Null.|  
|**creation_irp_id**|**int**|Viene mostrato un campo della richiesta di I/O REQ_PRE_CREATE utilizzata per creare questo handle. Non ammette i valori Null|  
|**handle_id**|**int**|Viene mostrato l'ID univoco di questo handle assegnato dal driver. Non ammette i valori Null.|  
|**creation_client_thread_id**|**varbinary(8)**|Viene mostrato un campo della richiesta di I/O REQ_PRE_CREATE utilizzata per creare questo handle. Ammette i valori Null.|  
|**creation_client_process_id**|**varbinary(8)**|Viene mostrato un campo della richiesta di I/O REQ_PRE_CREATE utilizzata per creare questo handle. Ammette i valori Null.|  
|**filestream_transaction_id**|**varbinary(128)**|Viene mostrato l'ID della transazione associata all'handle specificato. Si tratta del valore restituito per il **get_filestream_transaction_context** (funzione). Usare questo campo per aggiungere il **DM filestream_file_io_requests** visualizzazione. Ammette i valori Null.|  
|**access_type**|**nvarchar(60)**|Non ammette i valori Null.|  
|**logical_path**|**nvarchar(256)**|Viene mostrato il nome del percorso logico del file aperto da questo handle. Questo è lo stesso nome di percorso restituito dal **. PathName** metodo di **varbinary**(**max**) filestream. Ammette i valori Null.|  
|**physical_path**|**nvarchar(256)**|Viene mostrato il nome del percorso NTFS effettivo del file. Questo è lo stesso nome percorso restituito dal **. PhysicalPathName** metodo per il **varbinary**(**max**) filestream. Viene abilitato dal flag di traccia 5556. Ammette i valori Null.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [FileStream e FileTable DMV &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  
