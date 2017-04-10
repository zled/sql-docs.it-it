---
title: "Rinominare una tabella o una colonna (SSAS tabulare) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.renametableorcolumn.f1"
ms.assetid: 88061a39-c5aa-403d-a52b-7fdb365fc235
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 11
---
# Rinominare una tabella o una colonna (SSAS tabulare)
  È possibile modificare il nome di una tabella durante il processo di importazione digitando un **Nome descrittivo** nella pagina **Selezione tabelle e viste** dell' **Importazione guidata tabella**. È possibile modificare anche i nomi di tabelle e colonne se si importano dati specificando una query nella pagina **Specifica di una query SQL** dell' **Importazione guidata tabella**.  
  
 Dopo aver aggiunto i dati al modello, il nome o titolo di una tabella viene visualizzato nella scheda della tabella nella parte inferiore di Progettazione modelli. È possibile modificare il nome della tabella al fine di assegnarne uno più appropriato. È possibile anche rinominare una colonna dopo l'aggiunta dei dati al modello. Questa opzione risulta particolarmente importante quando si importano dati da più origini e si vuole essere sicuri che le colonne nelle differenti tabelle abbiano nomi facilmente distinguibili.  
  
### Per rinominare una tabella  
  
1.  In Progettazione modelli fare clic con il pulsante destro del mouse sulla scheda contenente la tabella da rinominare, quindi scegliere **Rinomina**.  
  
2.  Digitare il nuovo nome.  
  
    > [!NOTE]  
    >  È possibile modificare altre proprietà di una tabella, incluse le informazioni di connessione e i mapping di colonne, tramite la finestra di dialogo **Modifica proprietà tabella** . Tuttavia, in questa finestra non è possibile modificare il nome.  
  
### Per rinominare una colonna  
  
1.  In Progettazione modelli fare doppio clic sull'intestazione della colonna da rinominare o fare clic con il pulsante destro del mouse e selezionare **Rinomina colonna** nel menu di scelta rapida.  
  
2.  Digitare il nuovo nome.  
  
## Requisiti di denominazione per colonne e tabelle  
 Nel nome di una tabella o di una colonna non è possibile utilizzare le parole e i caratteri seguenti:  
  
-   Spazi iniziali o finali  
  
-   Caratteri di controllo  
  
-   I caratteri seguenti, che non sono validi nei nomi degli oggetti di Analysis Services: .,;':/\\*|?&%$!+=()[]{}<>  
  
-   Le parole chiave riservate di Analysis Services, inclusi i nomi delle funzioni e gli operatori MDX (Multidimensional Expressions) e DMX (Data Mining Extensions).  
  
## Effetto della ridenominazione su tabelle, colonne e calcoli esistenti  
 Modificando il nome di una tabella, si modifica il nome dell'oggetto tabella sottostante, che può contenere più colonne o misure. È pertanto necessario aggiornare tutte le colonne presenti nella tabella, nonché tutte le relazioni che coinvolgono la tabella, in modo che utilizzino il nuovo nome nelle relative definizioni. Tale aggiornamento viene eseguito automaticamente in alcuni casi. Le misure non sono aggiornate automaticamente.  
  
 È necessario aggiornare inoltre tutti i calcoli che utilizzano la tabella rinominata o le relative colonne, nonché i dati da essi derivati, che devono essere ricalcolati. A seconda del numero di tabelle e di calcoli interessati, l'operazione può richiedere del tempo prima di essere completata. Il momento migliore per rinominare le tabelle ricade pertanto nell'arco del processo di importazione o prima dell'inizio della compilazione di relazioni e calcoli complessi.  
  
## Vedere anche  
 [Tabelle e colonne &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)   
 [Importare da Power Pivot &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)   
 [Importare da Analysis Services &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/import-from-analysis-services-ssas-tabular.md)  
  
  