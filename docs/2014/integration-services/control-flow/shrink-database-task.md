---
title: Attività Compatta database | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.shrinkdatabasetask.f1
helpviewer_keywords:
- Shrink Database task
- database shrinking [Integration Services]
- shrinking databases
ms.assetid: e66286f8-97b1-4e5a-86b4-e56f1932b7d5
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8da3472bf3772654def991ede932f92a20283808
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054344"
---
# <a name="shrink-database-task"></a>Compatta database - attività
  Con l'attività Compatta database è possibile ridurre le dimensioni dei file di log e di dati del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Tramite l'attività Compatta database un pacchetto può compattare file per uno o più database.  
  
 Compattando i file di dati si recupera spazio spostando le pagine di dati dalla fine del file allo spazio non occupato più vicino all'inizio del file. Quando alla fine del file viene creato sufficiente spazio libero, le pagine di dati possono essere deallocate e restituite al file system.  
  
> [!WARNING]  
>  I dati spostati per ridurre un file possono essere dispersi in qualsiasi percorso disponibile nel file, provocando la frammentazione dell'indice e rallentando le prestazioni di query che eseguono ricerche in un intervallo dell'indice Per eliminare la frammentazione, valutare la possibilità di ricompilare gli indici sul file dopo la compattazione.  
  
## <a name="commands"></a>Comandi  
 L'attività Compatta database incapsula un comando DBCC SHRINKDATABASE, che include gli argomenti e le opzioni seguenti:  
  
-   *database_name*  
  
-   *target_percent*  
  
-   NOTRUNCATE o TRUNCATEONLY.  
  
 Se si utilizza l'attività Compatta database per compattare più database, verranno eseguiti più comandi SHRINKDATABASE, uno per ogni database. Vengono usati gli stessi argomenti per tutte le istanze del comando SHRINKDATABASE, ad eccezione dell'argomento *database_name*. Per altre informazioni, vedere [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql).  
  
## <a name="configuration-of-the-shrink-database-task"></a>Configurazione dell'attività Compatta database  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Questa attività è disponibile nella sezione **Attività di manutenzione** della **casella degli strumenti** di Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Attività Compatta database &#40;Piano di manutenzione&#41;](../../relational-databases/maintenance-plans/shrink-database-task-maintenance-plan.md)  
  
 Per ulteriori informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)], fare clic sull'argomento seguente:  
  
-   [Impostare le proprietà di un'attività o di un contenitore](../set-the-properties-of-a-task-or-container.md)  
  
  
