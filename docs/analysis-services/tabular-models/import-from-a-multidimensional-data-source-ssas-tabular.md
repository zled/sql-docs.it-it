---
title: "Importare da un&#39;origine dati multidimensionale (SSAS tabulare) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Importare da un&#39;origine dati multidimensionale (SSAS tabulare)
  Un database del cubo di Analysis Services può essere utilizzato come origine dati per un modello tabulare. Per importare dati da un cubo di Analysis Services, è necessario definire una query MDX per selezionare i dati da importare.  
  
 È possibile importare in un modello qualsiasi tipo di dati contenuto in un database di SQL Server Analysis Services. È possibile estrarre tutta o parte di una dimensione oppure ottenere sezioni e funzioni di aggregazione dal cubo, ad esempio la somma mensile delle vendite per l'anno corrente, e così via. È tuttavia necessario tenere presente che tutti i dati importati da un cubo sono bidimensionali. Se pertanto si definisce una query che consente di recuperare misure in base a più dimensioni, ogni dimensione dei dati verrà importata in una colonna separata.  
  
 La versione dei cubi di Analysis Services deve essere SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
### Per importare dati da un cubo di Analysis Services  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]fare clic sul menu **Modello** , quindi selezionare **Importa da origine dati**.  
  
2.  Selezionare **Microsoft Analysis Services** nella pagina **Connessione a un'origine dati**, quindi scegliere **Avanti**.  
  
3.  Seguire i passaggi nell'Importazione guidata tabella. Sarà possibile specificare una query MDX nella pagina **Specifica di una query MDX** . Per utilizzare Progettazione query MDX, nella pagina Specifica di una query MDX fare clic su **Progettazione**.  
  
## Vedere anche  
 [Importare dati &#40;SSAS tabulare&#41;](../Topic/Import%20Data%20\(SSAS%20Tabular\).md)   
 [Origini dati supportate &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  