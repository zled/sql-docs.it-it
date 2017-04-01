---
title: "Lezione 1: Creare un nuovo modello di progetto tabulare | Microsoft Docs"
ms.custom: ""
ms.date: "03/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 0d2eb34d-78c8-41ff-b92d-49b62c16b2ac
caps.latest.revision: 33
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 28
---
# Lezione 1: Creare un nuovo modello di progetto tabulare
In questa lezione verrà creato un nuovo progetto di modello tabulare in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Una volta creato il nuovo progetto, è possibile iniziare ad aggiungere dati tramite l'Importazione guidata tabella. Oltre alla creazione di un nuovo progetto, questa lezione include anche una breve introduzione all'ambiente di creazione di modelli tabulari in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
Per altre informazioni sui diversi tipi di progetti di modelli tabulari, vedere [Progetti di modello tabulare &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/tabular-model-projects-ssas-tabular.md). Per altre informazioni sull'ambiente di creazione di modelli tabulari, vedere [Progettazione di modelli tabulari &#40;SSAS&#41;](../analysis-services/tabular-models/tabular-model-designer-ssas.md).  
  
Tempo stimato per il completamento della lezione: **10 minuti**  
  
## Prerequisiti  
Questo argomento è la prima lezione di un'esercitazione sulla creazione di modelli tabulari. Per completare questa lezione, è necessario avere installato il database AdventureWorksDW in un'istanza di SQL Server. Per altre informazioni, vedere [Modellazione tabulare &#40;esercitazione di AdventureWorks&#41;](../analysis-services/tabular-modeling-adventure-works-tutorial.md).  
  
## Creare un nuovo modello di progetto tabulare  
  
#### Per creare un nuovo modello di progetto tabulare  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto**, in voce **Installato** fare clic su **Business Intelligence**, **Analysis Services** e **Progetto tabulare di Analysis Services**.  
  
3.  In **Nome** digitare **AW Internet Sales Tabular Model** e specificare un percorso per i file di progetto.  
  
    Per impostazione predefinita, **Nome soluzione** corrisponde al nome del progetto. È tuttavia possibile digitare un nome diverso per la soluzione.  
  
4.  Scegliere **OK**.  
  
5.  Nella finestra di dialogo **Progettazione modelli tabulari**, alla voce **Server dell'area di lavoro**, digitare il nome di un'istanza di Microsoft SQL Server 2016 Analysis Services in cui si hanno le autorizzazioni di amministratore del server e fare clic su **Test connessione**.  
  
    Nell'istanza del server dell'area di lavoro specificato sarà ospitato un database modello tabulare con lo stesso nome del progetto usato in fase di creazione.   
      
6.  In **Livello di compatibilità** verificare che **SQL Server 2016 (1200)** sia selezionato e fare clic su **OK**.   
      
    Se SQL Server 2016 (1200) non viene visualizzato nell'elenco dei livelli di compatibilità, significa che non si sta usando l'ultima versione di SQL Server Data Tools. Per ottenere l'ultima versione, vedere [Installare SQL Server Data Tools](https://msdn.microsoft.com/hh500335(v=vs.103).aspx).   
      
    È consigliabile selezionare un livello di compatibilità con una versione precedente solo se si vuole distribuire il modello tabulare in un'istanza diversa di Analysis Services che esegue SQL Server 2012 o SQL Server 2014. Per alte informazioni, vedere [Livello di compatibilità per i modelli tabulari in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).   
  
## Informazioni sull'ambiente di creazione di modelli tabulari per SQL Server Data Tools  
Dopo avere creato un nuovo progetto di modello tabulare, verrà analizzato l'ambiente di creazione di modelli tabulari in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (Visual Studio 2010 o versioni successive).  
  
Dopo essere stato creato, il progetto verrà visualizzato in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. In Progettazione modelli verrà visualizzato un modello vuoto e il file **Model.bim** verrà selezionato nella finestra **Esplora soluzioni**. Quando si aggiungono dati, nella finestra di progettazione vengono visualizzate tabelle e colonne. Se la finestra di progettazione, ovvero la finestra vuota con la scheda Model.bim, non viene visualizzata, in **Esplora soluzioni** fare doppio clic sul file **Model.bim** in **AW Internet Sales Tabular Model**.  
  
Nella finestra **Proprietà** è possibile visualizzare le proprietà di base del progetto. In **Esplora soluzioni** fare clic su **AW Internet Sales Tabular Model**. Si noti che nella finestra **Proprietà**, in **File di progetto**, viene visualizzato **AW Internet Sales Tabular Model.smproj**. Si tratta del nome del file di progetto, mentre in **Cartella di progetto** viene visualizzato il percorso specifico del file di progetto.  
  
In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **AW Internet Sales Tabular Model** e scegliere **Proprietà**. Verrà visualizzata la finestra di dialogo **Pagine delle proprietà di AW Internet Sales Tabular Model** (Pagine delle proprietà di AW Internet Sales Tabular Model). Si tratta delle proprietà avanzate del progetto. Più avanti, prima di distribuire il modello, verranno impostate alcune di queste proprietà.  
  
Verranno ora analizzate le proprietà del modello. In **Esplora soluzioni** fare clic su **Model.bim**. Nella finestra **Proprietà** verranno visualizzate le proprietà del modello, la più importante delle quali è la proprietà **Modalità DirectQuery**. Questa proprietà specifica se il modello verrà distribuito o meno nella modalità In-Memory (disattivata) o nella modalità DirectQuery (attivata). Per questa esercitazione il modello verrà creato e distribuito nella modalità In-Memory.  
  
Quando si crea un nuovo modello, determinate proprietà del modello vengono impostate automaticamente in base alle impostazioni di Modellazione dati che è possibile specificare nella finestra di dialogo Strumenti\Opzioni. Le proprietà Backup dei dati, Memorizzazione area di lavoro e Server dell'area di lavoro consentono di specificare la modalità e la posizione per il backup, la conservazione in memoria e la compilazione del database dell'area di lavoro, ovvero il database di creazione di modelli. Queste impostazioni possono essere modificate successivamente, ma per il momento è possibile lasciarle invariate.  
  
Con l'installazione di [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] vengono aggiunte nuove voci di menu all'ambiente di Visual Studio. Analizzare le nuove voci di menu specifiche della creazione di modelli tabulari. Fare clic sul menu **Modello**. Da questa posizione è possibile avviare l'Importazione guidata tabella, visualizzare e modificare le connessioni esistenti, aggiornare i dati dell'area di lavoro, esplorare il modello in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel utilizzando la funzionalità Analizza in Excel, creare prospettive e ruoli, selezionare la vista del modello e impostare opzioni di calcolo.  
  
Fare clic sul menu **Tabella**. Da questa posizione è possibile creare e gestire relazioni tra tabelle, creare, gestire e specificare impostazioni della tabella data, creare partizioni e modificare proprietà della tabella.  
  
Fare clic sul menu **Colonna**. Da questa posizione è possibile aggiungere ed eliminare colonne in una tabella, bloccare colonne e specificare un ordinamento. È inoltre possibile utilizzare la funzionalità Somma automatica per creare una misura di aggregazione standard per una colonna selezionata. Gli altri pulsanti della barra degli strumenti forniscono accesso rapido a funzionalità e comandi utilizzati di frequente.  
  
Esplorare alcune delle finestre di dialogo e posizioni per diverse funzionalità specifiche della creazione di modelli tabulari. Sebbene alcuni elementi non saranno ancora attivi, è possibile farsi una buona idea dell'ambiente di creazione di modelli tabulari.  
  
## Passaggi successivi  
Per continuare questa esercitazione, passare alla lezione successiva: [Lezione 2: Aggiungere dati](../analysis-services/lesson-2-add-data.md).  
  
  
  
