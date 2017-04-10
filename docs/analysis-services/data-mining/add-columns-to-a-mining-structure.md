---
title: "Aggiungere colonne a una struttura di data mining | Microsoft Docs"
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
  - "strutture di data mining [Analysis Services], colonne"
  - "colonne [data mining], colonne struttura di data mining"
  - "aggiunta di colonne"
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 30
---
# Aggiungere colonne a una struttura di data mining
  È possibile utilizzare Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] per aggiungere colonne a una struttura di data mining dopo averla definita tramite la Creazione guidata modello di data mining. È possibile aggiungere qualsiasi colonna presente nella vista origine dati utilizzata per definire la struttura di data mining.  
  
> [!NOTE]  
>  È possibile aggiungere più copie di colonne in una struttura di data mining; tuttavia, è consigliabile evitare di utilizzare più di un'istanza della colonna all'interno dello stesso modello, in modo da evitare false correlazioni tra la colonna di origine e quella derivata.  
  
### Per aggiungere una colonna a una struttura di data mining  
  
1.  Selezionare la scheda **Struttura di data mining** in Progettazione modelli di data mining.  
  
2.  Fare clic con il pulsante destro del mouse sulla struttura di data mining e scegliere **Aggiungi colonna**.  
  
     Verrà visualizzata la finestra di dialogo **Seleziona colonna**.  
  
3.  In **Tabella di origine** selezionare la tabella della vista origine dati in cui si trova la colonna.  
  
4.  In **Colonna di origine** selezionare la colonna che si desidera aggiungere alla struttura di data mining.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Se si aggiunge una colonna già esistente, nella struttura verrà inclusa una copia e al nome verrà aggiunto "1". È possibile specificare un nome più descrittivo per la colonna copiata digitandolo nella proprietà **Nome** della colonna della struttura di data mining.  
  
## Vedere anche  
 [Attività e procedure relative alla struttura di data mining](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  