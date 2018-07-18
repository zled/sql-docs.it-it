---
title: Generare lo script per una tabella | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ea88d736-849e-4368-b55d-06aeee097bf3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7808c9270e0085c2f8fafb5262d6356f8c8d1e08
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196711"
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
  
  
