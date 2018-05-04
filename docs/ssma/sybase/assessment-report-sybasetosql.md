---
title: Report di valutazione (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: af24f2c4-5e86-4135-a4f3-a24faaeeefe7
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e4a283be868d0911a73a819a2ad109da070e7f34
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="assessment-report-sybasetosql"></a>Report di valutazione (SybaseToSQL)
Nella finestra di Report di valutazione vengono visualizzati i risultati della conversione di oggetti di database per [!INCLUDE[tsql](../../includes/tsql_md.md)] , sintassi e possibile stimare la complessità e costi dei progetti di migrazione.  
  
Per accedere al Report di valutazione, selezionare gli oggetti da convertire in Visualizzatore metadati di origine, fare doppio clic su **database**, quindi selezionare **crea Report**.  
  
## <a name="options"></a>Opzioni  
**Statistiche di conversione**  
Mostra le statistiche di conversione dal tipo di istruzione. In questo riquadro è visibile solo quando un oggetto di gruppo, ad esempio uno schema, o un oggetto senza codice è stato selezionato nel riquadro a sinistra.  
  
**Oggetti per categoria**  
Mostra le statistiche di conversione dal tipo di oggetto. In questo riquadro è visibile solo quando un oggetto di gruppo, ad esempio uno schema, o un oggetto senza codice è stato selezionato nel riquadro a sinistra.  
  
**Statistiche**  
Mostra le statistiche di conversione per l'oggetto selezionato. In questo riquadro è visibile solo quando è selezionato un singolo oggetto con il codice nel riquadro a sinistra. Potrebbe essere necessario espandere **statistiche** per visualizzare questo riquadro.  
  
**Esplorazione dell'origine**  
Viene illustrato il codice di base per l'oggetto selezionato ed evidenzia il codice che non è stato convertito in [!INCLUDE[tsql](../../includes/tsql_md.md)]. In questo riquadro è visibile solo quando è selezionato un singolo oggetto con il codice nel riquadro a sinistra.  
  
Fare clic sui numeri di riga per impostare o cancellare i segnalibri. Utilizzare i pulsanti nella parte superiore del riquadro per esplorare il codice.  
  
**Navigazione di destinazione**  
Mostra la conversione del risultante [!INCLUDE[tsql](../../includes/tsql_md.md)] codice per l'oggetto selezionato e i messaggi di errore per il codice che non è stato convertito. In questo riquadro è visibile solo quando è selezionato un singolo oggetto con il codice nel riquadro a sinistra.  
  
Fare clic sui numeri di riga per impostare o cancellare i segnalibri. Utilizzare i pulsanti nella parte superiore del riquadro per esplorare il codice.  
  
**Riquadro messaggi**  
Viene illustrato l'errori, avvisi e messaggi informativi che vengono generati quando si crea il report di valutazione. I messaggi vengono raggruppati per numero. Per visualizzare il codice che ha causato l'errore, fare clic su **errore**, **avviso**, o **Info**, espandere la categoria di messaggi e quindi fare clic su un messaggio.  
  
