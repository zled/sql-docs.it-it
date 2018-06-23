---
title: Le notifiche (finestra di dialogo Opzioni di archiviazione) (Analysis Services - dati multidimensionali) | Documenti Microsoft
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
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.setstorageoptions.notifications.f1
ms.assetid: 5675cdbf-bfaa-4b6e-b716-31b8e9da72b4
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5b7dd3df8058b8c223d7737e4510ec74795ba75f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065697"
---
# <a name="notifications-storage-options-dialog-box-analysis-services---multidimensional-data"></a>Notifiche (finestra di dialogo Opzioni di archiviazione) (Analysis Services - Dati multidimensionali)
  Usare la scheda **Notifiche** della finestra di dialogo **Opzioni di archiviazione** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] per impostare il metodo di notifica e le relative impostazioni per una dimensione, un cubo, un gruppo di misure o una partizione.  
  
> [!NOTE]  
>  Prima di modificare queste impostazioni, è consigliabile acquisire dimestichezza con la modalità di archiviazione e la funzionalità di memorizzazione nella cache attiva. Per altre informazioni, vedere [Memorizzazione nella cache attiva &#40;partizioni&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="options"></a>Opzioni  
  
|Nome|Definizione|  
|----------|----------------|  
|**Modalità di archiviazione**|Consente di selezionare la modalità di archiviazione da utilizzare per l'oggetto.<br /><br /> **MOLAP**<br /> L'oggetto utilizza l'archiviazione OLAP multidimensionale (MOLAP).<br /><br /> **HOLAP**<br /> L'oggetto utilizza l'archiviazione OLAP ibrido (HOLAP).<br /><br /> **ROLAP**<br /> L'oggetto utilizza l'archiviazione OLAP relazionale (ROLAP).|  
|**Abilitare la memorizzazione nella cache**|Attiva la memorizzazione nella cache attiva.<br /><br /> Nota: se questa opzione non è selezionata, tutte le opzioni ad eccezione di **Modalità di archiviazione** sono disabilitate.|  
|**SQL Server**|Consente di usare un meccanismo di traccia specializzato in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per identificare le modifiche apportate alle tabelle sottostanti per l'oggetto.|  
|**Specificare le tabelle di rilevamento**|Specificare le tabelle sottostanti da rilevare per l'oggetto, quindi digitare un elenco di tabelle delimitate da punto e virgola (;) oppure fare clic sul pulsante con i puntini di sospensione (**...**) per aprire la finestra di dialogo **Oggetti relazionali** e selezionare le tabelle da rilevare. Per altre informazioni, vedere [Finestra di dialogo Oggetti relazionali &#40;Analysis Services - Dati multidimensionali&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Se questa opzione non è selezionata [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] tenta di determinare l'elenco delle tabelle sottostanti da rilevare per l'oggetto se vengono soddisfatti determinati requisiti. Per altre informazioni su questi requisiti, vedere [Memorizzazione nella cache attiva &#40;partizioni&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|**Inizializzate sul lato client**|Selezionare questa opzione per utilizzare il codice XML per il comando Analysis (XMLA), `NotifyTableChange`, per identificare le modifiche apportate alle tabelle sottostanti per l'oggetto. Questa opzione viene in genere selezionata se si desidera utilizzare un processo di notifica basato sul client.|  
|**Specificare le tabelle di rilevamento**|Selezionare questa opzione per specificare le tabelle sottostanti da rilevare per l'oggetto, quindi digitare un elenco di tabelle delimitate da punto e virgola (;) oppure fare clic sul pulsante con i puntini di sospensione (**...**) per aprire la finestra di dialogo **Oggetti relazionali** e selezionare le tabelle da rilevare. Per altre informazioni, vedere [Finestra di dialogo Oggetti relazionali &#40;Analysis Services - Dati multidimensionali&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Se questa opzione non è selezionata [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] tenta di determinare l'elenco delle tabelle sottostanti da rilevare per l'oggetto se vengono soddisfatti determinati requisiti. Per altre informazioni su questi requisiti, vedere [Memorizzazione nella cache attiva &#40;partizioni&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|**Polling pianificato**|Consente di utilizzare un meccanismo di polling per identificare le modifiche eseguendo una serie di query sulle tabelle sottostanti per l'oggetto.|  
|**Intervallo di polling**|Consente di specificare l'intervallo e le unità di tempo per il periodo che deve intercorrere prima che [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] esegua le query di polling e le query di elaborazione definite nella griglia di polling.|  
|**Attiva aggiornamenti incrementali**|Consente di eseguire un aggiornamento incrementale della cache MOLAP per un oggetto in base a un set di query di polling e di elaborazione progettato per identificare solo i dati aggiuntivi. Se questa opzione è selezionata la query di polling è associata a un identificatore di tabella nella vista origine dati. La query di elaborazione viene quindi utilizzata per identificare le modifiche confrontando il valore corrente della query di polling e il valore archiviato della query eseguita precedentemente.<br /><br /> Se questa opzione non è selezionata la cache MOLAP viene aggiornata interamente. La query di polling viene utilizzata per rilevare che è stata apportata una modifica e non è necessario alcun identificatore di tabella o query di elaborazione.|  
|**Griglia di polling**|Contiene le query di polling, le query di elaborazione e gli identificatori di tabella usati da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per eseguire il polling dell'origine dei dati e identificare le modifiche apportate alle tabelle sottostanti per l'oggetto. La griglia include le colonne seguenti:<br /><br /> **Query di polling**: digitare la query singleton eseguita all'intervallo di polling per identificare le modifiche per l'oggetto oppure fare clic sul pulsante con puntini di sospensione (**...** ) per aprire la **crea Query di Polling** dialogo casella e definire la query singleton. Per altre informazioni, vedere [Finestra di dialogo Crea query di polling &#40;Analysis Services - Dati multidimensionali&#41;](create-polling-query-dialog-box-analysis-services-multidimensional-data.md). Se l'opzione **Abilita aggiornamenti incrementali** è selezionata, la query di polling deve restituire un valore che identifica l'ultimo record aggiunto alla tabella identificata nella colonna **Tabella**. Se l'opzione **Abilita aggiornamenti incrementali** non è selezionata, la query di polling deve restituire un valore che identifica il numero corrente di record nella tabella.<br /><br /> **Query di elaborazione**: digitare la query eseguita all'intervallo di polling per recuperare nuovi record dalla tabella identificata nella **tabella**, oppure fare clic sul pulsante con puntini di sospensione (**...** ) per aprire la **crea Query di elaborazione** dialogo casella e definire la query. Per altre informazioni, vedere [Finestra di dialogo Crea query di elaborazione &#40;Analysis Services - Dati multidimensionali&#41;](create-processing-query-dialog-box-analysis-services-multidimensional-data.md). La query deve essere impostata in modo da accettare due parametri, con il valore precedente restituito dalla query in **Query di polling** e il valore corrente restituito dalla stessa query in **Query di polling**, che possono essere usati per identificare ed estrarre solo i record aggiunti durante il periodo di polling. Questa opzione è abilitata solo se è selezionata l'opzione **Abilita aggiornamenti incrementali** .<br /><br /> **Nella tabella**: digitare l'identificatore della tabella nella quale la query nel **query di Polling** tiene traccia dell'ultimo record oppure fare clic sul pulsante con puntini di sospensione (**...** ) per aprire la **trova tabella** finestra di dialogo e selezionare la tabella. Per altre informazioni, vedere [Finestra di dialogo Trova tabella &#40;Analysis Services - Dati multidimensionali&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo Opzioni di archiviazione &#40;Analysis Services - dati multidimensionali&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md)  
  
  