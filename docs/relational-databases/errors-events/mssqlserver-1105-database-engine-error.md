---
title: MSSQLSERVER_1105 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 1105 (Database Engine error)
ms.assetid: e7f4ad02-8c7f-4bb9-9781-2c86253f2138
caps.latest.revision: "19"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 4a76361f4aa307eeece1e57b8e2b0c9b51c07df0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver1105"></a>MSSQLSERVER_1105
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1105|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|NO_MORE_SPACE_IN_FG|  
|Testo del messaggio|Impossibile allocare spazio per l'oggetto '%.*ls'%.\*ls nel database'%.\*ls'. Il filegroup '%.\*ls' è pieno. Liberare spazio su disco eliminando i file non necessari, eliminando oggetti dal filegroup, aggiungendo file al filegroup oppure attivando l'aumento automatico delle dimensioni per i file esistenti nel filegroup.|  
  
## <a name="explanation"></a>Spiegazione  
Nel filegroup indicato non vi è spazio disponibile su disco.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire le azioni seguenti per tentare di liberare spazio sufficiente nel filegroup:  
  
-   Attivare l'aumento automatico delle dimensioni dei file.  
  
-   Aggiungere altri file al gruppo di file.  
  
-   Liberare spazio su disco eliminando indici o tabelle che non sono più necessari.  
  
-   Per ulteriori informazioni, vedere "Risoluzione dei problemi relativi a spazio su disco insufficiente" nella documentazione online di SQL Server.  
  
> [!NOTE]  
> Se un indice si trova in più file, **ALTER INDEX REORGANIZE** può restituire un errore 1105 quando uno dei file è pieno. Il processo di riorganizzazione viene bloccato quando il processo prova a spostare le righe nel file pieno. Per risolvere questa limitazione, eseguire **ALTER INDEX REBUILD** anziché **ALTER INDEX REORGANIZE** o modificare il limite di aumento delle dimensioni dei file pieni.  
  
