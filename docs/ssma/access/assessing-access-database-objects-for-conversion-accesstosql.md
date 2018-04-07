---
title: Valutare gli oggetti di Database di Access per la conversione (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
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
helpviewer_keywords:
- assessing SQL
- assessing syntax
- assessment reports
- creating assessment reports
- estimating migration effort
- reports
- SQL, assessing
- syntax, assessing
ms.assetid: 8b9e23d6-da62-437a-8c05-8ad2628b9441
caps.latest.revision: 16
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f34d6d2c90b90a5afc7b10a19cc5d82373a26a86
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="assessing-access-database-objects-for-conversion-accesstosql"></a>Valutare gli oggetti di Database di Access per la conversione (AccessToSQL)
Prima di caricare gli oggetti e la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario determinare la quantità della migrazione sia stata completata e il tempo potrebbe richiedere la conversione. SSMA è possibile creare una relazione di valutazione che mostra la percentuale di oggetti che sono state convertite correttamente a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi SQL Azure e l'ora le stime per eseguire la migrazione. SSMA consente inoltre di visualizzare i problemi specifici che hanno causato gli errori di conversione.  
  
## <a name="creating-assessment-reports"></a>Creazione di report di valutazione  
Quando crea una relazione di valutazione, SSMA converte gli oggetti di database di Access selezionati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi SQL Azure e quindi Mostra i risultati.  
  
**Per creare un report di valutazione**  
  
1.  Nel Visualizzatore metadati di accesso, selezionare i database che si desidera valutare.  
  
2.  Per omettere i singoli oggetti, deselezionare le caselle di controllo accanto agli oggetti che non si desidera valutare.  
  
3.  Fare doppio clic su **database**, quindi selezionare **crea Report**.  
  
    È inoltre possibile analizzare singoli oggetti destro del mouse su un oggetto e quindi selezionando **crea Report**.  
  
    SSMA Mostra lo stato di avanzamento nella barra di stato nella parte inferiore della finestra. Se il riquadro di Output è visibile, si verifica anche i messaggi nel riquadro di Output.  
  
Al termine, la valutazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per Access: verrà visualizzata la finestra di Report di valutazione.  
  
## <a name="using-assessment-reports"></a>Utilizzo dei report di valutazione  
La finestra di Report di valutazione contiene tre riquadri: un elenco di cartelle, un riquadro dei dettagli e un riquadro del messaggio.  
  
-   Riquadro di esplorazione consente di esplorare gli oggetti che sono stati valutati. È possibile scegliere gli elementi in questo riquadro per eseguire il drill-down chiavi, indici e le singole tabelle.  
  
-   Riquadro dei dettagli Mostra le statistiche di conversione per l'oggetto selezionato.  
  
-   Viene illustrato il riquadro dei messaggi di errori, avvisi e messaggi informativi per la conversione e tempo stimato per eseguire la migrazione e la procedura di correzione degli errori.  
  
È necessario correggere gli errori prima di eseguire nuovamente il report di valutazione o convertire gli schemi. Per trovare gli errori, fare clic su di **errori** pulsante nel riquadro messaggi e quindi espandere ogni errore per visualizzare un elenco di oggetti in cui si è verificato l'errore. Se si fa clic su un oggetto nel riquadro messaggi, tutti gli errori e avvisi per l'oggetto verranno visualizzato nel riquadro dei dettagli.  
  
## <a name="next-step"></a>Passaggio successivo  
[Conversione di oggetti di database di Access](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>Vedere anche  
[La migrazione dei database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
