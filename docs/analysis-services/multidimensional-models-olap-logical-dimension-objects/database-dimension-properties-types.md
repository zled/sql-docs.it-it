---
title: Tipi di dimensione | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- time dimensions [Analysis Services]
- quantitative dimensions [Analysis Services]
- BillOfMaterials dimension [Analysis Services]
- geography dimensions
- utility dimensions [Analysis Services]
- channel dimensions
- dimensions [Analysis Services], types
- products dimensions [Analysis Services]
- account dimensions [Analysis Services]
- organization dimensions
- currency dimensions [Analysis Services]
- rates dimensions
- promotion dimensions
- scenario dimensions [Analysis Services]
- customers dimensions [Analysis Services]
- Type property
ms.assetid: bd3195da-e762-4c98-b643-34c76e842343
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5fa77532b4c674c4b5035cf6b591b973008ae6e5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="database-dimension-properties---types"></a>Proprietà dimensione - tipi di database
  Il **tipo** l'impostazione della proprietà fornisce informazioni sul contenuto di una dimensione alle applicazioni client e server. In alcuni casi, il **tipo** impostazione solo vengono fornite indicazioni per le applicazioni client ed è facoltativo. In altri casi, ad esempio **account** o **ora** dimensioni, il **tipo** impostazioni delle proprietà per la dimensione e i relativi attributi determinano comportamenti specifici basati su server e può essere richiesto per implementare determinati comportamenti nel cubo. Ad esempio, il **tipo** di una dimensione può essere impostata su **account** per indicare alle applicazioni client che la dimensione standard contiene attributi conto. Per ulteriori informazioni sull'ora, l'account e dimensioni di tipo valuta, vedere [creare una dimensione di tipo data](../../analysis-services/multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [creare un conto finanziario della dimensione di tipo padre-figlio](../../analysis-services/multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), e [creare una valuta tipo di dimensione](../../analysis-services/multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).  
  
 L'impostazione predefinita per il tipo di dimensione è **regolare**, che non vi sono presupposizioni sul contenuto della dimensione. Questo è l'impostazione predefinita per tutte le dimensioni quando si definisce inizialmente una dimensione a meno che non si specifica **ora** quando si definisce una dimensione utilizzando la creazione guidata dimensione. È inoltre consigliabile lasciare **regolare** come tipo di dimensione, se la creazione guidata dimensione non è elencato un tipo appropriato per il tipo di dimensione.  
  
## <a name="available-dimension-types"></a>Tipi di dimensioni disponibili  
 Nella tabella seguente vengono descritti i tipi di dimensioni disponibili in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Tipo dimensione|Description|  
|--------------------|-----------------|  
|Regular|Dimensione il cui tipo non è stato impostato in base a un valore speciale.|  
|Time|Dimensione i cui attributi rappresentano periodi di tempo, ad esempio anni, semestri, trimestri, mesi e giorni.|  
|Organization|Dimensione i cui attributi rappresentano informazioni sull'organizzazione, ad esempio dipendenti o filiali.|  
|Geography|Dimensione i cui attributi rappresentano informazioni geografiche, ad esempio città o CAP.|  
|BillOfMaterials|Dimensione i cui attributi rappresentano informazioni relative alle scorte o alla produzione, ad esempio elenchi di parti di prodotti.|  
|Accounts|Dimensione i cui attributi rappresentano un grafico dei conti per la generazione di report finanziari.|  
|Customers|Dimensione i cui attributi rappresentano informazioni sui clienti o sui contatti.|  
|Products|Dimensione i cui attributi rappresentano informazioni sui prodotti.|  
|Scenario|Dimensione i cui attributi rappresentano informazioni di pianificazione o di analisi strategica.|  
|Quantitative|Dimensione i cui attributi rappresentano informazioni sulle quantità.|  
|Utilità|Dimensione i cui attributi rappresentano informazioni di vario tipo.|  
|Currency|Questo tipo di dimensione contiene dati e metadati relativi alla valuta.|  
|Rates|Dimensione i cui attributi rappresentano informazioni sui tassi valutari.|  
|Channel|Dimensione i cui attributi rappresentano informazioni sul canale.|  
|Promotion|Dimensione i cui attributi rappresentano informazioni sulle promozioni marketing.|  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una dimensione utilizzando una tabella esistente](../../analysis-services/multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Dimensioni &#40;Analysis Services - Dati multidimensionali&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
