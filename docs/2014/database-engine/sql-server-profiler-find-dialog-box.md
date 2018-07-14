---
title: SQL Server Profiler - finestra di dialogo Find | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
caps.latest.revision: 24
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 311d248acae2b64d106c57f5c7f92024c4174e5c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37199991"
---
# <a name="sql-server-profiler---find-dialog-box"></a>SQL Server Profiler - Finestra di dialogo Trova
  Usare la finestra di dialogo **Trova** per eseguire la ricerca all'interno di una traccia in base a parole o caratteri specifici. Per annullare la ricerca in corso, premere ESC.  
  
 Per aprire questa finestra di dialogo in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], scegliere **Trova** dal menu **Modifica**.  
  
## <a name="options"></a>Opzioni  
 **Trova**  
 Immettere il testo che si desidera cercare. La ricerca individua tutte le stringhe contenenti la stringa specificata. Ad esempio, se si cerca "Completed", viene individuata la stringa "SQL:BatchCompleted." I caratteri jolly (*, ? e così via) non sono supportati.  
  
 **Cerca nella colonna**  
 Fare clic sulla colonna di dati in cui eseguire la ricerca o su **\<Tutte le colonne>** per eseguire la ricerca in tutte le colonne di dati presenti nella traccia.  
  
 **Maiuscole/minuscole**  
 Consente di trovare una stringa di testo con le stesse lettere maiuscole e minuscole di quella specificata nella casella **Trova** . Deselezionare questa casella di controllo per trovare stringhe di testo nella traccia che corrispondono al testo specificato indipendentemente dai caratteri maiuscoli o minuscoli.  
  
 **Parola intera**  
 Consente di limitare l'ambito della ricerca alle parole intere. Deselezionare la casella di controllo **Parola intera** per cercare un insieme di caratteri all'interno di una parola.  
  
 **Trova successivo**  
 Consente di trovare l'esempio successivo dei caratteri specificati nella casella **Trova** .  
  
 **Trova precedente**  
 Consente di eseguire una ricerca all'indietro per trovare l'esempio precedente dei caratteri specificati nella casella **Trova** .  
  
## <a name="see-also"></a>Vedere anche  
 [Trovare un valore o una colonna di dati durante la traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)   
 [Creare una traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)   
 [Aprire una tabella di traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)   
 [Aprire un file di traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [Modelli e autorizzazioni di SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
