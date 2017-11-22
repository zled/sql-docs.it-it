---
title: MSSQLSERVER_1101 | Microsoft Docs
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
helpviewer_keywords: 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8e99a6a8072f882f794f2406c66c6b0625cbc7d4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver1101"></a>MSSQLSERVER_1101
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1101|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|NOALLOCPG|  
|Testo del messaggio|Impossibile allocare una nuova pagina per il database '%.*ls' a causa di spazio su disco insufficiente nel filegroup '%.\*ls'. Liberare lo spazio necessario eliminando oggetti dal filegroup, aggiungendo file al filegroup oppure attivando l'aumento automatico delle dimensioni per i file esistenti nel filegroup.|  
  
## <a name="explanation"></a>Spiegazione  
Nel filegroup indicato non vi è spazio disponibile su disco.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire le azioni seguenti per tentare di liberare spazio sufficiente nel filegroup.  
  
-   Attivare l'aumento automatico delle dimensioni dei file.  
  
-   Aggiungere altri file al gruppo di file.  
  
-   Liberare spazio su disco eliminando indici o tabelle non necessari dal filegroup.  
  
