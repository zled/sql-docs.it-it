---
title: Descrizione dettagliata del diagramma rete dipendenza (Data Mining Add-ins) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visio shapes, dependency network
- shapes, data mining
- shapes, network
- dependencies
- diagram, dependency network
- data mining layout toolbar
- dependency network
ms.assetid: aac732a8-5262-4649-b7d7-3ccf6f9cfa8b
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 855c66124c5084e58432f605d38a4cbb53832c74
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069519"
---
# <a name="dependency-network-diagram-walkthrough-data-mining-add-ins"></a>Descrizione dettagliata del diagramma della rete di dipendenze (componenti aggiuntivi Data mining)
  In vari tipi differenti di modelli di data mining viene utilizzato un grafico della rete come modalità di esplorazione delle relazioni nei dati. È possibile importare questi modelli in Visio utilizzando la **rete di dipendenze** il data shaping e quindi continuare a personalizzare e migliorare il layout. Il **forme di Data Mining per Visio** includono i seguenti controlli personalizzati per l'utilizzo di diagrammi di rete di dipendenze:  
  
-   Controlli di rendering per il grafico della rete  
  
     Queste opzioni fanno parte della procedura guidata che viene avviata quando si rilascia una forma nell'area di lavoro di Visio.  
  
-   **Layout Data Mining** sulla barra degli strumenti  
  
     Queste opzioni vengono aggiunte all'area di lavoro di Visio per consentire di interagire con il grafico della rete di dipendenze.  
  
## <a name="build-a-dependency-network-graph"></a>Compilazione di un grafico della rete di dipendenze  
 Si rilascia una forma nella pagina di Visio per avviare il **procedura guidata forma di Visio Net dipendenza** e impostare le opzioni del diagramma.  
  
#### <a name="use-the-dependency-net-visio-shape-wizard"></a>Utilizzo della Procedura guidata Forma di Visio per rete di dipendenze  
  
1.  Se non viene visualizzato **forme Microsoft Data Mining** nel **forme** elenco, fare clic su **più forme**, selezionare **Apri Stencil**e aprire la modello dal percorso di installazione predefinito.  
  
     \<unità >: \Programmi file (x85) \Microsoft SQL Server 2012 DM Add-Ins  
  
2.  Trascinare il **rete di dipendenze** forma nella pagina per avviare la procedura guidata. Scegliere **Avanti**.  
  
3.  Nella pagina iniziale del **procedura guidata forma di Visio rete di dipendenze**, fare clic su **successivo**.  
  
4.  Nel **selezionare un'origine dati** pagina del **procedura guidata forma di Visio rete di dipendenze**, scegliere una connessione a un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server che contiene il modello da visualizzare.  
  
5.  Selezionare un modello di data mining appropriato e fare clic su **successivo**.  
  
     Per selezionare un modello appropriato, è possibile esaminare il nome, descrizione, le colonne e tipo di dati di **proprietà** riquadro.  
  
     Questa forma supporta modelli creati tramite questi algoritmi:  
  
    -   Naive Bayes  
  
    -   Decision Trees  
  
    -   Regole di associazione  
  
6.  Nella pagina **selezione nodi per il rendering**, personalizzare le dimensioni del grafico e facoltativamente il filtro per includere solo determinati nodi.  
  
     Con un set di dati di grandi dimensioni, un grafico delle dipendenze può diventare enorme e contenere molti oggetti correlati, rappresentati come *nodi*. Tramite questa finestra di dialogo, è possibile creare un grafico della rete personalizzato in cui sono inclusi solo i nodi di interesse.  
  
     [segnaposto immagine]  
  
     **Numero di nodi da recuperare**  
     Se nel modello sono contenuti meno nodi rispetto al numero specificato, questa impostazione non avrà effetto. Se nel modello sono contenuti più nodi rispetto al numero specificato, verranno visualizzati solo i nodi più attendibili.  
  
     **Il nome contiene**  
     Lasciare vuota questa casella e fare clic sulla freccia verde per recuperare tutti i nodi del modello.  
  
     In alternativa, digitare una stringa e fare clic sulla freccia verde per restituire solo i nodi contenenti la stringa specificata.  
  
     La maggior parte dei modelli che è possibile creare con i dati di esempio non è grande, pertanto per questo esempio, aumentare il numero di nodi a 10, quindi fare clic sulla freccia verde per eseguire una query e ottenere un elenco di tutti i nodi.  
  
7.  Fare clic su **avanzate** per impostare le opzioni di ombreggiatura e forma per il grafico.  
  
8.  Fare clic su **Close** per uscire dall'installazione di **avanzate** finestra di dialogo Opzioni e quindi fare clic su **fine** per creare il grafico.  
  
## <a name="explore-and-modify-the-finished-diagram"></a>Esplorazione e modifica del diagramma completato  
 Dopo aver creato in Visio il grafico della rete di dipendenze, è possibile continuare a modificare e migliorare il grafico utilizzando le funzionalità di Visio.  
  
 Nel grafico seguente viene mostrato il layout predefinito di un grafico della rete di dipendenze.  
  
 [segnaposto immagine]  
  
1.  Utilizzare la **panoramica e Zoom** , controllare il **riquadro** area di Visio **visualizzazione** della barra multifunzione, per concentrarsi su una sezione del grafico e spostarsi nel diagramma.  
  
2.  Provare varie combinazioni di layout del grafico differenti di Visio **nuovo Layout pagina** opzione.  
  
3.  Fare clic sui **Add-Ins** della barra multifunzione e quindi visualizzata una delle barre degli strumenti personalizzate utilizzate per l'utilizzo di diagrammi di data mining:  
  
     **Layout**  
     Consente di ottimizzare il layout dei nodi nella pagina, nonché di modificare la visualizzazione in modo da includere tutti i nodi.  
  
     **Ridimensiona pagina**  
     Consente di modificare le dimensioni della pagina in modo da visualizzare tutti i nodi.  
  
     **Livello attendibilità bordo**  
     Consente di attivare e disattivare la visualizzazione del livello di attendibilità bordo per l'intero grafico. Un bordo è un collegamento tra nodi. È possibile utilizzare il controllo dispositivo di scorrimento per escludere tramite filtro i collegamenti non attendibili.  
  
     **Dispositivo di scorrimento**  
     Il **dispositivo di scorrimento** consente di controllare il livello di attendibilità delle relazioni che vengono visualizzati nel diagramma di rete di dipendenze.  
  
     Ogni nodo del grafico rappresenta uno stato. Una freccia rappresenta una transizione tra due stati e la probabilità associata alla transizione. Per ridurre il numero di nodi nel grafico, spostare il dispositivo di scorrimento verso l'alto.  
  
     Per aumentare il numero di nodi del grafico, spostare il dispositivo di scorrimento verso il basso.  
  
     **Aggiungere elementi**  
     Apre il **selezione nodi per il rendering** della finestra di dialogo in cui è possibile selezionare nuovi nodi da aggiungere al grafico.  
  
4.  È possibile rendere i grafici semplici o elaborati come desiderato e aggiungere annotazioni, rimanendo connessi al modello.  
  
     [segnaposto immagine]  
  
> [!WARNING]  
>  L'evidenziazione di nodi dipendenti e altre opzioni del menu di scelta rapida disponibili nelle versioni precedenti dei componenti aggiuntivi non funzionano in Office 2013.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi di diagrammi di Visio Data Mining &#40;componenti aggiuntivi Data Mining di dati SQL Server&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  