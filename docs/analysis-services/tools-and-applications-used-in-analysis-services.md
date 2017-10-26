---
title: Strumenti e applicazioni usate in Analysis Services | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 05/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 0ddb3b7a-7464-4d04-8659-11cb2e4cf3c3
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 5b9e63d4c7cdc57814b04b2e96e52bda17a25f5a
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="tools-and-applications-used-in-analysis-services"></a>Strumenti e applicazioni usati in Analysis Services
  Trovare gli strumenti e applicazioni, che è necessario per la compilazione di modelli di Analysis Services e la gestione di database distribuiti.  
  
## <a name="analysis-services-model-designers"></a>Strumenti di progettazione dei modelli di Analysis Services  
 I modelli vengono creati usando modelli di progetto in SQL Server Data Tools (SSDT), una shell di Visual Studio. Modelli di progetto forniscono i progettisti di modelli per la creazione degli oggetti modello di dati che costituiscono una soluzione di Analysis Services. SSDT è disponibile come download web gratuito aggiornati ogni mese.

 **[Scaricare SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)** 
  
 I modelli usano un'impostazione del livello di compatibilità per determinare la disponibilità di funzionalità e la versione di Analysis Services che deve eseguire il modello.  Se è possibile specificare che un determinato livello di compatibilità viene determinato in parte dalla progettazione del modello.  
  
 Modelli tabulari utilizzando le funzionalità più recenti, ad esempio il file BIM in formato JSON tabulare e bidirezionali il filtro incrociato, devono essere creati o aggiornati a livello di compatibilità 1200 o superiore.  
  
 Se è necessario un livello di compatibilità inferiore, ad esempio perché si desidera distribuire un modello in una versione precedente di Analysis Services, è possibile comunque utilizzare la progettazione del modello in SSDT. Le versioni più recenti dello strumento supportano la creazione di qualsiasi tipo di modello tabulare o multidimensionale, a qualsiasi livello di compatibilità.   

## <a name="administrative-tools"></a>Strumenti di amministrazione  
  
 SQL Server Management Studio (SSMS) è lo strumento di amministrazione principale per tutte le funzionalità di SQL Server, inclusi Analysis Services. SQL Server Management Studio è disponibile come download web gratuito aggiornati ogni mese. 
  
**[Scaricare SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)** 
  
 SQL Server Management Studio include gli eventi estesi (XEvent), che fornisce un'alternativa semplificata alle tracce di SQL Server Profiler utilizzato per attività di monitoraggio e diagnosi di problemi nei server di Azure Analysis Services e SQL Server 2016. Per altre informazioni, vedere [Monitor Analysis Services with SQL Server Extended Events](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md) .  
  
### <a name="sql-server-profiler"></a>SQL Server Profiler  
 Sebbene sia ufficialmente deprecato a favore di xEvents, SQL Server Profiler consente di monitorare facilmente connessioni, esecuzione di query MDX e altre operazioni del server. SQL Server Profiler viene installato per impostazione predefinita. È possibile trovarlo con le applicazioni SQL Server in app di Windows.  
  
### <a name="powershell"></a>PowerShell  
 È possibile usare i comandi PowerShell per eseguire molte attività amministrative. Vedere [riferimento di PowerShell](../analysis-services/powershell/analysis-services-powershell-reference.md) per ulteriori informazioni.  
  
### <a name="community-and-third-party-tools"></a>Strumenti della community e di terze parti  
 Controllare la [pagina codeplex di Analysis Services](http://sqlsrvanalysissrvcs.codeplex.com/) per esempi di codice della community. I[forum](http://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) possono essere utili per cercare consigli sugli strumenti di terze parti che supportano Analysis Services.  
  
## <a name="see-also"></a>Vedere anche  
 [Livello di compatibilità di un Database multidimensionale](../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Livello di compatibilità per i modelli tabulari](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  

