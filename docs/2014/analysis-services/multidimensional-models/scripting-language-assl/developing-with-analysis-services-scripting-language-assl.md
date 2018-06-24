---
title: Sviluppo con Analysis Services Scripting Language (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e7cc4d26ca41b36bc1472417d64702345911ceec
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064346"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Sviluppo con Analysis Services Scripting Language (ASSL)
  ASSL (Analysis Services Scripting Language) è un'estensione di XMLA che aggiunge un linguaggio di definizione dell'oggetto e un linguaggio di comando per la creazione e la gestione di strutture di Analysis Services direttamente sul server. È possibile utilizzare ASSL in un'applicazione personalizzata per comunicare con Analysis Services mediante il protocollo XMLA. Il linguaggio ASSL è costituito da due componenti:  
  
-   Linguaggio DDL (Data Definition Language), o linguaggio di definizione dell'oggetto, che specifica e descrive un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nonché i database e gli oggetti di database che l'istanza contiene.  
  
-   Linguaggio di comando che invia comandi di azione, ad esempio `Create`, `Alter` o `Process`, a un'istanza di Analysis Services. Tale linguaggio di comando verrà discusso il [XML for Analysis &#40;XMLA&#41; riferimento](../../xmla/xml-for-analysis-xmla-reference.md).  
  
 Per visualizzare l'ASSL che descrive una soluzione multidimensionale in [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], è possibile utilizzare il comando Visualizza codice al livello del progetto. È inoltre possibile creare o modificare script ASSL in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] utilizzando l'editor di query XMLA. Gli script compilati possono essere utilizzati per gestire oggetti o eseguire comandi nel server.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti ASSL e relative caratteristiche](assl-objects-and-object-characteristics.md)   
 [Convenzioni XML di ASSL](assl-xml-conventions.md)   
 [Origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../data-sources-and-bindings-ssas-multidimensional.md)  
  
  