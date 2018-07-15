---
title: Strumenti e applicazioni usate in Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0ddb3b7a-7464-4d04-8659-11cb2e4cf3c3
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b91b8628fe9c12af7bb1c5ab74a079aa52401398
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282047"
---
# <a name="tools-and-applications-used-in-analysis-services"></a>Strumenti e applicazioni usati in Analysis Services
  È importante trovare gli strumenti e le applicazioni necessari per la creazione di modelli di Analysis Services e la gestione dei database associati in un'istanza di Analysis Services.  
  
## <a name="analysis-services-model-designers"></a>Strumenti di progettazione dei modelli di Analysis Services  
 I modelli tabulari e multidimensionali vengono creati dai modelli di progetto in una soluzione compilata all'interno della shell di Visual Studio. Il modello di progetto fornisce gli strumenti di progettazione per la creazione di modelli, cubi, dimensioni e ruoli che costituiscono una soluzione di Analysis Services.  
  
### <a name="download-sql-server-data-tools-for-business-intelligence-ssdt-bi"></a>Download di SQL Server Data Tools per Business Intelligence (SSDT-BI)  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] per Business Intelligence (SSDT-BI), precedentemente noto come Business Intelligence Development Studio (BIDS), viene utilizzato per creare i modelli di Analysis Services, i report di Reporting Services e i pacchetti di Integration Services. È possibile scaricare SSDT-BI dai percorsi seguenti:  
  
-   [Scaricare SSDT-BI per Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkId=396526)  
  
-   [Scaricare SSDT-BI per Visual Studio 2012](http://go.microsoft.com/fwlink/p/?LinkID=273673)  
  
 Se si dispone di una versione precedente di SSDT-BI o BIDS installata nel computer, la versione più recente viene installata side-by-side alla versione precedente. La versione più recente e quella precedente degli strumenti di progettazione vengono in genere eseguite su una sola workstation in modo da poter modificare progetti e soluzioni legati a versioni specifiche del server.  
  
> [!NOTE]  
>  Sono disponibili vari siti di download per le versioni di SSDT di Visual Studio 2012 e Visual Studio 2013. La maggior parte non include i modelli di progetto BI. Tramite i collegamenti sopra indicati è possibile scaricare la versione corretta. Se la versione di SSDT-BI è quella corretta, viene visualizzata la cartella dei modelli di progetto Business Intelligence. Questa cartella contiene i modelli di progetto per Analysis Services, Reporting Services e Integration Services. A seconda della modalità di installazione di SSDT-BI, potrebbe essere visualizzato anche un modello di progetto aggiuntivo per i database di SQL Server.  
  
 ![Nuovi modelli di progetto in SSDT](media/ssdt-biprojects.png "Nuovi modelli di progetto in SSDT")  
  
## <a name="administrative-tools"></a>Strumenti di amministrazione  
  
### <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 Management Studio è lo strumento di amministrazione principale per tutte le funzionalità di SQL Server, compreso Analysis Services. SQL Server Management Studio è un componente facoltativo. Se non viene visualizzato con le altre applicazioni di SQL Server nella pagina App in Windows Server 2012, eseguire l'installazione di SQL Server per aggiungerlo all'installazione.  
  
### <a name="sql-server-profiler"></a>SQL Server Profiler  
 Sebbene sia ufficialmente deprecato, SQL Server Profiler consente di monitorare facilmente connessioni, esecuzione di query MDX e altre operazioni del server. SQL Server Profiler viene installato per impostazione predefinita. È possibile trovarlo con le applicazioni di SQL Server in App in Windows Server 2012.  
  
### <a name="powershell"></a>PowerShell  
 È possibile usare i comandi PowerShell per eseguire molte attività amministrative. Visualizzare [PowerShell per Analysis Services](analysis-services-powershell.md) per altre informazioni.  
  
### <a name="community-and-third-party-tools"></a>Strumenti della community e di terze parti  
 Controllare la [pagina codeplex di Analysis Services](http://sqlsrvanalysissrvcs.codeplex.com/) per esempi di codice della community. I[forum](http://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) possono essere utili per cercare consigli sugli strumenti di terze parti che supportano Analysis Services.  
  
  
