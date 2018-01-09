---
title: Documentazione e Script per un Database di Analysis Services | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML for Analysis, scripts
- XMLA, scripts
- scripts [Analysis Services], databases
- documenting databases
- databases [Analysis Services], documenting
- databases [Analysis Services], scripts
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ba1f7a1a969b055261f5b32955b18ad83941e3c9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="document-and-script-an-analysis-services-database"></a>Documentazione e script per un database di Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Dopo un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database viene distribuito, è possibile utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] XML for Analysis (XMLA) per restituire i metadati del database o di un oggetto contenuto nel database, uno script. È possibile salvare l'output di questo script in una nuova finestra dell' **Editor di query XMLA** , in un file o negli Appunti. Per altre informazioni su XMLA, vedere [Guida di riferimento ad Analysis Services Scripting Language &#40;ASSL&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
 Lo script XMLA generato utilizza gli elementi ASSL ([!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language) per definire gli oggetti contenuti nello script. Se è stato generato uno script CREATE, lo script XMLA risultante contiene un comando XMLA **Create** e gli elementi ASSL che consentono di creare l'intera struttura del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in un'istanza. Se è stato generato uno script ALTER, lo script XMLA risultante contiene un comando XMLA **Alter** e gli elementi ASSL che consentono di ripristinare lo stato in cui si trovava la struttura di un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esistente al momento della creazione dello script.  
  
 È possibile utilizzare in vari modi lo script XMLA generato da un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ad esempio per gli scopi seguenti:  
  
-   Per mantenere uno script di backup che consente di ricreare tutti gli oggetti e le autorizzazioni di database.  
  
-   Per creare o aggiornare il codice di sviluppo del database.  
  
-   Per creare un ambiente di prova o di sviluppo da uno schema esistente.  
  
## <a name="see-also"></a>Vedere anche  
 [Modificare o eliminare un database di Analysis Services](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)   
 [Modificare l'elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)   
 [Creare l'elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)  
  
  
