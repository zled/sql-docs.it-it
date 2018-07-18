---
title: "Lezione dell'esercitazione di Analysis Services 1: creare un nuovo progetto di modello tabulare | Documenti Microsoft"
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 403e6d04d339e3126afe964bd919304d04295c0b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="create-a-tabular-model-project"></a>Creare un progetto di modello tabulare

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione, utilizzare Visual Studio con SQL Server Data Tools (SSDT) o Visual Studio 2017, con estensione VSIX progetti di Microsoft Analysis Services per creare un nuovo progetto di modello tabulare a livello di compatibilità 1400. Una volta creato il nuovo progetto, è possibile iniziare l'aggiunta di dati e creazione del modello. In questa lezione offre inoltre una breve introduzione al modello tabulare di creazione ambiente Visual Studio.  
  
Tempo stimato per il completamento della lezione: **10 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti

Questo articolo è la prima lezione di un'esercitazione sulla creazione di modelli tabulari. Per completare questa lezione, esistono diversi prerequisiti, che è necessario che sul posto. Per ulteriori informazioni, vedere [Analysis Services - esercitazione Adventure Works](../tutorial-tabular-1400/as-adventure-works-tutorial.md).  
  
## <a name="create-a-new-tabular-model-project"></a>Creare un nuovo modello di progetto tabulare  
  
#### <a name="to-create-a-new-tabular-model-project"></a>Per creare un nuovo modello di progetto tabulare  
  
1.  In Visual Studio, sul **File** menu, fare clic su **New** > **progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere **installato** > **Business Intelligence** > **Analysis Services**, quindi fare clic su **progetto tabulare di Analysis Services**.  
  
3.  In **nome**, tipo **AW Internet Sales**e quindi specificare un percorso per i file di progetto.  
  
    Per impostazione predefinita, **Nome soluzione** corrisponde al nome del progetto; tuttavia, è possibile digitare un nome diverso per la soluzione.  
  
4.  Scegliere **OK**.  
  
5.  Nel **progettazione di modelli tabulari** nella finestra di dialogo **integrato dell'area di lavoro**.  
  
    L'area di lavoro viene ospitato un database modello tabulare con lo stesso nome del progetto durante la creazione di modelli. Area di lavoro integrata significa che Visual Studio utilizza un'istanza predefinita, eliminando la necessità di installare un'istanza del server Analysis Services separata solo per la creazione di modelli.
      
6.  In **livello di compatibilità**selezionare **SQL Server 2017 / Azure Analysis Services (1400)**.   
 
    ![as-lesson1-tmd](../tutorial-tabular-1400/media/as-lesson1-tmd.png)
      
    Se SQL Server 2017 / Azure Analysis Services (1400) nella casella di riepilogo livello compatibilità non è visualizzato, non si utilizza la versione più recente di SQL Server Data Tools. Per ottenere l'ultima versione, vedere [Installare SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).  
      
  
## <a name="understanding-the-ssdt-tabular-model-authoring-environment"></a>Comprendere l'ambiente di creazione di modelli tabulari SSDT  

Dopo aver creato un nuovo progetto di modello tabulare, è opportuno per esplorare il modello tabulare creazione ambiente Visual Studio.  
  
Dopo aver creato il progetto, viene aperto in Visual Studio. Sul lato destro, in **Esplora modelli tabulari**, vedrai una visualizzazione albero degli oggetti nel modello. Poiché non sono stati ancora importati i dati, le cartelle vengono. Fare doppio clic su una cartella di oggetti per eseguire azioni, simile alla barra dei menu. Mentre si esamina questa esercitazione, utilizzare Esplora modelli tabulari per esplorare i diversi oggetti nel progetto di modello.

![as-lesson1-tme](../tutorial-tabular-1400/media/as-lesson1-tme.png)

Fare clic su di **Esplora** scheda. In questo caso, viene visualizzato il **Model.bim** file. Se non viene visualizzata la finestra di progettazione a sinistra (la finestra vuota con la scheda Model.bim), nel **Esplora**in **progetto AW Internet Sales**, fare doppio clic su di **Model.bim** file. Il file Model.bim contiene i metadati per il progetto di modello. 

![as-lesson1-se](../tutorial-tabular-1400/media/as-lesson1-se.png)
  
Scegliere **Model.bim**. Nel **proprietà** , visualizzare le proprietà del modello, più importante delle quali è il **modalità DirectQuery** proprietà. Questa proprietà specifica se il modello viene distribuito in modalità In-Memory (disattivata) o in modalità DirectQuery (attivata). Per questa esercitazione, si creano e distribuire il modello in modalità In memoria.

![as-lesson1-properties](../tutorial-tabular-1400/media/as-lesson1-properties.png)
  
Quando si crea un progetto di modello, determinate proprietà del modello vengono impostate automaticamente sulla base delle impostazioni di modellazione dati che possono essere specificate nel **strumenti** menu > **opzioni** la finestra di dialogo. Le proprietà Backup dei dati, Memorizzazione area di lavoro e Server dell'area di lavoro consentono di specificare la modalità e la posizione per il backup, la conservazione in memoria e la compilazione del database dell'area di lavoro, ovvero il database di creazione di modelli. È possibile modificare queste impostazioni successivamente, se necessario, ma per ora, lasciare queste proprietà, così come sono.  

In **Esplora**, fare doppio clic su **AW Internet Sales** (progetto), quindi fare clic su **proprietà**. Il **pagine delle proprietà di AW Internet Sales** viene visualizzata la finestra di dialogo. Impostare alcune di queste proprietà in un secondo momento quando si distribuisce il modello.  
  
Durante l'installazione di SSDT, nuove voci di menu sono stati aggiunti all'ambiente di Visual Studio. Fare clic su di **modello** menu. Da qui è possibile importare i dati, aggiornare i dati dell'area di lavoro, esplorare il modello in Excel, creare prospettive e ruoli, selezionare la vista del modello e impostare le opzioni di calcolo. Fare clic su di **tabella** menu. Da qui, è possibile creare e gestire relazioni, specificare impostazioni tabella data, creare partizioni e modificare le proprietà di tabella. Se si sceglie il **colonna** menu, è possibile aggiungere ed eliminare colonne in una tabella, bloccare le colonne e specificare l'ordinamento. SSDT aggiunge anche alcuni pulsanti alla barra. Più utile è la funzionalità Somma automatica per creare una misura di aggregazione standard per una colonna selezionata. Gli altri pulsanti della barra degli strumenti forniscono accesso rapido a funzionalità e comandi utilizzati di frequente.  
  
Esplorare alcune delle finestre di dialogo e posizioni per diverse funzionalità specifiche della creazione di modelli tabulari. Mentre alcuni elementi non sono ancora attivi, è possibile ottenere una buona idea dell'ambiente di creazione di modelli tabulari.  
  

## <a name="whats-next"></a>Quali sono le operazioni successive?

[Lezione 2: Ottenere dati](../tutorial-tabular-1400/as-lesson-2-get-data.md).

  
  
  
