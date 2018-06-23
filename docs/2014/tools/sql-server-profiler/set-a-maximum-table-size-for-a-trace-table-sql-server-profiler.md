---
title: Impostare le dimensioni massime di una tabella di traccia (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 530e6bd70bc40fc85ac5a2071a3983b0933f6f31
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168433"
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a>Impostare le dimensioni massime di una tabella di traccia (SQL Server Profiler)
  In questo argomento viene descritta la procedura per l'impostazione delle dimensioni massime delle tabelle di traccia tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a>Per impostare le dimensioni massime di una tabella di traccia  
  
1.  Scegliere **Nuova traccia** dal menu **File**e quindi connettersi a un'istanza di SQL Server.  
  
     Verrà visualizzata la finestra di dialogo **Proprietà traccia**.  
  
    > [!NOTE]  
    >  Se l'opzione **Avvia traccia non appena viene stabilita una connessione**è selezionata, la finestra di dialogo **Proprietà traccia**non viene visualizzata e viene invece avviata la traccia. Per disabilitare questa impostazione, scegliere **Opzioni**dal menu **Strumenti**e deselezionare la casella di controllo **Avvia traccia non appena viene stabilita una connessione** .  
  
2.  Nella casella **Nome traccia** digitare un nome per la traccia.  
  
3.  Nell'elenco **Nome del modello**selezionare un modello di traccia.  
  
4.  Selezionare la casella di controllo **Salva nella tabella**.  
  
5.  Connettersi al server nel quale si desidera archiviare la traccia.  
  
     Verrà visualizzata la finestra di dialogo **Tabella di destinazione** .  
  
6.  Selezionare un database per la traccia dall'elenco **Database** .  
  
7.  Nella casella **Tabella** digitare o selezionare il nome di una tabella.  
  
8.  Selezionare la casella di controllo **Numero massimo di righe** e specificare il numero massimo di righe della tabella di traccia.  
  
    > [!NOTE]  
    >  Quando il numero di righe della tabella supererà il valore massimo specificato, gli eventi di traccia non verranno più registrati. L'esecuzione della traccia, tuttavia, proseguirà.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](sql-server-profiler.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  