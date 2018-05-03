---
title: Sviluppo con Analysis Services Scripting Language (ASSL) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2f2af5b141744f60a6005050eb74bbc4c9cb97c5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Sviluppo con Analysis Services Scripting Language (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  ASSL (Analysis Services Scripting Language) è un'estensione di XMLA che aggiunge un linguaggio di definizione dell'oggetto e un linguaggio di comando per la creazione e la gestione di strutture di Analysis Services direttamente sul server. È possibile utilizzare ASSL in un'applicazione personalizzata per comunicare con Analysis Services mediante il protocollo XMLA. Il linguaggio ASSL è costituito da due componenti:  
  
-   Linguaggio DDL (Data Definition Language), o linguaggio di definizione dell'oggetto, che specifica e descrive un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nonché i database e gli oggetti di database che l'istanza contiene.  
  
-   Un linguaggio di comando che invia i comandi di azione, ad esempio **crea**, **Alter**, o **processo**, a un'istanza di Analysis Services. Tale linguaggio di comando verrà discusso il [XML for Analysis &#40;XMLA&#41; riferimento](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md).  
  
 Per visualizzare l'ASSL che descrive una soluzione multidimensionale in [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], è possibile utilizzare il comando Visualizza codice al livello del progetto. È inoltre possibile creare o modificare script ASSL in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] utilizzando l'editor di query XMLA. Gli script compilati possono essere utilizzati per gestire oggetti o eseguire comandi nel server.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti ASSL e le caratteristiche degli oggetti](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)   
 [Convenzioni XML ASSL](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-xml-conventions.md)   
 [Origini dati e associazioni & #40; SSAS multidimensionale & #41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)  
  
  
