---
title: "Creare una dimensione di data mining | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strutture di data mining [Analysis Services], dimensioni"
ms.assetid: 9f0c39e5-3516-43ab-b203-f3f6dbcff89a
caps.latest.revision: 12
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 12
---
# Creare una dimensione di data mining
  Se la struttura di data mining è basata su un cubo OLAP, è possibile creare una dimensione che includa il contenuto del modello di data mining. È quindi possibile includere nuovamente la dimensione nel cubo di origine.  
  
 È inoltre possibile esplorare la dimensione, utilizzarla per esplorare i risultati del modello o eseguire una query sulla dimensione tramite MDX.  
  
### Per creare una dimensione di data mining  
  
1.  In Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] selezionare la scheda **Struttura di data mining** o **Modelli di data mining**.  
  
2.  Scegliere **Crea dimensione di data mining** dal menu **Modello di data mining**.  
  
     Verrà visualizzata la finestra di dialogo **Crea dimensione di data mining**.  
  
3.  Nell'elenco **Nome modello** della finestra di dialogo **Crea dimensione di data mining** selezionare un modello di data mining OLAP.  
  
4.  Nella casella **Nome dimensione** immettere un nome per la nuova dimensione di data mining.  
  
5.  Per creare un cubo che includa la nuova dimensione di data mining, selezionare **Crea cubo**. Dopo avere fatto clic su **Crea cubo**, è possibile immettere un nuovo nome per il cubo.  
  
6.  Scegliere **OK**.  
  
     La dimensione di data mining verrà creata e aggiunta alla cartella **Dimensioni** in Esplora soluzioni. Se è stata selezionata l'opzione **Crea cubo** verrà anche creato un nuovo cubo, che verrà aggiunto alla cartella **Cubi**.  
  
## Vedere anche  
 [Attività e procedure relative alla struttura di data mining](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  