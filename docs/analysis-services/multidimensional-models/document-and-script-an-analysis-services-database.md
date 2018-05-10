---
title: Documentazione e Script per un Database di Analysis Services | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 645499bc5311f74ba689b3cd48d2516c01d384fb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="document-and-script-an-analysis-services-database"></a>Documentazione e script per un database di Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Dopo la distribuzione di un database [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , è possibile usare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per generare l'output dei metadati del database o di un oggetto contenuto nel database in formato di script XMLA (XML for Analysis). È possibile salvare l'output di questo script in una nuova finestra dell'**Editor di query XMLA**, in un file o negli Appunti. Per altre informazioni su XMLA, vedere [Guida di riferimento ad Analysis Services Scripting Language &#40;ASSL&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
 Lo script XMLA generato utilizza gli elementi ASSL ([!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language) per definire gli oggetti contenuti nello script. Se è stato generato uno script CREATE, lo script XMLA risultante contiene un comando XMLA **Create** e gli elementi ASSL che consentono di creare l'intera struttura del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in un'istanza. Se è stato generato uno script ALTER, lo script XMLA risultante contiene un comando XMLA **Alter** e gli elementi ASSL che consentono di ripristinare lo stato in cui si trovava la struttura di un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esistente al momento della creazione dello script.  
  
 È possibile utilizzare in vari modi lo script XMLA generato da un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ad esempio per gli scopi seguenti:  
  
-   Per mantenere uno script di backup che consente di ricreare tutti gli oggetti e le autorizzazioni di database.  
  
-   Per creare o aggiornare il codice di sviluppo del database.  
  
-   Per creare un ambiente di prova o di sviluppo da uno schema esistente.  
  
## <a name="see-also"></a>Vedere anche  
 [Modificare o eliminare un database di Analysis Services](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)   
 [Elemento ALTER &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)   
 [Creare l'elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)  
  
  
