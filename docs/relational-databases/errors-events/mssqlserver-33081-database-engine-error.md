---
title: MSSQLSERVER_33081 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 33081 (Database Engine error)
ms.assetid: 839705e7-fa37-4c0d-9f3f-95a9eab98bcf
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c5c47dd2a9d349da10e876f8da486790355be125
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver33081"></a>MSSQLSERVER_33081
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|33081|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SEC_DLL_TRUST_VERIFICATION_FAILED|  
|Testo del messaggio|Impossibile caricare il provider del servizio di crittografia '%.*ls' a causa di una firma Authenticode o un percorso file non valido.  Controllare i messaggi precedenti per altri errori.|  
  
## <a name="explanation"></a>Spiegazione  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è stato in grado di caricare il provider del servizio di crittografia elencato nel messaggio di errore. Questo errore può essere provocato da numerose API Windows non corrette. Il buffer circolare contiene il nome dell'API non corretta e il codice di errore Windows restituito dall'API. Per ottenere altre informazioni, eseguire una query sulla vista sys.dm_os_ring_buffers nel modo seguente.  
  
```  
SELECT * FROM sys.dm_os_ring_buffers   
WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
```  
  
## <a name="user-action"></a>Azione dell'utente  
Per esaminare il problema, cercare il codice di errore Windows codice di errore in MSDN (http://msdn.microsoft.com/). Risolvere l'errore o contattare il Servizio Supporto Tecnico Clienti [!INCLUDE[msCoName](../../includes/msconame-md.md)] per ulteriori informazioni. Se è necessario contattare il Servizio Supporto Tecnico Clienti Microsoft, raccogliere le informazioni seguenti che dovranno essere comunicate al personale di supporto:  
  
-   Log degli errori che mostra l'errore relativo all'impossibilità di caricare il provider di crittografia.  
  
-   Output dell'istruzione seguente:  
  
    ```  
    SELECT * FROM sys.dm_os_ring_buffers   
    WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
    ```  
  
> [!NOTE]  
> Tentare di raccogliere subito le informazioni sul buffer circolare poiché possono essere perse durante un riavvio.  
  

