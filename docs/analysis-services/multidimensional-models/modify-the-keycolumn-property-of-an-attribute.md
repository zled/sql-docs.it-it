---
title: "Modificare la propriet&#224; KeyColumn di un attributo | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "associazione di attributi [Analysis Services]"
  - "attributi [Analysis Services], associazione"
  - "colonne chiave [Analysis Services]"
ms.assetid: a2643be4-8123-4cc3-baf9-e5ec54a1669d
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Modificare la propriet&#224; KeyColumn di un attributo
  È possibile modificare la proprietà **KeyColumns** di un attributo. Ad esempio, è possibile specificare una chiave composta anziché una chiave semplice come chiave dell'attributo.  
  
### Per modificare la proprietà KeyColumns di un attributo  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il progetto nel quale si vuole modificare la proprietà **KeyColumns**.  
  
2.  Aprire Progettazione dimensioni effettuando una delle operazioni seguenti:  
  
    -   In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla dimensione nella cartella **Dimensioni** e quindi scegliere **Apri** o **Progettazione viste**.  
  
         -oppure-  
  
    -   In Progettazione cubi, nella scheda **Struttura cubo**, espandere la dimensione del cubo nel riquadro **Dimensioni** e fare clic su **Modifica \<dimensione>**.  
  
3.  Nel riquadro **Attributi** della scheda **Struttura dimensione** fare clic sull'attributo per il quale si vuole modificare la proprietà **KeyColumns**.  
  
4.  Nella finestra **Proprietà** fare clic sul valore della proprietà **KeyColumns**.  
  
5.  Fare clic sul pulsante di ricerca (**...**) che viene visualizzato nella cella del valore della casella delle proprietà.  
  
     Verrà visualizzata la finestra di dialogo **Colonne chiave**.  
  
6.  Per rimuovere una colonna chiave esistente, nell'elenco **Colonne chiave** selezionare la colonna e quindi fare clic sul pulsante **\<**.  
  
7.  Per aggiungere una colonna chiave, nell'elenco **Colonne disponibili** selezionare la colonna e quindi fare clic sul pulsante **>**.  
  
    > [!NOTE]  
    >  Se si definiscono più colonne chiave, l'ordine di visualizzazione di tali colonne nell'elenco **Colonne chiave** influisce sull'ordine visualizzato. Ad esempio, l'attributo mese ha due colonne chiave: mese ed anno. Se la colonna anno è visualizzata nell'elenco prima della colonna mese, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ordina per anno e quindi per mese. Se la colonna mese appare prima della colonna anno, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ordina per mese e quindi per anno.  
  
8.  Per modificare l'ordine delle colonne chiave, selezionare una colonna e quindi fare clic sul pulsante **Su** o **Giù**.  
  
## Vedere anche  
 [Riferimento alle proprietà degli attributi delle dimensioni](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  