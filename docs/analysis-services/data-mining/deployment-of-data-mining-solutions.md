---
title: Distribuzione di soluzioni di Data Mining | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining models [Analysis Services], deploying
- deploying [Analysis Services], production environments
- deploying [Analysis Services - data mining]
- solutions [Analysis Services], deploying
- models [Analysis Services], data mining
ms.assetid: d83effc7-437d-42e9-8ac3-b65f79e27043
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: aa037f7ff155df158ba2967c5e7c31989ace887d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="deployment-of-data-mining-solutions"></a>Distribuzione di soluzioni di data mining
  L'ultimo passaggio del processo di data mining consiste nel distribuire i modelli in un ambiente di produzione. La distribuzione è importante perché rende disponibili i modelli agli utenti in modo da poter eseguire le attività seguenti:  
  
-   Utilizzare i modelli per creare stime e prendere decisioni aziendali. Per informazioni sugli strumenti che è possibile usare per creare query, vedere [Strumenti query di data mining](../../analysis-services/data-mining/data-mining-query-tools.md).  
  
-   Incorporare la funzionalità di data mining direttamente in un'applicazione. È possibile includere la libreria AMO (Analysis Management Objects) o un assembly contenente un set di oggetti utilizzabili dall'applicazione per creare, modificare, elaborare ed eliminare strutture e modelli di data mining.  
  
-   Creare report che consentano agli utenti di richiedere stime, visualizzare tendenze o confrontare modelli.  
  
 In questa sezione vengono fornite informazioni dettagliate sulle opzioni di distribuzione.  
  
 [Requisiti per la distribuzione delle soluzioni di data mining](#bkmk_Reqs)  
  
 [Distribuzione di una soluzione relazionale](#bkmk_RelationalSltn)  
  
 [Distribuzione di una soluzione multidimensionale](#bkmk_MDSltn)  
  
 [Risorse correlate](#bkmk_Resources)  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Distribuire una soluzione di data mining in versioni precedenti di SQL Server](../../analysis-services/data-mining/deploy-a-data-mining-solution-to-previous-versions-of-sql-server.md)  
  
 [Esportare e importare gli oggetti di data mining](../../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
##  <a name="bkmk_Reqs"></a> Requisiti per la distribuzione delle soluzioni di data mining  
 L'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a cui si distribuisce la soluzione deve essere in esecuzione in una modalità che supporta oggetti multidimensionali e oggetti di data mining; non è infatti possibile distribuire oggetti di data mining a un'istanza che ospita modelli tabulari o dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
 Pertanto, quando si crea una soluzione di data mining in Visual Studio, assicurarsi di usare il modello **Progetto multidimensionale e di data mining di Analysis Services**.  
  
 Quando si distribuisce la soluzione, gli oggetti utilizzati per il data mining vengono creati nell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] specificata, in un database con lo stesso nome del file della soluzione.  
  
###  <a name="bkmk_RelationalSltn"></a> Distribuzione di una soluzione relazionale  
 Quando si distribuisce una soluzione di data mining relazionale, gli oggetti di data mining obbligatori vengono creati all'interno di un nuovo database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e gli oggetti vengono elaborati per impostazione predefinita. Tramite la proprietà di configurazione **Opzione di elaborazione** è possibile modificare le opzioni di elaborazione. Per altre informazioni, vedere [Configurare proprietà di progetti di Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md).  
  
 Per impostazione predefinita, solo le modifiche incrementali vengono distribuite ogni volta. In altre parole, è possibile modificare un modello di data mining e alla successiva distribuzione del progetto solo quel modello di data mining verrà aggiornato. Tuttavia, se più client modificano il database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , è possibile che si verifichino degli errori. Per modificare la modalità di distribuzione predefinita in modo che l'intero database venga aggiornato alla distribuzione della soluzione, modificare la proprietà **Modalità distribuzione**  
  
 In una soluzione di data mining relazionale, gli unici oggetti che devono essere distribuiti sono la definizione dell'origine dati, eventuali viste origine dati utilizzate, le strutture di data mining e tutti i modelli di data mining dipendenti.  
  
###  <a name="bkmk_MDSltn"></a> Distribuzione di una soluzione multidimensionale  
 Quando si distribuisce una soluzione di data mining multidimensionale, questa soluzione crea gli oggetti di data mining all'interno dello stesso database del cubo di origine.  
  
 Quando si elabora un modello o una struttura di data mining, è necessario elaborare anche il cubo di origine. Per questo motivo, la distribuzione di una soluzione che utilizza modelli di data mining OLAP può prendere più tempo rispetto alle soluzioni di data mining relazionali.  
  
 In genere, gli oggetti di data mining utilizzano anche le stesse origini dati e le stesse viste origine dati utilizzate per il cubo. Tuttavia, è possibile aggiungere origini dati e viste origine dati destinate in modo specifico al data mining. Ad esempio, un cubo in genere non contiene dati su clienti potenziali o dati esterni non utilizzati negli oggetti multidimensionali.  
  
##  <a name="bkmk_Resources"></a> Risorse correlate  
 [Spostamento di oggetti di data mining](../../analysis-services/data-mining/moving-data-mining-objects.md)  
  
 Se il modello è basato unicamente su dati relazionali, l'esportazione e l'importazione di oggetti tramite DMX è il modo più semplice per spostare i modelli.  
  
 [Spostare un database di Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)  
  
 Quando i modelli utilizzano un cubo come origine dati, fare riferimento a questo argomento per ottenere ulteriori informazioni sullo spostamento dei modelli e dei dati del cubo di supporto.  
  
 [Distribuire progetti di Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
 Vengono fornite informazioni generali sulla distribuzione di progetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e vengono descritte le proprietà che è possibile impostare come parte della configurazione del progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Elaborazione di un modello multidimensionale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Strumenti query di data mining](../../analysis-services/data-mining/data-mining-query-tools.md)   
 [Requisiti e considerazioni sull'elaborazione &#40;data mining&#41;](../../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  

