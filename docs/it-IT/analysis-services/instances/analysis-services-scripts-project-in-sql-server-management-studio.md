---
title: Progetto di script in SQL Server Management Studio di Analysis Services | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 86b6090d2f781d1db835752c95907fa1be182963
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="analysis-services-scripts-project-in-sql-server-management-studio"></a>Progetto script Analysis Services in SQL Server Management Studio
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]è possibile creare un progetto script di Analysis Server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per raggruppare script correlati per lo sviluppo, la gestione e il controllo del codice sorgente. Se in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]non è caricata alcuna soluzione, tramite la creazione di un nuovo progetto script di Analysis Server viene creata automaticamente una nuova soluzione. In caso contrario, il nuovo progetto script di Analysis Server può essere aggiunto alla soluzione esistente oppure creato in una nuova soluzione.  
  
 Per creare un progetto script di Analysis Server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], è necessario eseguire i passaggi fondamentali seguenti:  
  
1.  Dal menu File **Nuovo**e quindi fare clic su **Progetto**.  
  
     Selezionare il modello di progetto **Script di Analysis Server** , quindi specificare un nome e un percorso per il nuovo progetto.  
  
2.  Fare clic con il pulsante destro del mouse su **Connessioni** per creare una nuova connessione nella cartella Connessioni del progetto script di Analysis Server in Esplora soluzioni.  
  
     La cartella contiene le stringhe di connessione a istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] su cui possono essere eseguiti gli script inclusi nel progetto script di Analysis Server. In un progetto script di Analysis Server è possibile includere più connessioni. È inoltre possibile scegliere la connessione su cui eseguire uno script del progetto al momento dell'esecuzione.  
  
3.  Fare clic con il pulsante destro del mouse su **Query** per creare script MDX (Multidimensional Expressions), DMX (Data Mining Extensions) e XMLA (XML for Analysis) nella cartella Script del progetto Script di Analysis Server in Esplora soluzioni.
  
4.  Fare clic con il pulsante destro del mouse sul progetto, scegliere **Aggiungi**, quindi **Elemento esistente** per includere eventuali file aggiuntivi, ad esempio file di testo contenenti note sul progetto, nella cartella **Varie** del progetto Script di Analysis Server in Esplora soluzioni. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]questi file vengono ignorati.  
  
## <a name="file-types"></a>Tipi di file  
 In una soluzione di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] possono essere inclusi vari tipi di file a seconda dei progetti compresi nella soluzione e degli elementi di ogni progetto della soluzione. Per altre informazioni sui tipi di file per le soluzioni in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vedere [File per la gestione di soluzioni e progetti](http://msdn.microsoft.com/library/e19d2859-0b97-4727-ac27-c4c226d86b2f). In genere i file dei vari progetti di una soluzione [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] sono archiviati nella cartella delle soluzioni, in una cartella distinta per ogni progetto.  
  
 La cartella di un progetto script di Analysis Server può includere i tipi di file elencati nella tabella seguente.  
  
|Tipo di file|Description|  
|---------------|-----------------|  
|File di definizione del progetto script di Analysis Server (ssmsasproj)|Contiene i metadati relativi alle cartelle visualizzate in Esplora soluzioni e informazioni sulle cartelle in cui devono essere visualizzati i file del progetto.<br /><br /> Il file di definizione del progetto include inoltre i metadati per le connessioni a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] incluse nel progetto e i metadati che associano le connessioni ai file script del progetto.|  
|File script DMX (dmx)|Contiene uno script DMX incluso nel progetto.|  
|File script MDX (mdx)|Contiene uno script MDX incluso nel progetto.|  
|File script XMLA (xmla)|Contiene uno script XMLA incluso nel progetto.|  
  
## <a name="analysis-services-templates"></a>Modelli di Analysis Services  
 Quando si aggiungono nuovi script MDX, DMX o XMLA a un progetto Script di Analysis Server, è possibile usare Esplora modelli per individuare i modelli di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ovvero una raccolta di istruzioni o script predefiniti che illustrano come deve essere eseguita una determinata azione. Esplora modelli è accessibile dal menu **Visualizza** e include modelli per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]e [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Per altre informazioni, vedere [Utilizzare i modelli di Analysis Services in SQL Server Management Studio](../../analysis-services/instances/use-analysis-services-templates-in-sql-server-management-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di modelli multidimensionali tramite SQL Server Data Tools &#40;SSDT&#41;](../../analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)   
 [Espressioni MDX & #40; MDX & #41; Riferimento](../../mdx/multidimensional-expressions-mdx-reference.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento](../../dmx/data-mining-extensions-dmx-reference.md)   
 [Analysis Services Scripting Language &#40;ASSL per XMLA&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [Analysis Services Scripting Language &#40;ASSL per XMLA&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)  
  
  