---
title: File per la gestione di soluzioni e progetti | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 13c811a0c616a9ef859e86c688804c829ec0d9f0
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="files-that-manage-solutions-and-projects"></a>File per la gestione di soluzioni e progetti
 <a name="-this-topic-describes-the-file-types-that-are-specific-to-includemsconameincludesmsconamemdmd-includessmanstudiofullincludesssmanstudiofullmdmd-by-default-all-solutions-and-their-projects-are-created-in-my-documentssql-server-management-studio-projects"></a>- Questo argomento descrive i tipi di file specifici di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Per impostazione predefinita, tutte le soluzioni e i relativi progetti vengono creati in \Documenti\SQL Server Management Studio Projects.  
 -  
 -## File della soluzione di Management Studio  
 -[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] usa tipi di file diversi rispetto a [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] o [!INCLUDE[msCoName](../../includes/msconame_md.md)] Visual Studio. Ciò vuol dire che non è possibile aprire una soluzione [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] o in Visual Studio. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] I file della soluzione consentono a Esplora soluzioni di visualizzare un'interfaccia grafica per la gestione dei file.  
 -  
 -|Estensione|Tipo di file|Description|Creato da|  
 -|-------------|-------------|---------------|--------------|  
 -|ssmssln|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] Oggetto della soluzione|Offre l'ambiente con riferimenti alla posizione sul disco di progetti, elementi di progetto e soluzione di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] |[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]|  
 -  
 -## File del progetto di Management Studio  
 - Mentre le soluzioni contengono i file della soluzione per la gestione degli oggetti presenti in una soluzione, i progetti contengono i file del progetto. Il tipo di file del progetto creato da [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] per un progetto dipende dal modello utilizzato per la creazione del progetto stesso. Nella tabella seguente viene descritto il tipo di file creato per ogni progetto.  
 -  
 -|Estensione|Modelli di progetto|  
 -|-------------|--------------------|  
 -|ssmssqlproj|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Progetto di script|  
 -|ssmsasproj|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)] Progetto di script|  
 -  
 -## Posizione dei file a livello di soluzione  
 - Per impostazione predefinita, i file a livello di soluzione vengono creati nella directory fisica del primo progetto creato con la soluzione. È possibile specificare una directory per la soluzione creando una soluzione oppure specificare la directory quando si crea un nuovo progetto.  
 -  
 - Se la struttura della directory è simile alla struttura logica visualizzata in Esplora soluzioni, è più facile individuare i file del progetto e della soluzione e condividerli con altri sviluppatori di un team.  
 -  
 -## Vedere anche  
 -[Gestire file con codifica](../../ssms/solution/manage-files-with-encoding.md)  
 -[File esterni](../../ssms/solution/miscellaneous-files.md)  
 -[Esplora soluzioni](../../ssms/solution/solution-explorer.md)  
 -[Soluzioni &#40;SQL Server Management Studio&#41;](../../ssms/solution/solutions-sql-server-management-studio.md)  
 -[Progetti &#40;SQL Server Management Studio&#41;](../../ssms/solution/projects-sql-server-management-studio.md)  
 -[Controllo del codice sorgente di Esplora soluzioni](https://msdn.microsoft.com/en-us/library/ms173879.aspx)  
  
