---
title: 'Lezione 1: Creare un nuovo progetto di modello tabulare | Documenti Microsoft'
ms.custom: ''
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 0d2eb34d-78c8-41ff-b92d-49b62c16b2ac
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f0c3761c88fa38ceaa4258bd6576b986c6bc94fd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a>Lezione 1: Creare un nuovo modello di progetto tabulare
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In questa lezione verrà creato un nuovo progetto di modello tabulare in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Una volta creato il nuovo progetto, è possibile iniziare ad aggiungere dati tramite l'Importazione guidata tabella. In questa lezione offre inoltre una breve introduzione al modello tabulare in SSDT ambiente di creazione.  
  
Tempo stimato per il completamento della lezione: **10 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
Questo argomento è la prima lezione di un'esercitazione sulla creazione di modelli tabulari. Per completare questa lezione, è necessario disporre di database di esempio AdventureWorksDW installato in un'istanza di SQL Server. Per altre informazioni, vedere [modellazione tabulare &#40;esercitazione di AdventureWorks&#41;](../analysis-services/tabular-modeling-adventure-works-tutorial.md).  
  
## <a name="create-a-new-tabular-model-project"></a>Creare un nuovo modello di progetto tabulare  
  
#### <a name="to-create-a-new-tabular-model-project"></a>Per creare un nuovo modello di progetto tabulare  
  
1.  In SSDT nel **File** menu, fare clic su **New** > **progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere **installato** > **Business Intelligence** > **Analysis Services**, quindi fare clic su **progetto tabulare di Analysis Services**.  
  
3.  In **nome**, tipo **AW Internet Sales**e quindi specificare un percorso per i file di progetto.  
  
    Per impostazione predefinita, **Nome soluzione** corrisponde al nome del progetto. È tuttavia possibile digitare un nome diverso per la soluzione.  
  
4.  Scegliere **OK**.  
  
5.  Nel **progettazione di modelli tabulari** nella finestra di dialogo **integrato dell'area di lavoro**.  
  
    L'area di lavoro verrà ospitato un database modello tabulare con lo stesso nome del progetto durante la creazione di modelli. Area di lavoro integrata significa che SSDT verrà utilizzata un'istanza predefinita, eliminando la necessità di installare un'istanza del server Analysis Services separata solo per la creazione di modelli. Per ulteriori informazioni, vedere [Database area di lavoro](../analysis-services/tabular-models/workspace-database-ssas-tabular.md).
      
6.  In **Livello di compatibilità**verificare che **SQL Server 2016 (1200)** sia selezionato e fare clic su **OK**.   
 
    ![as-tabular-lesson1-tmd](../analysis-services/media/as-tabular-lesson1-tmd.png)
      
    Se non viene visualizzato SQL Server 2016 RTM (1200) nella casella di riepilogo livello compatibilità, non si utilizza la versione più recente di SQL Server Data Tools. Per ottenere l'ultima versione, vedere [Installare SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).  

    Se si utilizza la versione più recente di SSDT, è anche possibile scegliere SQL Server 2017 (1400). Tuttavia, per completare la lezione 13: la distribuzione, è necessario un server SQL Server 2017 o Azure per distribuire.
      
    Selezione di un livello di compatibilità precedenti è consigliabile solo se si intende distribuire il modello tabulare completato a un'altra istanza di Analysis Services in esecuzione una versione precedente di SQL Server. Area di lavoro integrata non è supportata per i livelli di compatibilità precedenti. Per alte informazioni, vedere [Livello di compatibilità per i modelli tabulari in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).   
  
## <a name="understanding-the-ssdt-tabular-model-authoring-environment"></a>Comprendere l'ambiente di creazione di modelli tabulari SSDT  
Dopo aver creato un nuovo progetto di modello tabulare, è opportuno per esplorare il modello tabulare in SSDT ambiente di creazione.  
  
Dopo aver creato il progetto, viene aperto in SSDT. Sul lato destro, in **Esplora modelli tabulari**, si noterà una visualizzazione albero degli oggetti nel modello. Poiché non sono stati ancora importati i dati, le cartelle sarà vuote. Fare doppio clic su una cartella di oggetti per eseguire azioni, simile alla barra dei menu. Mentre si esamina questa esercitazione, si userà Esplora modelli tabulari per esplorare i diversi oggetti nel progetto di modello.

![as-tabular-lesson1-tme](../analysis-services/media/as-tabular-lesson1-tme.png)

Fare clic su di **Esplora** scheda. In questo caso, verrà visualizzato il **Model.bim** file. Se non viene visualizzata la finestra di progettazione a sinistra (la finestra vuota con la scheda Model.bim), nel **Esplora**in **progetto AW Internet Sales**, fare doppio clic su di **Model.bim** file. Il file Model.bim contiene tutti i metadati per il progetto di modello. 

![as-tabular-lesson1-se](../analysis-services/media/as-tabular-lesson1-se.png)
  
Esaminiamo le proprietà del modello. Scegliere **Model.bim**. Nel **proprietà** finestra, verrà visualizzato il [proprietà del modello](../analysis-services/tabular-models/model-properties-ssas-tabular.md), più importante delle quali è il **modalità DirectQuery** proprietà. Questa proprietà specifica se il modello verrà distribuito o meno nella modalità In-Memory (disattivata) o nella modalità DirectQuery (attivata). Per questa esercitazione il modello verrà creato e distribuito nella modalità In-Memory.

![as-tabular-lesson1-properties](../analysis-services/media/as-tabular-lesson1-properties.png)
  
Quando si crea un nuovo modello, determinate proprietà del modello vengono impostate automaticamente sulla base delle impostazioni di modellazione dati che possono essere specificate nel **strumenti** > **opzioni** la finestra di dialogo. Le proprietà Backup dei dati, Memorizzazione area di lavoro e Server dell'area di lavoro consentono di specificare la modalità e la posizione per il backup, la conservazione in memoria e la compilazione del database dell'area di lavoro, ovvero il database di creazione di modelli. Queste impostazioni possono essere modificate successivamente, ma per il momento è possibile lasciarle invariate.  

In **Esplora**, fare doppio clic su **AW Internet Sales** (progetto), quindi fare clic su **proprietà**. Il **pagine delle proprietà di AW Internet Sales** viene visualizzata la finestra di dialogo. Si tratta di avanzate [le proprietà del progetto](../analysis-services/tabular-models/project-properties-ssas-tabular.md). Più avanti, prima di distribuire il modello, verranno impostate alcune di queste proprietà.  
  
Durante l'installazione di SSDT, nuove voci di menu sono stati aggiunti all'ambiente di Visual Studio. Diamo un'occhiata quelle specifiche per la creazione di modelli tabulari. Fare clic sul menu **Modello** . Da qui è possibile avviare l'importazione guidata tabella, visualizzare e modificare le connessioni esistenti, aggiornare i dati dell'area di lavoro, esplorare il modello in Excel con la funzionalità analizza in Excel, creare prospettive e ruoli, selezionare la vista del modello e impostare le opzioni di calcolo.  
  
Fare clic sul menu **Tabella** . Da questa posizione è possibile creare e gestire relazioni tra tabelle, creare, gestire e specificare impostazioni della tabella data, creare partizioni e modificare proprietà della tabella.  
  
Fare clic sul menu **Colonna** . Da questa posizione è possibile aggiungere ed eliminare colonne in una tabella, bloccare colonne e specificare un ordinamento. È inoltre possibile utilizzare la funzionalità Somma automatica per creare una misura di aggregazione standard per una colonna selezionata. Gli altri pulsanti della barra degli strumenti forniscono accesso rapido a funzionalità e comandi utilizzati di frequente.  
  
Esplorare alcune delle finestre di dialogo e posizioni per diverse funzionalità specifiche della creazione di modelli tabulari. Sebbene alcuni elementi non saranno ancora attivi, è possibile farsi una buona idea dell'ambiente di creazione di modelli tabulari.  


## <a name="additional-resources"></a>Risorse aggiuntive
Per ulteriori informazioni sui diversi tipi di progetti di modello tabulare, vedere [progetti di modello tabulare](../analysis-services/tabular-models/tabular-model-projects-ssas-tabular.md). Per ulteriori informazioni sull'ambiente di creazione di modelli tabulari, vedere [Progettazione modelli tabulari ](../analysis-services/tabular-models/tabular-model-designer-ssas.md).  
  

## <a name="whats-next"></a>Quali sono le operazioni successive?
Passare alla lezione successiva: [lezione 2: aggiungere dati](../analysis-services/lesson-2-add-data.md).

  
  
  
