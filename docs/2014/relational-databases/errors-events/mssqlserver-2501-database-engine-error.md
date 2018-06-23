---
title: MSSQLSERVER_2501 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2501 (Database Engine error)
ms.assetid: 895aafe3-a4e7-4ed8-acc5-93be76ef3664
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1d6e9f16e00684f0a55682b69e4c2d89d0dd552e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157160"
---
# <a name="mssqlserver2501"></a>MSSQLSERVER_2501
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2501|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_NO_SUCH_TABLE_NAME|  
|Testo del messaggio|Impossibile trovare un oggetto o una tabella con il nome 'NAME'. Controllare il catalogo di sistema.|  
  
## <a name="explanation"></a>Spiegazione  
 Non è possibile individuare l'oggetto specificato.  
  
### <a name="possible-causes"></a>Possibili cause  
 L'errore può essere causato da uno dei problemi seguenti:  
  
-   L'oggetto non è stato specificato correttamente.  
  
-   L'oggetto non esiste o è stato rimosso prima di essere utilizzato in un'istruzione.  
  
-   È possibile che l'oggetto esista ma non possa essere esposto all'utente. Ad esempio, l'utente potrebbe non disporre di autorizzazioni sufficienti per visualizzare l'oggetto oppure l'oggetto è costituito da una tabella interna che non può essere visualizzata dall'utente.  
  
## <a name="user-action"></a>Azione dell'utente  
  
-   Verificare la correttezza del contesto di database corrente. Per altre informazioni, vedere [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).  
  
-   Verificare che il nome della tabella o dell'oggetto sia stato specificato correttamente.  
  
-   Verificare il nome dello schema contenente l'oggetto. Se l'oggetto appartiene a uno schema diverso da quello predefinito, ovvero **dbo**, è necessario specificare il nome della tabella o dell'oggetto usando il formato in due parti *schema_name.object_name*.  
  
-   Verificare l'esistenza dell'oggetto nelle tabelle di sistema. Per verificare l'esistenza di una tabella o un altro oggetto con ambito schema, eseguire una query nella vista del catalogo [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql). Se l'oggetto non è presente nelle tabelle di sistema, significa che è stato eliminato o l'utente non dispone delle autorizzazioni necessarie per visualizzare i metadati dell'oggetto. Per altre informazioni su come visualizzare i metadati degli oggetti, vedere [Configurazione della visibilità dei metadati](../security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
  
