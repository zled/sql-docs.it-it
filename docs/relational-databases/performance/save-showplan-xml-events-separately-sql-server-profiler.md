---
title: Salvare eventi Showplan XML in modo indipendente (SQL Server Profiler) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Showplan XML events
- saving Showplan XML events
- events [SQL Server], Showplan XML
ms.assetid: 33320a7a-36e8-401c-876d-5b82c49abd85
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e92884b770e55cbd1b34203d7979041ee3821159
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="save-showplan-xml-events-separately-sql-server-profiler"></a>Salvataggio di eventi Showplan XML in modo indipendente (SQL Server Profiler)
  In questo argomento viene illustrato come salvare eventi **Showplan XML** acquisiti in tracce in file SQLPlan distinti utilizzando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. È possibile aprire i file degli eventi **Showplan XML** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]per visualizzare il piano di esecuzione grafico per ogni evento.  
  
### <a name="to-save-showplan-xml-events-separately"></a>Per salvare gli eventi Showplan XML in modo indipendente  
  
1.  Scegliere **Nuova traccia** dal menu **File**e quindi connettersi a un'istanza di SQL Server.  
  
     Verrà visualizzata la finestra di dialogo **Proprietà traccia**.  
  
    > [!NOTE]  
    >  Se l'opzione **Avvia traccia non appena viene stabilita una connessione**è selezionata, la finestra di dialogo **Proprietà traccia**non viene visualizzata e viene invece avviata la traccia. Per disabilitare questa impostazione, scegliere **Opzioni**dal menu **Strumenti**e deselezionare la casella di controllo **Avvia traccia non appena viene stabilita una connessione** .  
  
2.  Nella finestra di dialogo **Proprietà traccia** digitare un nome per la traccia nella casella **Nome traccia** .  
  
3.  Nell'elenco **Modello** selezionare un modello di traccia sul quale basare la traccia oppure selezionare **Vuoto** per non utilizzare alcun modello.  
  
4.  Eseguire una delle operazioni seguenti:  
  
    -   Selezionare la casella di controllo**Salva nel file** per acquisire la traccia in un file. Specificare un valore per l'opzione **Dimensioni massime del file**. Se lo si desidera, selezionare le caselle di controllo **Consenti rollover dei file** e **Dati di traccia elaborati dal server** .  
  
    -   Selezionare la casella di controllo**Salva nella tabella** per acquisire la traccia in una tabella di database. Facoltativamente selezionare la casella di controllo **Numero massimo di righe**e specificare un valore.  
  
5.  Facoltativamente, selezionare la casella di controllo **Data e ora di arresto della traccia** e specificare una data e un'ora di arresto della traccia.  
  
6.  Fare clic sulla scheda **Selezione eventi**.  
  
7.  Nella finestra di dialogo **Eventi**espandere la categoria di eventi **Prestazioni**e quindi selezionare la casella di controllo **Showplan XML**. Se la categoria di eventi **Performance** non è visualizzata, selezionare la casella di controllo **Mostra tutti gli eventi** .  
  
     Verrà visualizzata la finestra di dialogo **Impostazioni estrazione event**viene aggiunta alla finestra di dialogo **Proprietà traccia**.  
  
8.  Scegliere **Impostazioni estrazione event**selezionare la casella di controllo **Salva eventi Showplan XML separatamente**.  
  
9. Nella finestra di dialogo **Salva con nome** immettere il nome del file in cui archiviare gli eventi **Showplan XML** .  
  
10. Fare clic su **Tutti i batch Showplan XML in un singolo file** per salvare tutti gli eventi **Showplan XML** in un unico file XML oppure su **Crea un file distinto per ogni singolo batch Showplan XML**per creare un nuovo file XML per ogni evento **Showplan XML** .  
  
11. Per visualizzare i file degli eventi **Showplan XML** in SQL Server Management Studio, scegliere **Apri** dal menu **File**e quindi fare clic su **File**. Passare alla directory in cui sono stati salvati i file o il file degli eventi **Showplan XML** per selezionarne uno e aprirlo. I file degli eventi**Showplan XML** hanno estensione SqlPlan.  
  
## <a name="see-also"></a>Vedere anche  
 [Analizzare query con risultati SHOWPLAN in SQL Server Profiler](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  

