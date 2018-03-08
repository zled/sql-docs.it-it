---
title: Data Mining Extensions (DMX) riferimento | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: DMX
helpviewer_keywords:
- DMX [Analysis Services]
- statements [DMX]
- Data Mining Extensions [Analysis Services], statements
- DMX [Analysis Services], about Data Mining Extensions
- DMX [Analysis Services], statements
- data definition statements [DMX]
- predictions [DMX]
- Data Mining Extensions [Analysis Services]
- SSAS, DMX
- queries [DMX], extensions reference
- SQL Server Analysis Services, DMX
- OLE DB for Data Mining
- data manipulation statements [DMX]
- Data Mining Extensions [Analysis Services], about Data Mining Extensions
- mining models [Analysis Services], DMX
ms.assetid: 6d85ca20-de67-4e20-b3b5-b734c6cfcece
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 270ff587bb8595abab74487d92c237e1cb10e2e5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="data-mining-extensions-dmx-reference"></a>Guida di riferimento a DMX (Data Mining Extensions)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Estensioni DMX (Data Mining) è un linguaggio che è possibile utilizzare per creare e utilizzare i modelli di data mining in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. DMX consente di creare la struttura di nuovi modelli di data mining, eseguirne il training, nonché esplorarli, gestirli ed eseguire stime basate su tali modelli. DMX comprende istruzioni DDL (Data Definition Language) e DML (Data Manipulation Language), nonché funzioni e operatori.  
  
## <a name="microsoft-ole-db-for-data-mining-specification"></a>Specifica Microsoft OLE DB for Data Mining  
 Le funzionalità di data mining [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] vengono compilate in modo conforme con il [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB per la specifica di Data Mining.  
  
 Il [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB specifiche di Data Mining definisce le operazioni seguenti:  
  
-   Una struttura per contenere le informazioni che definiscono un modello di data mining.  
  
-   Un linguaggio per la creazione e l'utilizzo di modelli di data mining.  
  
 La specifica definisce gli aspetti fondamentali del data mining, ad esempio l'oggetto virtuale modello di data mining. L'oggetto modello di data mining incapsula tutte le informazioni note su un determinato modello di data mining. Tale oggetto è strutturato come una tabella SQL, con colonne, tipi di dati e metainformazioni che descrivono il modello. Grazie a questa struttura è possibile utilizzare il linguaggio DMX, che è un'estensione di SQL, per creare e utilizzare i modelli.  
  
 **Per ulteriori informazioni:** [di Data Mining strutture &#40; Analysis Services - Data Mining &#41;](../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
##  <a name="BKMK_DMXStatements"></a>Istruzioni DMX  
 È possibile utilizzare istruzioni DMX per creare, elaborare, eliminare, copiare ed esplorare modelli di data mining e generare stime basate su tali modelli. DMX include due tipi di istruzioni, le istruzioni per la definizione dei dati e istruzioni per la manipolazione dei dati. Ogni tipo di istruzione consente di eseguire attività diverse.  
  
 Ulteriori informazioni sull'utilizzo delle istruzioni DMX sono disponibili nelle sezioni seguenti:  
  
-   [Istruzioni di definizione dei dati](#BKMK_DDL)  
  
-   [Istruzioni di manipolazione dei dati](#BKMK_DML)  
  
-   [Nozioni fondamentali sulle query](#BKMK_Queries)  
  
###  <a name="BKMK_DDL"></a>Istruzioni di definizione dei dati  
 Le istruzioni DMX per la definizione dei dati consentono di creare e definire nuovi modelli e strutture di data mining, importare ed esportare modelli e strutture di data mining ed eliminare i modelli esistenti da un database. Le istruzioni DMX per la definizione dei dati fanno parte del linguaggio DDL (Data Definition Language).  
  
 Le istruzioni DMX per la definizione dei dati consentono di eseguire le attività seguenti:  
  
-   Creare una struttura di data mining utilizzando il [CREATE MINING STRUCTURE](../dmx/create-mining-structure-dmx.md) istruzione e aggiungere un modello di data mining alla struttura di data mining utilizzando il [ALTER MINING STRUCTURE](../dmx/alter-mining-structure-dmx.md) istruzione.  
  
-   Creare contemporaneamente un modello di data mining e la struttura di data mining associati utilizzando il [CREATE MINING MODEL](../dmx/create-mining-model-dmx.md) istruzione per compilare un oggetto del modello di data mining i dati vuoti.  
  
-   Esportare un modello di data mining e la struttura di data mining associati a un file utilizzando il [ESPORTARE](../dmx/export-dmx.md) istruzione. Importare un modello di data mining e la struttura di data mining associati da un file che viene creato dall'istruzione esportazione utilizzando il [importazione](../dmx/import-dmx.md) istruzione.  
  
-   Copiare la struttura di un modello di data mining esistente in un nuovo modello ed eseguirne il training con gli stessi dati, utilizzando il [SELECT INTO](../dmx/select-into-dmx.md) istruzione.  
  
-   Rimuovere completamente un modello di data mining da un database utilizzando il [DROP MINING MODEL](../dmx/drop-mining-model-dmx.md) istruzione. Rimuovere completamente una struttura di data mining e tutti i modelli di data mining associati dal database utilizzando il [DROP MINING STRUCTURE](../dmx/drop-mining-structure-dmx.md) istruzione.  
  
 Per ulteriori informazioni sulle attività di data mining di dati che è possibile eseguire tramite istruzioni DMX, vedere [DMX Data Mining Extensions &#40; &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md).  
  
 [Torna a istruzioni DMX](#BKMK_DMXStatements)  
  
###  <a name="BKMK_DML"></a>Istruzioni di manipolazione dei dati  
 Le istruzioni DMX per la manipolazione dei dati consentono di utilizzare modelli di data mining esistenti, esplorare i modelli e creare stime basate su di essi. Le istruzioni DMX per la manipolazione dei dati fanno parte del linguaggio DML (Data Manipulation Language).  
  
 Le istruzioni DMX per la manipolazione dei dati consentono di eseguire le attività seguenti:  
  
-   Eseguire il training di un modello di data mining utilizzando il [INSERT INTO](../dmx/insert-into-dmx.md) istruzione. Tale istruzione non inserisce i dati effettivi dell'origine in un oggetto modello di data mining, ma crea un'astrazione che descrive il modello di data mining creato dall'algoritmo. La query di origine per un'istruzione INSERT INTO è descritta in [ \<query di origine dati >](../dmx/source-data-query.md).  
  
-   Estendere l'istruzione SELECT per visualizzare le informazioni calcolate durante il training del modello e archiviate nel modello di data mining, ad esempio le statistiche dei dati di origine. Di seguito sono le clausole che è possibile includere per estendere le funzionalità dell'istruzione SELECT:  
  
    -   [SELECT DISTINCT FROM &#60; modello di &#62; &#40; DMX &#41;](../dmx/select-distinct-from-model-dmx.md)  
  
    -   [SELECT FROM &#60; modello di &#62;. DMX contenuto &#40; &#41;](../dmx/select-from-model-content-dmx.md)  
  
    -   [SELECT FROM &#60; modello di &#62;. DMX casi &#40; &#41;](../dmx/select-from-model-cases-dmx.md)  
  
    -   [SELECT FROM &#60; modello di &#62;. DMX SAMPLE_CASES &#40; &#41;](../dmx/select-from-model-sample-cases-dmx.md)  
  
    -   [SELECT FROM &#60; modello di &#62;. DMX DIMENSION_CONTENT &#40; &#41;](../dmx/select-from-model-dimension-content-dmx.md)  
  
-   Creare stime basate su un modello di data mining esistente utilizzando il [PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) clausola dell'istruzione SELECT. La query di origine per un'istruzione PREDICTION JOIN è descritta in [ \<query di origine dati >](../dmx/source-data-query.md).  
  
-   Rimuovere tutti i dati con Training da un modello o una struttura utilizzando il [DMX DELETE &#40; &#41;](../dmx/delete-dmx.md) istruzione.  
  
 Per ulteriori informazioni sulle attività di data mining di dati che è possibile eseguire tramite istruzioni DMX, vedere [DMX Data Mining Extensions &#40; &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md).  
  
 [Torna a istruzioni DMX](#BKMK_DMXStatements)  
  
###  <a name="BKMK_Queries"></a>Nozioni fondamentali sulle Query DMX  
 L'istruzione SELECT è la base per la maggior parte delle query DMX. A seconda delle clausole utilizzate con tale istruzione, è possibile visualizzare o copiare modelli di data mining oppure eseguire stime basate su tali modelli. La query di stima utilizza una forma di selezionare per creare stime basate sui modelli di data mining esistente. È inoltre possibile utilizzare funzioni per estendere oltre le capacità intrinseche del modello di data mining le funzionalità di esplorazione e per l'esecuzione di query sui modelli di data mining.  
  
 Le funzioni DMX consentono di calcolare nuove informazioni e di ottenere informazioni individuate durante il training dei modelli. È possibile utilizzare tali funzioni per vari scopi, inclusa la generazione di statistiche che descrivono i dati sottostanti o l'accuratezza di una stima oppure una descrizione dettagliata di una stima.  
  
 **Per ulteriori informazioni****informazioni:** [DMX comprensione di un'istruzione Select](../dmx/understanding-the-dmx-select-statement.md), [DMX funzioni di stima generale &#40; &#41;](../dmx/general-prediction-functions-dmx.md), [struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md), [DMX Data Mining Extensions &#40; &#41; Riferimento (funzione)  ](../dmx/data-mining-extensions-dmx-function-reference.md)  
  
 [Torna a istruzioni DMX](#BKMK_DMXStatements)  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40; DMX &#41; Convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40; DMX &#41; Elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
