---
title: Generare lo script per una tabella | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea88d736-849e-4368-b55d-06aeee097bf3
caps.latest.revision: 29
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 4f7605be808552de655ed89155f7956efb86cb75
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169555"
---
# <a name="script-a-table"></a>Generare lo script per una tabella
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] consente di creare script per selezionare, inserire, aggiornare ed eliminare tabelle o per creare, modificare, eliminare o eseguire stored procedure.  
  
 Talvolta è necessario creare uno script con più opzioni disponibili, come ad esempio le opzioni per eliminare e poi creare una procedura o per creare una tabella e modificarne un'altra. Per creare script combinati, salvare il primo script in una finestra dell'editor di query e il secondo negli Appunti in modo da incollarlo nella finestra dopo il primo script.  
  
## <a name="creating-an-update-script"></a>Creazione di uno script di aggiornamento  
  
#### <a name="to-create-the-insert-script-for-a-table"></a>Per creare lo script di inserimento per una tabella  
  
1.  In Esplora oggetti espandere il server, espandere **Database**, [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] e **Tabelle**, fare clic con il pulsante destro del mouse su **HumanResources.Employee**, quindi scegliere **Crea script per tabella**.  
  
2.  Nel menu di scelta rapida sono disponibili sette opzioni di script: **Genera codice per istruzione CREATE in**, **Genera codice per istruzione DROP in**, **Genera codice per istruzione DROP e CREATE in**, **Genera codice per istruzione SELECT in**, **Genera codice per istruzione INSERT in**, **Genera codice per istruzione UPDATE in**e **Genera codice per istruzione DELETE in**. Scegliere **Genera codice per istruzione UPDATE in**e quindi fare clic su **Nuova finestra editor di query**.  
  
3.  Viene aperta una finestra dell'editor di query che esegue una connessione e presenta l'intera istruzione di aggiornamento.  
  
     In questa procedura vengono illustrate le potenzialità della funzionalità di creazione di script per numerose operazioni e non soltanto per la creazione di tabelle e stored procedure. Questa nuova funzionalità consente di aggiungere rapidamente script per la manipolazione dei dati al progetto e per l'esecuzione di stored procedure. Ciò comporta un notevole risparmio di tempo nei casi di tabelle e procedure contenenti molti campi.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Riepilogo: Scrittura di codice Transact-SQL](../../tutorials/summary-writing-transact-sql.md)  
  
  