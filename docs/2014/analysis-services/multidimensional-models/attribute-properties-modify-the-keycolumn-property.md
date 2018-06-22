---
title: Modificare la proprietà KeyColumn di un attributo | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- binding attributes [Analysis Services]
- attributes [Analysis Services], binding
- key columns [Analysis Services]
ms.assetid: a2643be4-8123-4cc3-baf9-e5ec54a1669d
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 68a1759aa5a527037c87efc6763ac81e40958d2d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062984"
---
# <a name="modify-the-keycolumn-property-of-an-attribute"></a>Modificare la proprietà KeyColumn di un attributo
  È possibile modificare la proprietà **KeyColumns** di un attributo. Ad esempio, è possibile specificare una chiave composta anziché una chiave semplice come chiave dell'attributo.  
  
### <a name="to-modify-the-keycolumns-property-of-an-attribute"></a>Per modificare la proprietà KeyColumns di un attributo  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto nel quale si vuole modificare la proprietà **KeyColumns** .  
  
2.  Aprire Progettazione dimensioni effettuando una delle operazioni seguenti:  
  
    -   In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla dimensione nella cartella **Dimensioni** e quindi scegliere **Apri** o **Progettazione viste**.  
  
         -oppure-  
  
    -   In Progettazione cubi nel **struttura cubo** scheda, espandere la dimensione del cubo nel **dimensioni** riquadro e fare clic su **modifica \<dimensione >**.  
  
3.  Nel riquadro **Attributi** della scheda **Struttura dimensione** fare clic sull'attributo per il quale si vuole modificare la proprietà **KeyColumns** .  
  
4.  Nella finestra **Proprietà** fare clic sul valore della proprietà **KeyColumns** .  
  
5.  Fare clic sul pulsante di ricerca ( **...** ) che viene visualizzato nella cella del valore della casella delle proprietà.  
  
     Verrà visualizzata la finestra di dialogo **Colonne chiave** .  
  
6.  Per rimuovere una colonna chiave esistente, nell'elenco **Colonne chiave** selezionare la colonna e quindi fare clic sul pulsante **\<** .  
  
7.  Per aggiungere una colonna chiave, nell'elenco **Colonne disponibili** selezionare la colonna e quindi fare clic sul pulsante **>** .  
  
    > [!NOTE]  
    >  Se si definiscono più colonne chiave, l'ordine di visualizzazione di tali colonne nell'elenco **Colonne chiave** influisce sull'ordine visualizzato. Ad esempio, l'attributo mese ha due colonne chiave: mese ed anno. Se la colonna anno è visualizzata nell'elenco prima della colonna mese, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ordina per anno e quindi per mese. Se la colonna mese appare prima della colonna anno, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ordina per mese e quindi per anno.  
  
8.  Per modificare l'ordine delle colonne chiave, selezionare una colonna e quindi fare clic sul pulsante **Su** o **Giù** .  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle proprietà degli attributi delle dimensioni](dimension-attribute-properties-reference.md)  
  
  