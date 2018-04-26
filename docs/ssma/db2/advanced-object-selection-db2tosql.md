---
title: Advanced Selezione oggetto (DB2ToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ca098c15-c343-4d7d-a284-c2fc405eb991
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9771987e0a2fd5e6136be8c3cb952769ecc74a73
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="advanced-object-selection-db2tosql"></a>Selezione avanzata di oggetti (DB2ToSQL)
Il **avanzate sezione oggetto** la finestra di dialogo consente di filtrare gli oggetti di database utilizzando le stringhe e sottostringhe nel nome dell'oggetto, quindi selezionare o deselezionare gli oggetti. SSMA consente di eseguire operazioni di conversione e migrazione oggetti selezionati.  
  
Per accedere a questa finestra di dialogo, in un Visualizzatore metadati e quindi scegliere **Selezione oggetto avanzata**.  
  
Quando si apre la finestra di dialogo, fare clic su **Mostra elementi sottocategorie** per visualizzare tutti gli oggetti che dispongono di metadati caricato nel progetto. È quindi possibile immettere le stringhe per filtrare gli elementi. Ad esempio, immettere la stringa "company" per visualizzare tutti gli elementi con nomi che includono tale stringa.  
  
Prima di utilizzare questa finestra di dialogo, si desidera forzare SSMA per caricare tutti i metadati dal salvataggio del progetto o la conversione di schemi.  
  
## <a name="options"></a>Opzioni  
**Controllare tutti gli elementi**  
Aggiunge un segno di spunta accanto a tutti gli elementi. Questi elementi verranno immediatamente selezionati in Esplora risorse di metadati.  
  
**Deselezionare tutti gli elementi**  
Rimuove il segno di spunta accanto a tutti gli elementi. Questi elementi verranno cancellati immediatamente in Esplora risorse di metadati.  
  
**Modalità di visualizzazione elenco**  
Consente di visualizzare filtrato di elementi in un elenco.  
  
**Modalità di visualizzazione tabella**  
Consente di visualizzare filtrato di elementi in una tabella.  
  
**Caricare solo gli elementi visualizzati**  
Attiva o disattiva la visualizzazione delle categorie o gli elementi. Quando si seleziona questo pulsante, SSMA Mostra tutti gli elementi che soddisfano i criteri di filtro e quelli che sono stati caricati in precedenza. Se questo pulsante non è selezionato, tramite SSMA vengono illustrate le cartelle di categoria.  
  
**Filtra**  
Immettere la stringa in cui che si desidera utilizzare per filtrare gli elementi. Ad esempio, per trovare tutti disponibili elementi che contengono la stringa "ID" nel nome dell'elemento, immettere la stringa "ID" nel **filtro** casella.  
  
Se gli elementi corrispondono ai criteri di filtro, le categorie o gli elementi verranno visualizzato durante la digitazione della stringa. Per visualizzare gli elementi corrispondenti, si consiglia di scegliere il **visualizzati solo gli elementi caricati** pulsante.  
  
**Cancella filtro**  
Cancella il **filtro** casella.  
  
