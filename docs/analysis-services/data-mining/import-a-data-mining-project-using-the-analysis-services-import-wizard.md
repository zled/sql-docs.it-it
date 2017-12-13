---
title: Importare un progetto di Data Mining utilizzando l'importazione guidata di Analysis Services | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62bc9fc5-c6ff-4517-b598-d92df76743a2
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b90ffa3645d844d066542e0c2cd8ac7e6999250d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="import-a-data-mining-project-using-the-analysis-services-import-wizard"></a>Importare un progetto di data mining utilizzando l'Importazione guidata di Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]In questo argomento viene descritto come creare un nuovo progetto di data mining importando i metadati da un progetto di data mining esistente in un altro server, utilizzando il modello, **Importa da Server (multidimensionale e Data Mining)**, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="import-data-sources-mining-structures-and-mining-models-from-an-existing-data-mining-project"></a>Importare origini dati, strutture e modelli di data mining da un progetto di data mining esistente  
 Quando si usa il modello **Importa da server (multidimensionale e data mining)**, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] viene creato un nuovo progetto di data mining, quindi vengono copiati i metadati dal progetto di data mining specificato. Il nuovo progetto contiene le stesse origini dati, viste origine dati, strutture e modelli di data mining del database di ssASnoversion da cui è stata effettuata l'importazione. Tuttavia, non è possibile utilizzare il progetto finché non sono state aggiornate alcune proprietà e non sono stati elaborati gli oggetti come descritto:  
  
-   I dati stessi non vengono copiati dal server di origine nel nuovo progetto di data mining, vengono importate solo le definizioni delle origini dati e le viste origine dati. Pertanto, al completamento del processo di importazione e dopo la creazione degli oggetti, è necessario popolare gli oggetti con i dati eseguendo il training delle strutture di data mining e dei modelli dipendenti. Per eseguire il training dei modelli e delle strutture, è possibile utilizzare il comando **Elabora tutto** di Progettazione modelli di data mining.  
  
-   Se si importa un progetto creato in una versione precedente di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], l'origine dati potrebbe utilizzare provider che non sono installati nel server nel quale si importa il progetto. Se si riscontrano errori durante l'elaborazione delle strutture di data mining importate, fare clic con il pulsante destro del mouse su ogni origine dati e selezionare **Apri finestra di progettazione** per modificare la stringa di connessione e rivedere le proprietà del provider.  
  
     Potrebbe inoltre essere necessario verificare che l'account utilizzato per elaborare gli oggetti di data mining o i modelli di data mining di query disponga delle autorizzazioni necessarie sull'origine dati.  
  
-   Per impostazione predefinita, quando si importa un progetto, il database dell'area di lavoro viene impostato su localhost o qualsiasi istanza predefinita configurata come **Server di destinazione predefinito** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Per impostare questa proprietà, scegliere **Finestre di progettazione Business Intelligence** dal menu **Opzioni**, selezionare **Analysis Services**, quindi **Generale**.  
  
     Si noti che in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]è disponibile un'altra opzione separata che è possibile impostare per configurare il server di distribuzione predefinito per i progetti di modello tabulare di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . L'impostazione **Server di distribuzione predefinito**determina il database dell'area di lavoro predefinito per i progetti di modello tabulare. Non è possibile utilizzare istanze che supportano i modelli tabulari per i progetti di data mining  
  
     Se non è possibile modificare il database di distribuzione predefinito per utilizzare un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in esecuzione in modalità multidimensionale o di data mining, è sempre possibile specificare il database di distribuzione tramite la finestra di dialogo **Proprietà progetto** .  
  
#### <a name="to-create-a-new-data-mining-project-by-importing-an-existing-data-mining-project"></a>Per creare un nuovo progetto di data mining importando un progetto di data mining esistente  
  
1.  In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2.  In **Modelli installati** nella finestra di dialogo **Nuovo progetto**fare clic su **Business Intelligence**, fare clic su **Analysis Services**e quindi su **Importa da server (multidimensionale e data mining)**.  
  
3.  In **Nome**digitare un nome per il progetto, quindi specificare un percorso e un nome per la soluzione e scegliere **OK**.  
  
     Verrà avviata l' **Importazione guidata database di Analysis Services** . Fare clic su OK nella pagina introduttiva per continuare.  
  
4.  Nella pagina **Seleziona database di origine**per **Server**specificare l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] che contiene la soluzione da importare.  
  
     Per **Database**scegliere il database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contenente i dati e gli oggetti di data mining da importare.  
  
    > [!WARNING]  
    >  Non è possibile specificare gli oggetti da importare; quando si sceglie un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esistente, vengono importati tutti gli oggetti multidimensionali e di data mining.  
  
     Scegliere **Avanti**.  
  
5.  Nella pagina **Completamento procedura guidata**viene visualizzato lo stato di avanzamento dell'operazione di importazione. Non è possibile annullare l'operazione o modificare gli oggetti importati. Fare clic su **Fine** al termine.  
  
     Il nuovo progetto viene aperto automaticamente tramite [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà del progetto &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/project-properties-ssas-tabular.md)  
  
  
