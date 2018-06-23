---
title: Impostazione chiave e tipo (Creazione guidata dimensione) | Documenti Microsoft
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
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1ce08115251beee6dc71509bc4d3a53420ecd678
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155852"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a>Impostazione chiave e tipo della dimensione (Creazione guidata dimensione)
  La pagina **Impostazione chiave e tipo della dimensione** consente di definire l'attributo chiave della dimensione e di indicare se si tratta di una dimensione a modifica lenta.  
  
> [!NOTE]  
>  Questa pagina viene visualizzata solo se si seleziona **Build the dimension without using a data source** (Compila dimensione senza usare un'origine dei dati) nella pagina **Select Build Method** (Selezione metodo di compilazione) e **Dimensione standard** nella pagina **Selezione tipo di dimensione** .  
  
## <a name="options"></a>Opzioni  
 **Attributo chiave**  
 Consente di selezionare l'attributo che costituirà l'attributo chiave per la dimensione.  
  
> [!NOTE]  
>  Se non sono stati definiti attributi per la dimensione, l'unico valore disponibile per questa opzione sarà **Creare automaticamente l'attributo chiave**. Questo valore non è disponibile se sono stati definiti attributi per la dimensione.  
  
 **Si tratta di una dimensione a modifica**  
 Selezionare questa opzione per indicare che si tratta di una dimensione a modifica lenta. Selezionando questa opzione vengono create colonne e attributi aggiuntivi che possono essere utilizzati per tenere traccia di tutti gli spostamenti dei membri tra le gerarchie della dimensione.  
  
## <a name="see-also"></a>Vedere anche  
 [F1 Guida della procedura guidata di dimensione](dimension-wizard-f1-help.md)   
 [Le dimensioni &#40;Analysis Services - dati multidimensionali&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensioni nei modelli multidimensionali](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  