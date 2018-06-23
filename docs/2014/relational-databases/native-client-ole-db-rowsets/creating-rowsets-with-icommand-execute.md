---
title: 'Creazione di set di righe con ICommand:: Execute | Documenti Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b62e32653777192d77c404cabee49cc188444204
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166826"
---
# <a name="creating-rowsets-with-icommandexecute"></a>Creazione di set di righe con ICommand::Execute
  Per i set di righe creati tramite il **ICommand:: Execute** (metodo), le proprietà desiderate nel set di righe risultante può vincolare il testo del comando. Si tratta di un fattore particolarmente critico per i consumer che supportano testo del comando dinamico.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non è possibile utilizzare [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursori per supportare i risultati di più set di righe generati da molti comandi. Se un consumer richiede un set di righe per cui è necessario il supporto del cursore [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si verifica un errore se il testo del comando genera più di un singolo set di righe come risultato. Per altre informazioni, vedere [risultati più set di righe di generazione di comandi](../native-client-ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Scorrevole [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di righe del provider OLE DB Native Client sono supportati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursori. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impone limitazioni sui cursori che sono sensibili alle modifiche apportate dagli altri utenti del database. In particolare, le righe in alcuni cursori non possono essere ordinate e il tentativo di creare un set di righe tramite un comando che contiene una clausola SQL ORDER BY può non riuscire. Per altre informazioni, vedere [set di righe e cursori del Server SQL](rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](rowsets.md)  
  
  