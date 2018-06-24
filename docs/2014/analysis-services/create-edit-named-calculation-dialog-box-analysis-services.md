---
title: Creare una modifica denominata finestra di dialogo calcolo (Analysis Services) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 007fce8fae62df381629b4daa1b6ef0c00d781bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054664"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a>Creare, modificare la finestra di dialogo calcolo denominato (Analysis Services)
  Usare la finestra di dialogo **Crea calcolo denominato o Modifica calcolo denominato** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] per definire o modificare un calcolo denominato per una tabella in una vista origine dati. Per visualizzare la finestra di dialogo **Crea calcolo denominato o Modifica calcolo denominato** è possibile:  
  
-   Fare clic su **Nuovo calcolo denominato** nel riquadro **Barra degli strumenti** di **Progettazione Vista origine dati**.  
  
-   Fare clic con il pulsante destro del mouse su una tabella nel riquadro **Tabelle** o **Diagramma**di **Progettazione vista origine dati** e scegliere **Nuovo calcolo denominato**.  
  
-   Fare clic con il pulsante destro del mouse sul nome di un calcolo denominato nel riquadro **Diagramma** di **Progettazione vista origine dati** e scegliere **Modifica calcolo denominato**.  
  
## <a name="options"></a>Opzioni  
 **Nome colonna**  
 Consente di digitare il nome del calcolo denominato.  
  
 **Descrizione**  
 Consente di digitare la descrizione facoltativa del calcolo denominato.  
  
 **Espressione**  
 Consente di digitare un'espressione SQL valida che restituisce un valore scalare. L'espressione viene inviata al provider e convalidata nell'espressione seguente:  
  
```  
SELECT <Table Name in Data Source>.* , <Expression> AS <Column Name> FROM <Table Name in Data Source>AS <Table Name in Data Source View>  
```  
  
 L'espressione può contenere riferimenti ad altre tabelle specificati mediante un'istruzione sub-SELECT. If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre di progettazione e finestre di dialogo di Analysis Services &#40;dati multidimensionali&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Progettazione vista origine dati &#40;Analysis Services - dati multidimensionali&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  