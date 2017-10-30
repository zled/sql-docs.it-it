---
title: Catalog. catalog_properties (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: e604a382-95c8-4764-b268-742eb5c6d4cf
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ca3d5da05126d5b71bf6d714f9e8449f9f5c8335
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcatalogproperties-ssisdb-database"></a>catalog.catalog_properties (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzate le proprietà del catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Nome della proprietà del catalogo.|  
|property_value|**nvarchar(256)**|Valore della proprietà del catalogo.|  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista viene visualizzata una riga per ogni proprietà del catalogo. Nelle proprietà visualizzate da questa vista sono inclusi gli elementi seguenti:  
  
|Nome proprietà|Description|  
|-------------------|-----------------|  
|**ENCRYPTION_ALGORITHM**|Tipo di algoritmo di crittografia utilizzato per crittografare i dati sensibili. Nei valori supportati sono inclusi: `DES`, `TRIPLE_DES`, `TRIPLE_DES_3KEY`, `DESX`, `AES_128`, `AES_192` e `AES_256`. Nota: il database del catalogo deve essere in modalità utente singolo per la modifica di questa proprietà.|  
|**MAX_PROJECT_VERSIONS**|Numero di nuove versioni del progetto che saranno mantenute per un solo progetto. Quando viene abilitata la pulizia delle versioni, quelle precedenti oltre questo conteggio saranno eliminate.|  
|**OPERATION_CLEANUP_ENABLED**|Quando il valore è `TRUE`, dettagli e messaggi di operazione anteriori **RETENTION_WINDOW** (giorni) vengono eliminato dal catalogo. Quando il valore è `FALSE`, tutti i dettagli e i messaggi dell'operazione vengono archiviati nel catalogo. Nota: la pulizia dell'operazione viene eseguita da un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**RETENTION_WINDOW**|Numero di giorni di archiviazione nel catalogo dei dettagli e dei messaggi dell'operazione. Quando il valore è `-1`, il periodo di memorizzazione è infinito. Nota: Se non si desidera alcuna pulizia, impostare **OPERATION_CLEANUP_ENABLED** a **FALSE**.|  
|**VALIDATION_TIMEOUT**|Arresto delle convalide se non completate nel numero di secondi specificati da questa proprietà.|  
|**VERSION_CLEANUP_ENABLED**|Quando il valore è `TRUE`, solo il **MAX_PROJECT_VERSIONS** numero di versioni del progetto viene archiviato nel catalogo e vengono eliminate tutte le altre versioni di progetto. Quando il valore è **FALSE**, tutte le versioni di progetto vengono archiviate nel catalogo. Nota: la pulizia dell'operazione viene eseguita da un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**SERVER_LOGGING_LEVEL**|Livello di registrazione predefinito per il server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
  

