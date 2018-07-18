---
title: 'Creazione di set di righe con ICommand:: Execute | Documenti Microsoft'
description: 'Creazione di set di righe con ICommand:: Execute'
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
- Execute method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3069d9a15ca9e988ed241515d19d66bb7b79e9d3
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689954"
---
# <a name="creating-rowsets-with-icommandexecute"></a>Creazione di set di righe con ICommand::Execute
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Per i set di righe creati tramite il **ICommand:: Execute** (metodo), le proprietà desiderate nel set di righe risultante può vincolare il testo del comando. Si tratta di un fattore particolarmente critico per i consumer che supportano testo del comando dinamico.  
  
 Il Driver OLE DB per SQL Server non è possibile utilizzare [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cursori per supportare i risultati di più set di righe generati da molti comandi. Se un consumer richiede un set di righe per cui è necessario il supporto del cursore [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], si verifica un errore se il testo del comando genera più di un singolo set di righe come risultato. Per altre informazioni, vedere [risultati più set di righe di generazione di comandi](../../oledb/ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Scorrevole Driver OLE DB per i set di righe di SQL Server sono supportati da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cursori. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] impone limitazioni sui cursori che sono sensibili alle modifiche apportate dagli altri utenti del database. In particolare, le righe in alcuni cursori non possono essere ordinate e il tentativo di creare un set di righe tramite un comando che contiene una clausola SQL ORDER BY può non riuscire. Per altre informazioni, vedere [set di righe e cursori del Server SQL](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
