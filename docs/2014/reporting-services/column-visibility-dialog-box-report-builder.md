---
title: Finestra di dialogo visibilità colonne (Generatore Report) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10127"
ms.assetid: 0c030cab-6087-45a5-99f0-c7bd693f20a1
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f6ab67682afc00057085fe3d0f793c51a28258d7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057765"
---
# <a name="column-visibility-dialog-box-report-builder"></a>Finestra di dialogo Visibilità colonne (Generatore report)
  Utilizzare la finestra di dialogo **Visibilità colonne** per visualizzare o nascondere la colonna selezionata quando il report viene eseguito per la prima volta oppure per utilizzare un altro elemento del report per attivare/disattivare la visibilità della colonna.  
  
## <a name="options"></a>Opzioni  
 **Quando il report viene eseguito inizialmente**  
 Selezionare un'opzione per indicare come deve essere visualizzato inizialmente l'elemento nel report.  
  
 **Mostra**  
 Selezionare questa opzione per indicare che la colonna deve essere visualizzata.  
  
 **Nascondi**  
 Selezionare questa opzione per indicare che la colonna deve essere nascosta.  
  
 **Mostra o Nascondi in base a un'espressione**  
 Selezionare questa opzione per modificare l'impostazione di visibilità iniziale tramite un'espressione.  
  
 Digitare un'espressione che restituisce un `Boolean` valore del `True` per nascondere l'elemento e `False` per visualizzare l'elemento. Fare clic sul pulsante Espressione (*fx*) per modificare l'espressione.  
  
 **Visualizzazione può essere attivata/disattivata tramite questo elemento del report**  
 Selezionare questa opzione per visualizzare l'immagine dell'elemento Toggle che consente all'utente di visualizzare o nascondere la colonna in un visualizzatore di report HTML.  
  
 Digitare o selezionare il nome di una casella di testo del report in cui visualizzare l'immagine dell'elemento Toggle, ad esempio Textbox1. La casella di testo selezionata deve trovarsi nell'ambito corrente o contenitore dell'elemento del report. Ad esempio, per attivare/disattivare la visibilità di righe associate a un gruppo figlio, selezionare una casella di testo in una riga associata al gruppo padre. Per attivare/disattivare la visibilità di un grafico, selezionare una casella di testo che si trovi nello stesso ambito contenitore del grafico, ad esempio il corpo del report o un rettangolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Aggiungere un'azione Espandi o Comprimi a un elemento &#40;Generatore report e SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [Immagini &#40;Report e SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [Guida di Generatore report per finestre di dialogo, riquadri e procedure guidate](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Finestra di dialogo Proprietà immagine, Generale &#40;Generatore report e SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
