---
title: "Proprietà (SSAS tabulare) del modello | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.wspacedbconfig.f1
- sql13.asvs.bidtoolset.fileprop.f1
ms.assetid: 8ab04656-75a5-485c-9687-7b1ca49f7f80
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e0d09f3f0bd09017c73579d3f8b04b27e91cabfb
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="model-properties-ssas-tabular"></a>Proprietà modello (SSAS tabulare)
  In questo argomento vengono descritte le proprietà dei modelli tabulari. Ogni progetto di modello tabulare ha proprietà del modello che influiscono su come viene eseguito il backup e su come viene compilato il modello durante la creazione in Strumenti di sviluppo di SQL Server, nonché su come viene archiviato il database dell'area di lavoro. Le proprietà del modello descritte in questo argomento non vengono applicate ai modelli che sono già stati distribuiti.  
  
 Sezioni dell'argomento:  
  
-   [Proprietà dei modelli](#bkmk_model_properties)  
  
-   [Configurare le impostazioni delle proprietà dei modelli](#bkmk_conf_model_prop)  
  
##  <a name="bkmk_model_properties"></a> Proprietà dei modelli  
 **Avanzate**  
  
|Proprietà|Impostazione predefinita|Description|  
|--------------|---------------------|-----------------|  
|**Azione di compilazione**|Compila|Questa proprietà consente di specificare la modalità di correlazione del file al processo di compilazione e distribuzione. Per questa impostazione della proprietà sono disponibili le opzioni seguenti:<br /><br /> **Compila** : viene eseguita una normale azione di compilazione. Le definizioni per gli oggetti modello verranno scritte nel file con estensione asdatabase.<br /><br /> **Nessuna** : l'output nel file con estensione asdatabase sarà vuoto.|  
|**Copia nella directory di output**|Non copiare|Questa proprietà consente di specificare il file di origine che sarà copiato nella directory di output. Per questa impostazione della proprietà sono disponibili le opzioni seguenti:<br /><br /> **Non copiare** : non viene creata alcuna copia nella directory di output.<br /><br /> **Copia sempre** : viene sempre creata una copia nella directory di output.<br /><br /> **Copia se più recente** : viene creata una copia nella directory di output solo se sono state apportate modifiche al file model.bim.|  
  
 **Varie**  
  
> [!NOTE]  
>  Alcune proprietà vengono impostate automaticamente quando si crea il modello e non possono essere modificate.  
  
> [!NOTE]  
>  Le proprietà Server dell'area di lavoro, Memorizzazione area di lavoro e Backup dei dati dispongono di impostazioni predefinite applicate quando si crea un nuovo progetto di modello. È possibile modificare le impostazioni predefinite per nuovi modelli nella pagina Modellazione dati nelle impostazioni di Analysis Server in Strumenti\finestra di dialogo Opzioni. Queste proprietà, come altre, possono essere impostate anche per ogni modello nella finestra Proprietà. Per altre informazioni, vedere [Configurare la modellazione dei dati e le proprietà di distribuzione predefinite &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md).  
  
|Proprietà|Impostazione predefinita|Description|  
|--------------|---------------------|-----------------|  
|**Confronto**|Regole di confronto predefinite per il computer per il quale viene installato Visual Studio.|Designazione regole di confronto per il modello.|  
|**Livello di compatibilità**|Valore predefinito o di altro tipo selezionato in fase di creazione del progetto.|Si applica a SQL Server 2012 Analysis Services SP1 o versione successiva. Specifica le funzionalità e le impostazioni disponibili per il modello. Per informazioni dettagliate, vedere [Livello di compatibilità per i modelli tabulari in Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).|  
|**Backup dei dati**|Non eseguire il backup su disco|Viene specificato se viene mantenuto o meno un backup dei dati del modello in un file di backup. Per questa impostazione della proprietà sono disponibili le opzioni seguenti:<br /><br /> **Esegui il backup su disco** : viene specificato di mantenere un backup dei dati del modello su disco. Quando il modello viene salvato, anche i dati vengono salvati nel file (ABF) di backup. La selezione di questa opzione può comportare tempi di caricamento e salvataggio del modello più lenti.<br /><br /> **Non eseguire il backup su disco** : viene specificato di non mantenere un backup dei dati del modello su disco. Questa opzione consentirà di ridurre i tempi di salvataggio e caricamento del modello.<br /><br /> <br /><br /> L'impostazione predefinita per questa proprietà può essere modificata nella pagina Modellazione dati nelle impostazioni di Analysis Server in Strumenti\finestra di dialogo Opzioni.| 
|**Direzione del filtro predefinito**|Direzione singola|Determina la direzione del filtro predefinito per le nuove relazioni.| 
|**Modalità DirectQuery**|Disattivato|Viene specificato se questo modello funziona nella modalità DirectQuery. Per altre informazioni, vedere [Modalità DirectQuery &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md).|  
|**Nome file**|Model.bim|Viene specificato il nome del file con estensione bim. È consigliabile non modificare il nome del file.|  
|**Percorso completo**|Percorso specificato durante la creazione del progetto.|Percorso del file model.bim. Questa proprietà non può essere impostata nella finestra Proprietà.|  
|**Lingua**|Inglese|Lingua predefinita del modello. La lingua predefinita è determinata dalla lingua di Visual Studio. Questa proprietà non può essere impostata nella finestra Proprietà.|  
|**Database dell'area di lavoro**|Nome del progetto, seguito da una carattere di sottolineatura e da un GUID.|Nome del database dell'area di lavoro utilizzato per l'archiviazione e la modifica del modello in memoria per il file model.bim selezionato. Questo database verrà visualizzato nell'istanza di Analysis Services specificata nella proprietà Workspace Server. Questa proprietà non può essere impostata nella finestra Proprietà. Per altre informazioni, vedere [Database dell'area di lavoro &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/workspace-database-ssas-tabular.md).|  
|**Memorizzazione area di lavoro**|Scarica dalla memoria|Viene specificato come viene mantenuto un database dell'area di lavoro dopo la chiusura di un modello. In un database dell'area di lavoro sono inclusi i metadati del modello, i dati importati in un modello e le credenziali di rappresentazione (crittografate). In alcuni casi, le dimensioni del database dell'area di lavoro possono essere elevate e occupare quindi una quantità notevole di memoria. Per impostazione predefinita, i database dell'area di lavoro vengono scaricati dalla memoria. Quando si modifica questa impostazione, è importante considerare le risorse di memoria disponibili nonché pianificare la frequenza con la quale utilizzare il modello. Per questa impostazione della proprietà sono disponibili le opzioni seguenti:<br /><br /> **Mantieni in memoria** : viene specificato di mantenere il database dell'area di lavoro in memoria dopo la chiusura di un modello. Questa opzione utilizza una maggior quantità di memoria, tuttavia, quando si apre un modello, vengono utilizzate meno risorse e il database dell'area di lavoro viene caricato più velocemente.<br /><br /> **Scarica dalla memoria** : viene specificato di mantenere il database dell'area di lavoro su disco, ma non più in memoria dopo la chiusura di un modello. Questa opzione utilizza una minor quantità di memoria, tuttavia, quando si apre un modello, vengono utilizzate ulteriori risorse e il caricamento del modello risulta più lento rispetto a quando il database dell'area di lavoro viene mantenuto in memoria. Utilizzare questa opzione quando le risorse in memoria sono limitate o quando in uso in un database dell'area di lavoro remoto.<br /><br /> **Elimina area di lavoro** : viene specificato di eliminare il database dell'area di lavoro dalla memoria e di non mantenerlo su disco dopo la chiusura del modello. Questa opzione utilizza una minor quantità di memoria e di spazio di archiviazione, tuttavia, quando si apre un modello, vengono utilizzate ulteriori risorse e il caricamento del modello risulta più lento rispetto a quando il database dell'area di lavoro viene mantenuto in memoria o su disco. Utilizzare questa opzione quando i modelli vengono utilizzati solo occasionalmente.<br /><br /> <br /><br /> L'impostazione predefinita per questa proprietà può essere modificata nella pagina Modellazione dati nelle impostazioni di Analysis Server in Strumenti\finestra di dialogo Opzioni.|  
|**Server dell'area di lavoro**|localhost|Questa proprietà specifica il server predefinito usato per ospitare il database dell'area di lavoro mentre si crea il modello. Tutte le istanze disponibili di Analysis Services in esecuzione sul computer locale sono incluse nella casella di riepilogo.<br /><br /> L'impostazione predefinita per questa proprietà può essere modificata nella pagina Modellazione dati nelle impostazioni di Analysis Server in Strumenti\finestra di dialogo Opzioni.<br /><br /> <br /><br /> Nota: si consiglia di specificare sempre un server Analysis Services locale come server dell'area di lavoro. Per i database dell'area di lavoro in un server remoto, l'importazione da [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] non è supportata, il backup dei dati non può essere eseguito in locale e l'interfaccia utente può essere soggetta a latenza durante le query.|  
  
##  <a name="bkmk_conf_model_prop"></a> Configurare le impostazioni delle proprietà dei modelli  
  
1.  In **Esplora soluzioni**di SSDT fare clic sul file **Model.bim** .  
  
2.  Nella finestra **Proprietà** fare clic su una proprietà, quindi digitare un valore o fare clic sulla freccia GIÙ per selezionare un'opzione di impostazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare la modellazione dei dati e le proprietà di distribuzione predefinite &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)   
 [Proprietà del progetto &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/project-properties-ssas-tabular.md)  
  
  

