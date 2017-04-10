---
title: "Modelli tabulari (SSAS) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 17
---
# Modelli tabulari (SSAS)
  I modelli tabulari sono database di Analysis Services eseguiti in memoria in o in modalità DirectQuery, che accedono ai dati direttamente dalle origini dati relazionali di back-end.  
  
 Il valore predefinito è in memoria. Usando un processore di query multithreading e algoritmi di compressione all'avanguardia, il motore di analisi in memoria offre accesso rapido ai dati e agli oggetti del modello tabulare con applicazioni client di creazione di report quali Microsoft Excel e Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].  
  
 DirectQuery è una modalità di query alternativa usata per i modelli che sono troppo grandi per rientrare nella memoria o quando la volatilità dei dati preclude una strategia di elaborazione ragionevole. In questa versione, DirectQuery offre maggiore parità con i modelli in memoria attraverso il supporto di altre origini dati, la capacità di gestire tabelle e colonne calcolate in un modello DirectQuery, la sicurezza a livello di riga con espressioni DAX che raggiungono il database back-end e le ottimizzazioni delle query che comportano una velocità effettiva maggiore rispetto alle versioni precedenti. Per sfruttare i vantaggi dei recenti miglioramenti è necessario il livello di compatibilità 1200, introdotto in questa versione.  
  
 I modelli tabulari vengono creati [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usando il modello di progetto di modello tabulare che offre un'area di progettazione per la creazione di un modello, tabelle, relazioni ed espressioni DAX. È possibile importare i dati da più origini e migliorare il modello aggiungendo relazioni, tabelle colonne calcolate, misure, indicatori KPI, gerarchie e traduzioni.  
  
 I modelli possono essere quindi distribuiti in un'istanza di Analysis Services configurata per la modalità di server tabulare, in cui le applicazioni di reporting client possono connettersi ai modelli. I modelli distribuiti possono essere gestiti in SQL Server Management Studio solo come modelli multidimensionali. Tali modelli, inoltre, possono essere partizionati per elaborazioni ottimizzate e protetti a livello di riga tramite ruoli basati sulla sicurezza.  
  
## Contenuto della sezione  
 [Soluzioni di modelli tabulari &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md): gli argomenti di questa sezione illustrano la creazione e distribuzione di soluzioni di modelli tabulari.
  
 [Database modello tabulare &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md): gli argomenti di questa sezione illustrano la gestione di soluzioni di modelli tabulari distribuiti.
  
 [Accesso ai dati di modello tabulare](../../analysis-services/tabular-models/tabular-model-data-access.md): gli argomenti di questa sezione illustrano la connessione alle soluzioni di modelli tabulari distribuiti.
  
## Vedere anche  
 [Novità di Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Confronto tra soluzioni tabulari e multidimensionali &#40;SSAS&#41;](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Strumenti e applicazioni usati in Analysis Services](../../analysis-services/tools-and-applications-used-in-analysis-services.md)   
 [Modalità DirectQuery &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Livello di compatibilità per i modelli tabulari in Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  