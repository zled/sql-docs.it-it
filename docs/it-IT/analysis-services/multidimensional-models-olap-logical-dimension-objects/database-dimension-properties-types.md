---
title: Tipi di dimensione | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c36b8c16acb2521c2472b1f4398cb68ea89952d2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="database-dimension-properties---types"></a>Proprietà dimensione - tipi di database
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
|Utility|Dimensione i cui attributi rappresentano informazioni di vario tipo.|  
|Currency|Questo tipo di dimensione contiene dati e metadati relativi alla valuta.|  
|Rates|Dimensione i cui attributi rappresentano informazioni sui tassi valutari.|  
|Channel|Dimensione i cui attributi rappresentano informazioni sul canale.|  
|Promotion|Dimensione i cui attributi rappresentano informazioni sulle promozioni marketing.|  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una dimensione utilizzando una tabella esistente](../../analysis-services/multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Dimensioni & #40; Analysis Services - dati multidimensionali & #41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
