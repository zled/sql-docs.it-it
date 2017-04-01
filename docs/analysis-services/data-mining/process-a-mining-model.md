---
title: "Elaborare un modello di data mining | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelli di data mining [Analysis Services], elaborazione"
ms.assetid: c2204472-c500-47a5-9afa-7ce2ca78b233
caps.latest.revision: 32
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 32
---
# Elaborare un modello di data mining
  La scheda Modelli di data mining di Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] consente di elaborare un modello di data mining specifico associato a una struttura di data mining oppure tutti i modelli associati alla struttura.  
  
 È possibile elaborare un modello di data mining utilizzando gli strumenti seguenti:  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
 Inoltre, è possibile utilizzare un comando di elaborazione XMLA. Per altre informazioni, vedere [Strumenti e approcci per l’elaborazione &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/tools-and-approaches-for-processing-analysis-services.md).  
  
### Elaborare un singolo modello di data mining utilizzando SQL Server Data Tools  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining selezionare un modello di data mining in una o più colonne di modelli nella griglia.  
  
2.  Scegliere **Elabora modello** dal menu **Modello di data mining**.  
  
     Se sono state apportate modifiche alla struttura di data mining, prima di elaborare il modello verrà richiesto di ridistribuire la struttura. Scegliere **Sì**.  
  
3.  Nella finestra di dialogo **Elabora modello di data mining - \<modello>** fare clic su **Esegui**.  
  
     Verrà visualizzata la finestra di dialogo **Stato elaborazione** contenente informazioni sull'elaborazione dei modelli.  
  
4.  Al termine dell'elaborazione del modello, fare clic su **Chiudi** nella finestra di dialogo **Stato elaborazione**.  
  
5.  Fare clic su **Chiudi** nella finestra di dialogo **Elabora modello di data mining - \<modello>**.  
  
 Tramite questa procedura sono stati elaborati solo la struttura di data mining e il modello di data mining associato.  
  
### Elaborare tutti i modelli di data mining associati a una struttura di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining scegliere **Elabora struttura di data mining e tutti i modelli** dal menu **Modello di data mining**.  
  
2.  Se sono state apportate modifiche alla struttura di data mining, prima di elaborare i modelli verrà richiesto di ridistribuire la struttura. Scegliere **Sì**.  
  
3.  Nella finestra di dialogo **Elabora Struttura di data mining - \<struttura>** fare clic su **Esegui**.  
  
4.  Verrà visualizzata la finestra di dialogo **Stato elaborazione** contenente informazioni sull'elaborazione dei modelli.  
  
5.  Al termine dell'elaborazione dei modelli, fare clic su **Chiudi** nella finestra di dialogo **Stato elaborazione**.  
  
6.  Fare clic su **Chiudi** nella finestra di dialogo **Elaborazione di \<modello>**.  
  
 Tramite questa procedura sono stati elaborati la struttura di data mining e tutti i modelli di data mining associati.  
  
## Vedere anche  
 [Attività e procedure relative al modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  