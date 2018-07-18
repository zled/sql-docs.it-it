---
title: Definizione conversione valuta (configurazione guidata Business Intelligence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.existingscriptpage.f1
ms.assetid: 37dd65b7-9d8d-44ad-b316-96a92c622472
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ce1916bd988d23dfd33f689f189436a50408a207
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159512"
---
# <a name="define-currency-conversion-business-intelligence-wizard"></a>Definizione conversione valuta (Configurazione guidata funzionalità di Business Intelligence)
  Usare la pagina **Definizione conversione valuta** per esaminare lo script MDX (Multidimensional Expressions) contenente la funzionalità di conversione valuta generata dalla Configurazione guidata funzionalità di Business Intelligence. Sarà quindi possibile sovrascrivere la funzionalità di conversione valuta precedentemente definita nello script MDX del cubo con lo script MDX generato dalla procedura guidata o accodare il nuovo script a quello esistente.  
  
> [!NOTE]  
>  Questa pagina verrà visualizzata solo se la Configurazione guidata funzionalità di Business Intelligence rileva almeno una conversione valuta precedentemente definita nello script MDX per il cubo. Nello script MDX per un cubo, le conversioni valuta sono racchiuse tra i commenti seguenti:  
>   
>  `//<Currency conversion>`  
>   
>  `...`  
>   
>  `[MDX statements for the currency conversion]`  
>   
>  `...`  
>   
>  `//</Currency conversion>`  
>   
>  Se questi commenti vengono modificati o eliminati, la Configurazione guidata funzionalità di Business Intelligence può non essere in grado di rilevare le conversioni valuta precedentemente definite.  
  
## <a name="options"></a>Opzioni  
 **Nuovo script di conversione valuta**  
 Consente di visualizzare lo script MDX generato dalla sessione corrente della Configurazione guidata funzionalità di Business Intelligence.  
  
 **Sovrascrivi script di conversione valuta esistente**  
 Selezionare questa opzione per sovrascrivere lo script MDX visualizzato in **Script di conversione valuta esistente** con lo script MDX visualizzato in **Nuovo script di conversione valuta**.  
  
 **Accoda dopo**  
 Selezionare questa opzione per accodare lo script MDX visualizzato in **Nuovo script di conversione valuta** alla fine dello script MDX visualizzato in **Script di conversione valuta esistente**. Lo script accodato viene visualizzato come nuova sezione.  
  
 **Script di conversione valuta esistente**  
 Consente di selezionare la sezione dello script MDX esistente che contiene la funzionalità di conversione valuta precedentemente definita da sovrascrivere o a cui accodare il nuovo script.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida F1 di Business Intelligence guidata](business-intelligence-wizard-f1-help.md)   
 [Finestra di progettazione del cubo &#40;Analysis Services - dati multidimensionali&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Finestra di progettazione della dimensione &#40;Analysis Services - dati multidimensionali&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
