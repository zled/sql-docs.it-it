---
title: "Le proprietà per la struttura di Data Mining e le colonne della struttura | Documenti Microsoft"
ms.custom: 
ms.date: 03/13/2017
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
helpviewer_keywords:
- mining structures [Analysis Services], column properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- properties [data mining]
ms.assetid: ce90f684-bb8c-4eca-b9e6-000794dbee16
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 42ee21307542c7e204ac7b4616714c2285cce032
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="properties-for-mining-structure-and-structure-columns"></a>Proprietà delle strutture di data mining e delle colonne delle strutture di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]È possibile impostare o modificare le proprietà per una struttura di data mining e delle colonne associate e tabelle nidificate tramite il **struttura di Data Mining** scheda Progettazione modelli di Data Mining. Le impostazioni delle proprietà eseguite in questa scheda vengono propagate in ogni modello di data mining associato alla struttura.  
  
> [!NOTE]  
>  Se si modifica il valore di una proprietà nella struttura di data mining, anche di metadati come, ad esempio, un nome o descrizione, la struttura di data mining e i relativi modelli devono essere rielaborati prima che sia possibile visualizzare o eseguire una query sul modello.  
  
## <a name="properties-of-mining-structures-and-mining-structure-columns"></a>Proprietà delle strutture di data mining e delle colonne delle strutture di data mining  
 Nella tabella seguente vengono descritte le proprietà della struttura di data mining e delle colonne della struttura di data mining specifiche del data mining, che è possibile visualizzare o configurare nella scheda **Struttura di data mining** . Per visualizzare o configurare queste proprietà, fare clic con il pulsante destro del mouse su un elemento della visualizzazione albero e quindi scegliere **Proprietà**.  
  
-   Per visualizzare le proprietà della struttura, fare clic sull'intestazione della struttura di data mining.  
  
-   Per visualizzare le proprietà di una colonna o di una tabella nidificata, fare clic sul nome della colonna.  
  
### <a name="properties-of-the-mining-structure"></a>Proprietà della struttura di data mining  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**CacheMode**|Specifica se i case utilizzati nel training devono essere memorizzati nella cache o eliminati una volta completato il training. **Nota:**  questa proprietà deve essere impostata su **KeepTrainingCases** per attivare il drill-through e i dati di controllo.|  
|**Confronto**|Specifica le regole di confronto predefinite per la colonna. Se non specificato, vengono utilizzate le regole di confronto del server.|  
|**Description**|Descrive la struttura di data mining. È consigliabile che nella descrizione vengano specificati lo scopo e la composizione dei dati nella struttura.|  
|**ErrorConfiguration (predefinita)**|Specifica le opzioni per la gestione speciale di errori, se presenti.|  
|**HoldoutMaxCases**|Specifica il numero massimo di case della struttura che possono essere riservati come set di dati di test.  Se i valori vengono specificati per **HoldoutMaxCases** e **HoldoutPercent**, le condizioni vengono combinate. **Nota:**  per impostare questa proprietà, <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> deve essere impostato su **KeepTrainingCases**.|  
|**HoldoutPercent**|Specifica la percentuale dei case della struttura da riservare come set di dati di test. Se i valori vengono specificati per **HoldoutMaxCases** e **HoldoutPercent**, le condizioni vengono combinate. **Nota:**  per impostare questa proprietà, <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> deve essere impostato su **KeepTrainingCases**.|  
|**HoldoutSeed**|Specifica un valore per l'inizializzazione del partizionamento del set di test di controllo, per assicurare che il set di dati di test possa essere ricreato. **Nota:**  per impostare questa proprietà, <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> deve essere impostato su **KeepTrainingCases**.|  
|**ID**|Consente di visualizzare l'identificatore univoco della struttura di data mining.<br /><br /> Il nome assegnato alla struttura di data mining quando è stata creata viene utilizzato come ID. Se successivamente si modifica il nome digitando un nuovo valore per la proprietà **nome** , il nuovo nome viene utilizzato solo come alias. L'ID non viene modificato.|  
|**Lingua**|Specifica la lingua delle didascalie della struttura di data mining.|  
|**nome**|Specifica il nome o l'alias della struttura di data mining.<br /><br /> Se si modifica il valore della proprietà Name, il nuovo nome viene utilizzato solo come didascalia o alias. L'identificatore della struttura di data mining non viene modificato.|  
|**Origine**|Visualizza il nome dell'origine dati e il tipo di origine dati.|  
  
### <a name="properties-of-the-mining-structure-columns"></a>Proprietà delle colonne della struttura di data mining  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**ClassifiedColumns**|Identifica la colonna descritta da una colonna classificata.|  
|**Contenuto**|Tipo di contenuto della colonna.|  
|**Description**|Descrive la colonna. È consigliabile che la descrizione della colonna fornisca informazioni sulla derivazione o l'alterazione dei dati della colonna per il data mining.|  
|**DiscretizationBucketCount**|Visualizza il numero di bucket della colonna discretizzata.<br /><br /> Attivato solo se il tipo di contenuto è impostato su **Discretized**.<br /><br /> Questa proprietà è di sola lettura.|  
|**DiscretizationMethod**|Visualizza il metodo utilizzato per discretizzare la colonna.<br /><br /> Attivato solo se il tipo di contenuto è impostato su **Discretized**.<br /><br /> Questa proprietà è di sola lettura.|  
|**Distribuzione**|Specifica la distribuzione del contenuto della colonna.|  
|**ID**|Visualizza l'identificatore della colonna.<br /><br /> Se si modifica il valore della proprietà Name della colonna, non influisce sul valore della proprietà ID.|  
|**IsKey**|Indica se la colonna è una colonna chiave.|  
|**KeyColumns**|Contiene la definizione di una colonna che corrisponde alla chiave o fa parte della chiave di un attributo.|  
|**ModelingFlags**|Imposta parametri aggiuntivi disponibili tramite l'algoritmo.|  
|**nome**|Nome della colonna.|  
|**NameColumn**|Identifica la colonna che fornisce il nome dell'elemento padre.|  
|**Origine**|Visualizza l'origine della colonna.<br /><br /> Per le origini dati relazionali, il valore è sempre **(nessuno)**.<br /><br /> Per le strutture basate su un cubo OLAP, il valore è l'istruzione MDX che definisce la sezione utilizzata come origine per la tabella nidificata.|  
|**SourceMeasureGroup**|Visualizza l'origine del gruppo di misure.<br /><br /> Per le origini dati relazionali, il valore è sempre **(nessuno)**.<br /><br /> Per le strutture basate su un cubo OLAP, il valore è l'istruzione MDX che definisce la sezione utilizzata come origine per la tabella nidificata.|  
|**Tipo**|Tipo di dati del contenuto della colonna.|  
  
 Per altre informazioni sull'impostazione o sulla modifica delle proprietà, vedere [attività e procedure relative alla struttura di data mining](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una struttura di data mining relazionale](../../analysis-services/data-mining/create-a-relational-mining-structure.md)   
 [Colonne della struttura di data mining](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
