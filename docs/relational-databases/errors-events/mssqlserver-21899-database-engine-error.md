---
title: MSSQLSERVER_21899 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
caps.latest.revision: "6"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 677f6c5b9a406bdc66d2d92bc696c59c74f77a51
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver21899"></a>MSSQLSERVER_21899
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21899|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLErrorNum21899|  
|Testo del messaggio|Impossibile eseguire la query sul server di pubblicazione reindirizzato '%s' per determinare la presenza di voci sysserver per i Sottoscrittori del server di pubblicazione originale '%s'. Errore '%d', messaggio di errore '%s'.|  
  
## <a name="explanation"></a>Spiegazione  
**sp_validate_redirected_publisher** esegue query sulle tabelle di metadati delle sottoscrizioni del database del server di pubblicazione presente sul server remoto per determinare i Sottoscrittori associati. L'errore 21899 viene restituito in caso di errore di questa query. La query della convalida richiede l'accesso al database pubblicato sul server di pubblicazione reindirizzato. Se l'accesso specificato quando è stato chiamato **sp_adddistpublisher** per il server di pubblicazione originale non è autorizzato ad accedere al database pubblicato sul server di pubblicazione reindirizzato, viene restituito l'errore 21899.  
  
## <a name="user-action"></a>Azione dell'utente  
Controllare il messaggio di errore citato per determinare la causa dell'errore ed eseguire azioni correttive appropriate  
  
