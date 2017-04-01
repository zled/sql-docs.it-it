---
title: "Aggiungere un attributo a una dimensione | Microsoft Docs"
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
helpviewer_keywords: 
  - "aggiunta di attributi"
  - "creazione automatica di attributi"
  - "attributi [Analysis Services], creazione"
  - "attributi [Analysis Services], aggiunta"
  - "creazione manuale di attributi [Analysis Services]"
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
caps.latest.revision: 32
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Aggiungere un attributo a una dimensione
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è possibile aggiungere un attributo a una dimensione automaticamente o manualmente.  
  
 Per creare un attributo automaticamente, nella scheda **Struttura dimensione** di Progettazione dimensioni, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], selezionare la colonna di cui si vuole eseguire il mapping a un attributo e quindi trascinare tale colonna nel riquadro **Attributi** dal riquadro **Vista origine dati**. Verrà creato un attributo di cui viene eseguito il mapping alla colonna al quale verrà assegnato lo stesso nome della colonna. Se esiste già un attributo con lo stesso nome, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aggiungerà al nome un suffisso composto da un numero ordinale, a partire da "1" per il primo nome duplicato.  
  
 Per creare un attributo manualmente, attivare la visualizzazione griglia nel riquadro **Attributi**. Nella colonna del nome dell'ultima riga della griglia fare clic sull'elemento **\<nuovo attributo>**. Digitare un nome per il nuovo attributo. Verrà creato un attributo di cui viene eseguito il mapping a una colonna con le impostazioni predefinite per tutte le proprietà. È possibile impostare il mapping nella finestra **Proprietà** di [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] configurando la proprietà **KeyColumns** del nuovo attributo.  
  
 Per altre informazioni, vedere [Definire automaticamente un nuovo attributo](../../analysis-services/multidimensional-models/define-a-new-attribute-automatically.md), [Definire manualmente un nuovo attributo](../Topic/Define%20a%20New%20Attribute%20Manually.md), [Associare un attributo a una colonna del nome](../../analysis-services/multidimensional-models/bind-an-attribute-to-a-name-column.md) e [Modificare la proprietà KeyColumn di un attributo](../../analysis-services/multidimensional-models/modify-the-keycolumn-property-of-an-attribute.md).  
  
## Vedere anche  
 [Riferimento alle proprietà degli attributi delle dimensioni](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  