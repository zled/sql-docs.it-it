---
title: sys.fn_xe_file_target_read_file (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_xe_file_target_read_file_TSQL
- fn_xe_file_target_read_file
- sys.fn_xe_file_target_read_file_TSQL
- sys.fn_xe_file_target_read_file
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], functions
- fn_xe_file_target_read_file function
- sys.fn_xe_file_target_read_file function
ms.assetid: cc0351ae-4882-4b67-b0d8-bd235d20c901
caps.latest.revision: 20
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 29a0eda47d510292d657bfdb7912a9fe8940b023
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43099619"
---
# <a name="sysfnxefiletargetreadfile-transact-sql"></a>sys.fn_xe_file_target_read_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Legge file creati dalla destinazione asincrona dei file degli eventi estesi. Viene restituito un evento per riga in formato XML.  
  
> [!WARNING]  
>  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] accettare i risultati della traccia generati in formato XEL e XEM. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Estesi supportano solo gli eventi i risultati della traccia in formato XEL. È consigliabile utilizzare SQL Server Management Studio per leggere i risultati della traccia in formato XEL.    
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.fn_xe_file_target_read_file ( path, mdpath, initial_file_name, initial_offset )  
```  
  
## <a name="arguments"></a>Argomenti  
 *path*  
 Percorso dei file da leggere. *percorso* può contenere caratteri jolly e può includere il nome di un file. *percorso* viene **nvarchar(260)**. Non prevede alcun valore predefinito. Nel contesto del Database SQL di Azure, questo valore è un URL HTTP a un file in archiviazione di Azure.
  
 *mdpath*  
 Il percorso del file di metadati che corrisponde al file o ai file specificati dal *percorso* argomento. *mdpath* viene **nvarchar(260)**. Non prevede alcun valore predefinito. A partire da SQL Server 2016, questo parametro può essere specificato come null.
  
> [!NOTE]  
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] non richiede la *mdpath* parametro. È tuttavia disponibile per la compatibilità con i file di log generati in versioni precedenti di SQL Server.  
  
 *initial_file_name*  
 Il primo file da leggere dal *percorso*. *initial_file_name* viene **nvarchar(260)**. Non prevede alcun valore predefinito. Se **null** è specificato come argomento di tutti i file trovati in *percorso* vengono letti.  
  
> [!NOTE]  
>  *initial_file_name* e *initial_offset* sono argomenti accoppiati. Se si specifica un valore per uno dei due argomenti, è necessario specificare un valore anche per l'altro.  
  
 *initial_offset*  
 Utilizzato per specificare l'ultimo offset letto precedentemente e consente di ignorare tutti gli eventi fino all'offset (incluso). L'enumerazione degli eventi inizia dopo l'offset specificato. *initial_offset* viene **bigint**. Se **null** viene specificato come argomento l'intero file verrà letto.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|module_guid|**uniqueidentifier**|GUID del modulo dell'evento. Non ammette i valori Null.|  
|package_guid|**uniqueidentifier**|GUID del pacchetto dell'evento. Non ammette i valori Null.|  
|object_name|**nvarchar(256)**|Nome dell'evento. Non ammette i valori Null.|  
|event_data|**nvarchar(max)**|Contenuto dell'evento in formato XML. Non ammette i valori Null.|  
|file_name|**nvarchar(260)**|Nome del file che contiene l'evento. Non ammette i valori Null.|  
|file_offset|**bigint**|Offset del blocco nel file che contiene l'evento. Non ammette i valori Null.|  
|timestamp_utc|**datetime2**|**Si applica a** : da [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] fino a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br />Data e ora (fuso orario UTC) dell'evento. Non ammette i valori Null.|  

  
## <a name="remarks"></a>Note  
 Leggere i risultati di grandi dimensioni imposta eseguendo **Sys. fn_xe_file_target_read_file** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] può comportare un errore. Usare la **risultati in un File** modalità (**Ctrl + Maiusc + F**) per esportare set di risultati di grandi dimensioni in un file e invece di leggere il file con un altro strumento.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-retrieving-data-from-file-targets"></a>A. Recupero di dati da destinazioni di file  
 Nell'esempio seguente vengono restituite tutte le righe di tutti i file. Nell'esempio le destinazioni di file e i metafile si trovano nella cartella della traccia in C:\unità.  
  
```  
SELECT * FROM sys.fn_xe_file_target_read_file('C:\traces\*.xel', 'C:\traces\metafile.xem', null, null);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Viste a gestione dinamica degli eventi estesi](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)   
 [Viste del catalogo degli eventi estesi &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Eventi estesi](../../relational-databases/extended-events/extended-events.md)  
  
  
