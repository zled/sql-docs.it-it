---
title: Utilizzare diagrammi in Progettazione origine dati (Analysis Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.dsvdesigner.findtable.f1
- sql13.asvs.dsvdesigner.diagramorganizerpane.f1
- sql13.asvs.dsvdesigner.diagrampane.f1
helpviewer_keywords:
- data source views [Analysis Services], diagrams
- diagrams [Analysis Services]
ms.assetid: 491fdd22-2326-4f27-a0dd-0a02faae3fd8
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b3e877f63972f6a891f788a65196d2ec621cc203
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="work-with-diagrams-in-data-source-view-designer-analysis-services"></a>Utilizzare diagrammi in Progettazione vista origine dati (Analysis Services)
  Un diagramma vista origine dati è una rappresentazione visiva degli oggetti contenuti in tale vista. È possibile utilizzare il diagramma in modo interattivo per aggiungere, nascondere, eliminare o modificare oggetti specifici. Inoltre, è possibile creare più diagrammi nella stessa vista origine dati per concentrare l'attenzione su un subset degli oggetti.  
  
 Per modificare l'area del diagramma visualizzata nel riquadro, fare clic sulla freccia a quattro punte nell'angolo inferiore destro del riquadro e quindi trascinare la casella di selezione sul diagramma di anteprima fino a selezionare l'area da visualizzare nel riquadro.  
  
 In questo argomento sono contenute le sezioni seguenti:  
  
 [Aggiungere un diagramma](#bkmk_add)  
  
 [Modificare o eliminare un diagramma](#bkmk_edit)  
  
 [Ricercare tabelle in un diagramma](#bkmk_findtables)  
  
 [Disporre oggetti in un diagramma](#bkmk_arrangeobjects)  
  
 [Mantenere la disposizione degli oggetti](#bkmk_preserve)  
  
##  <a name="bkmk_add"></a> Aggiungere un diagramma  
 I diagrammi delle viste origine dati vengono creati automaticamente durante la creazione di tale vista. Quando la vista origine dati è disponibile, è possibile creare diagrammi aggiuntivi, rimuoverli o nascondere oggetti specifici per generare una rappresentazione della vista origine dati più gestibile.  
  
 Per creare un nuovo diagramma, fare clic con il pulsante destro del mouse in qualsiasi punto del riquadro **Libreria diagrammi** e scegliere **Nuovo diagramma**.  
  
 Quando si definisce inizialmente una vista origine dati (DSV) in un progetto di Analysis Services, tutte le tabelle e le viste aggiunte alla vista origine dati vengono aggiunti per il \<tutte le tabelle > diagramma. Questo diagramma viene visualizzato nel riquadro Libreria diagrammi di Progettazione vista origine dati, mentre le tabelle di tale diagramma e le relative colonne e relazioni vengono elencate nel riquadro Tabelle e visualizzate graficamente nel riquadro degli schemi. Tuttavia, quando si aggiungere tabelle, viste e query denominate per il \<tutte le tabelle > diagramma, il numero degli oggetti nel diagramma rende difficile visualizzare le relazioni, vengono aggiunte al diagramma, in particolare come più tabelle dei fatti e delle dimensioni due tabelle sono correlate a più tabelle dei fatti.  
  
 Per semplificare la rappresentazione visiva quando si desidera visualizzare soltanto un subset delle tabelle della vista origine dati, è possibile definire diagrammi secondari, denominati semplicemente diagrammi, costituiti da subset selezionati delle tabelle, delle viste e delle query denominate della vista origine dati. È possibile utilizzare i diagrammi per raggruppare gli elementi nella vista origine dati in base alle esigenze aziendali o ai requisiti delle soluzioni.  
  
 È possibile raggruppare query denominate e tabelle correlate in diagrammi separati per scopi aziendali, nonché per rendere maggiormente comprensibile una vista origine dati contenente un numero elevato di tabelle e query denominate. La stessa tabella o query denominata può essere incluso in più diagrammi, ad eccezione del \<tutte le tabelle > diagramma. Nel \<tutte le tabelle > diagramma, tutti gli oggetti contenuti nella vista origine dati vengono visualizzati una sola volta.  
  
##  <a name="bkmk_edit"></a> Modificare o eliminare un diagramma  
 Quando si utilizza un diagramma, prestare molta attenzione ai comandi utilizzati per l'aggiunta e la rimozione di oggetti. Ad esempio, l'eliminazione di un oggetto da un diagramma ne comporterà l'eliminazione anche dalla vista origine dati. Se si desidera eliminare l'oggetto solo dal diagramma, usare invece **Nascondi tabella** .  
  
 ![Schermata dell'area di lavoro di diagramma, menu di scelta rapida](../../analysis-services/multidimensional-models/media/ssas-olapdsv-diagram.gif "schermata dell'area di lavoro di diagramma, menu di scelta rapida")  
  
 Sebbene sia possibile nascondere gli oggetti singolarmente, restituendoli utilizzando il comando Mostra tabelle correlate vengono restituiti anche tutti gli oggetti correlati al diagramma. Per controllare quali oggetti vengono restituiti all'area di lavoro, trascinarli invece dal riquadro Tabelle.  
  
##  <a name="bkmk_findtables"></a> Ricercare tabelle in un diagramma  
 Se le dimensioni dello schema sono elevate, potrebbe essere difficile scorrere fino a una tabella specifica nel riquadro **Diagramma** . Gli strumenti seguenti semplificano tuttavia la ricerca di una tabella in un diagramma.  
  
-   Scorrere l'elenco di tabelle nel riquadro **Tabelle** .  
  
     Per includere una tabella nel diagramma corrente, trascinare la tabella dal riquadro **Tabelle** a quello del diagramma.  
  
     Per allineare al centro la visualizzazione in una tabella già inclusa nel diagramma, selezionarla nel riquadro **Tabelle** .  
  
-   Indicatore di posizione delle tabelle nel riquadro **Diagramma** : l'indicatore di posizione delle tabelle è un'icona a forma di freccia a 4 punte che si trova all'intersezione tra le barre di scorrimento orizzontale e verticale nell'angolo inferiore destro del riquadro **Diagramma** . Consente di visualizzare un'anteprima del diagramma corrente nel riquadro Diagramma. È possibile utilizzare questa anteprima per modificare la visualizzazione nel riquadro Diagramma in base a qualsiasi posizione nel diagramma.  
  
-   Usare la finestra di dialogo **Trova tabella** : fare clic con il pulsante destro del mouse in un'area vuota del riquadro Diagramma e scegliere **Trova tabella**. In alternativa, fare clic sul comando **Trova tabella** sulla barra degli strumenti o nel menu **Vista origine dati** .  
  
     È possibile digitare stringhe e caratteri jolly nella casella Filtro per visualizzare subset delle tabelle presenti nel diagramma.  
  
##  <a name="bkmk_arrangeobjects"></a> Disporre oggetti in un diagramma  
 Sebbene in Progettazione vista origine dati sia possibile definire più diagrammi per rendere una vista origine dati maggiormente comprensibile, i diagrammi contenenti decine di tabelle possono risultare di difficile lettura e la riorganizzazione manuale dei layout delle tabelle potrebbe essere un'operazione laboriosa. In Progettazione vista origine dati, le tabelle del diagramma corrente possono essere riorganizzate automaticamente con un layout rettangolare o diagonale basato sulle relazioni tra tali tabelle.  
  
-   In un layout rettangolare, le linee di relazione vengono tracciate tra le tabelle anziché tra le colonne, in senso orizzontale e verticale.  
  
-   In un layout diagonale, le linee di relazione vengono tracciate nel modo più diretto possibile tra le colonne correlate delle tabelle. Una relazione tra più colonne viene collegata alla prima colonna correlata nella tabella. Se le colonne di una tabella non sono visibili, le linee vengono tracciate verso la parte superiore della tabella.  
  
##  <a name="bkmk_preserve"></a> Mantenere la disposizione degli oggetti  
 Dopo aver disposto manualmente le tabelle nel modo desiderato, l'aggiunta di più tabelle al diagramma può comportare un aggiornamento del diagramma che rimuove tutte le modifiche recenti apportate al layout dell'oggetto.  
  
 Questo comportamento si verifica con più probabilità quando si aggiunge una tabella, poiché causa lo spostamento di altre tabelle nella Libreria diagrammi per consentire l'inserimento di quella nuova. Il diagramma viene quindi ridisegnato per assicurare che tutte le tabelle e le linee di connessione siano rappresentate correttamente. A questo punto è possibile che tutte le modifiche manuali apportate alla posizione di oggetti specifici vadano perse.  
  
 Per evitare il problema, aggiungere tutte le tabelle prima di procedere alle modifiche finali. In tal modo gli oggetti dovrebbero mantenere la relativa posizione nel diagramma quando verrà riaperto.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste origine dati in modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Progettazione vista origine dati &#40; Analysis Services - dati multidimensionali &#41;](http://msdn.microsoft.com/library/6f40a074-761f-440b-a999-09b755bd86ce)  
  
  

