---
title: sys.database_filestream_options (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- database_filestream_options
- sys.database_filestream_options_TSQL
- database_filestream_options_TSQL
- sys.database_filestream_options
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_filestream_options catalog view
ms.assetid: 3383c607-0bbc-456a-ab37-7230f4cbf0e9
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aec483bb817934a935c0c7ff2480f30539b83f17
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33181367"
---
# <a name="sysdatabasefilestreamoptions-transact-sql"></a>sys.database_filestream_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di visualizzare informazioni sul livello di accesso non transazionale a dati FILESTREAM in tabelle FileTable abilitato. Contiene una riga per ogni database nell'istanza di SQL Server.  
  
 Per altre informazioni sugli oggetti FileTable, vedere [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md).  
  
  
|Colonna|Tipo|Description|  
|------------|----------|-----------------|  
|**database_id**|**int**|ID del database. Questo valore è univoco all'interno dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**directory_name**|**nvarchar(255)**|Directory a livello di database per tutti gli spazi dei nomi della tabella FileTable.|  
|**non_transacted_access**|**tinyint**|Livello di accesso non transazionale a dati FILESTREAM abilitato. Il livello di accesso è impostato dall'opzione di NON_TRANSACTED_ACCESS il **CREATE DATABASE** o **ALTER DATABASE** istruzione.<br /><br /> I possibili valori di questa impostazione sono i seguenti:<br /><br /> 0: non abilitato. Si tratta del valore predefinito. Questo livello viene impostato specificando il valore **OFF** per il **NON_TRANSACTED_ACCESS** opzione.<br /><br /> 1: accesso in sola lettura. Questo livello viene impostato specificando il valore **READ_ONLY** per il **NON_TRANSACTED_ACCESS** opzione.<br /><br /> 3: accesso completo. Questo livello viene impostato specificando il valore **completo** per il **NON_TRANSACTED_ACCESS** opzione.<br /><br /> 5: in transizione verso READONLY.<br /><br /> 6: in transizione verso OFF.|  
|**non_transacted_access_desc**|**nvarchar(60)**|La descrizione del livello di accesso non transazionale identificato in non_transacted_access.<br /><br /> I possibili valori di questa impostazione sono i seguenti:<br /><br /> NONE: valore predefinito.<br /><br /> READ_ONLY<br /><br /> FULL<br /><br /> IN_TRANSITION_TO_READ_ONLY<br /><br /> IN_TRANSITION_TO_OFF|  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitazione dei prerequisiti per la tabella FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
  
