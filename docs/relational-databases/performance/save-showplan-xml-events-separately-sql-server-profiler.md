---
title: Salvare eventi Showplan XML in modo indipendente (SQL Server Profiler) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Showplan XML events
- saving Showplan XML events
- events [SQL Server], Showplan XML
ms.assetid: 33320a7a-36e8-401c-876d-5b82c49abd85
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 106a627a50964d482776401bf27db6f2c83ac0ea
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="save-showplan-xml-events-separately-sql-server-profiler"></a>Salvare eventi Showplan XML in modo indipendente (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento illustra come salvare eventi **Showplan XML** acquisiti in tracce in file SQLPlan distinti usando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. È possibile aprire i file di eventi **Showplan XM** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per visualizzare graficamente il piano di esecuzione di ogni evento.  
  
## <a name="save-showplan-xml-events-separately"></a>Salvare gli eventi Showplan XML in modo indipendente  
  
1. Scegliere **Nuova traccia** dal menu **File** e quindi connettersi a un'istanza di SQL Server.  
  
     Verrà visualizzata la finestra di dialogo **Proprietà traccia** .  
  
    > [!NOTE]  
    >  Se la casella di controllo **Avvia traccia non appena viene stabilita una connessione** è selezionata, la finestra di dialogo **Proprietà traccia** non viene visualizzata e viene invece avviata la traccia. Per disattivare questa impostazione, scegliere **Opzioni** dal menu **Strumenti** e deselezionare la casella di controllo **Avvia traccia non appena viene stabilita una connessione**.  
  
2. Nella finestra di dialogo **Proprietà traccia** digitare un nome per la traccia nella casella **Nome traccia** .  
  
3. Nell'elenco **Modello** selezionare un modello di traccia su cui basare la traccia. Se non si vuole usare alcun modello, selezionare **Vuoto**.  
  
4. Eseguire una delle operazioni seguenti:  
  
    -   Per acquisire la traccia in un file selezionare la casella di controllo **Salva nel file**. Specificare un valore per l'opzione **Dimensioni massime del file**. 
    
        Se lo si desidera, selezionare le caselle di controllo **Consenti rollover dei file** e **Dati di traccia elaborati dal server** .  
  
    -   Per acquisire la traccia in una tabella di database, selezionare la casella di controllo **Salva nella tabella**. 
    
        Facoltativamente selezionare **Numero massimo di righe** e specificare un valore.  
  
5. Facoltativamente, selezionare la casella di controllo **Data e ora di arresto della traccia** e specificare una data e un'ora di arresto della traccia. 
  
6. Fare clic sulla scheda **Selezione eventi**.  
  
7. Nella colonna di dati **Eventi** espandere la categoria di eventi **Prestazioni** e quindi selezionare la casella di controllo **Showplan XML**. Se la categoria di eventi **Performance** non è visualizzata, selezionare la casella di controllo **Mostra tutti gli eventi**.  
  
     La scheda **Impostazioni estrazione eventi** viene aggiunta alla finestra di dialogo **Proprietà traccia**.  
  
8. Nella scheda **Impostazioni estrazione eventi** selezionare la casella di controllo **Salva eventi Showplan XML separatamente**.  
  
9. Nella finestra di dialogo **Salva con nome** immettere il nome del file in cui archiviare gli eventi **Showplan XML** .  
  
10. Selezionare **Tutti i batch Showplan XML in un singolo file** per salvare tutti gli eventi **Showplan XML** in un unico file XML. In alternativa, selezionare **Crea un file distinto per ogni singolo batch Showplan XML** per creare un nuovo file XML per ogni evento **Showplan XML**.  
  
11. Per visualizzare i file degli eventi **Showplan XML** in SQL Server Management Studio, scegliere **Apri** dal menu **File**e quindi fare clic su **File**. Passare alla directory in cui sono stati salvati i file o il file degli eventi **Showplan XML** per selezionarne uno e aprirlo. I file degli eventi**Showplan XML** hanno estensione SqlPlan.  
  
## <a name="see-also"></a>Vedere anche  
 [Analizzare query con risultati Showplan in SQL Server Profiler](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
