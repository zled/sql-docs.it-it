---
title: Aggiungendo o rimuovendo tabelle o viste in un tipo di dati di origine vista (Analysis Services) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: de75b3dfe13d5a640537f2bbc1a09b6c097687f9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022118"
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>Aggiunta o rimozione di tabelle o viste in una vista origine dati (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Dopo aver creato una vista origine dati in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], è possibile modificarla in Progettazione vista origine dati aggiungendo o rimuovendo tabelle e colonne, incluse quelle provenienti da un'altra origine dati.  
  
 Per aprire la vista origine dati in Progettazione vista origine dati, è necessario fare doppio clic sulla vista in Esplora soluzioni. Una volta aperta la vista origine dati, è possibile usare il comando **Aggiungi/Rimuovi tabelle** nella barra dei pulsanti o nel menu per modificare o estendere la vista origine dati. È possibile inoltre utilizzare gli oggetti nel diagramma. Ad esempio, è possibile selezionare un oggetto e utilizzare il tasto CANC sulla tastiera per rimuovere un oggetto.  
  
> [!WARNING]  
>  Prestare attenzione in caso di rimozione di una tabella. Se si rimuove una tabella vengono eliminate anche tutte le colonne e relazioni associate dalla vista origine dati e tutti gli oggetti associati a tale tabella non sono più validi.  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>Selezione delle tabelle o delle viste da aggiungere o rimuovere  
 Usando la finestra di dialogo **Aggiungi/Rimuovi tabelle** è possibile spostare tabelle o viste tra gli elenchi **Oggetti disponibili** e **Oggetti inclusi** . Nell'elenco **Oggetti disponibili** vengono incluse inizialmente tutte le tabelle o le viste dell'origine dei dati primaria che non sono già contenute nella vista origine dati. Se l'origine dati primaria supporta la funzione **OPENROWSET** , è anche possibile aggiungere tabelle o viste da altre origini dati nel progetto o nel database.  
  
 Se si aggiunge o si rimuove una tabella dalla vista origine dati, la tabella verrà aggiunta o rimossa anche dal diagramma corrente selezionato nella vista. Per altre informazioni sui diagrammi, vedere [Usare diagrammi in Progettazione vista origine dati &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md).  
  
 Dopo aver spostato una tabella nell'elenco **Oggetti inclusi** della finestra di dialogo **Aggiungi/Rimuovi tabelle** , è possibile aggiungere tutte le tabelle correlate. Questa operazione consente di aggiungere le tabelle nell'origine dei dati in base a vincoli di chiave esterna, se esistono. Se non esistono vincoli di chiave esterna, è possibile usare la proprietà **NameMatchingCriteria** della vista origine dati per determinare le relazioni specificando un criterio di corrispondenza per i nomi delle colonne nelle tabelle al fine di generare le relazioni probabili. Se è specificata la proprietà **NameMatchingCriteria**per la vista origine dati, fare clic su **Aggiungi tabelle correlate** per aggiungere le tabelle dell'origine dati con nomi di colonne corrispondenti. Per altre informazioni sull'impostazione della proprietà **NameMatchingCriteria** , vedere [Viste origine dati in modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
> [!NOTE]  
>  L'aggiunta o la rimozione di oggetti in una vista origine dati non influisce sull'origine dati sottostante.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste origine dati nei modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Utilizzare diagrammi in Progettazione vista origine dati & #40; Analysis Services & #41;](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
