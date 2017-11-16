---
title: Partizioni abilitate la scrittura | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- storage [Analysis Services], partitions
- write-enabled partitions [Analysis Services]
- partitions [Analysis Services], write-enabled
- partitions [Analysis Services], storage
- writeback [Analysis Services], partitions
- storing data [Analysis Services], partitions
ms.assetid: 46e7683f-03ce-4af2-bd99-a5203733d723
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 87ca933c004d59a8c2e680d79e9d9499700f7e43
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="partitions---write-enabled-partitions"></a>Partizioni - partizioni abilitate per scrittura
  I dati di un cubo sono in genere di sola lettura. In determinati scenari, tuttavia, può rivelarsi utile abilitare una partizione per la scrittura. Le partizioni abilitate per la scrittura vengono utilizzate per consentire agli utenti aziendali di sperimentare vari scenari modificando i valori delle celle e analizzando gli effetti delle modifiche sui dati del cubo. Quando si abilita per la scrittura una partizione, le applicazioni client potranno registrare modifiche ai dati nella partizione. Tali modifiche, note come dati writeback, vengono archiviate in una tabella separata e non sovrascrivono i dati esistenti in un gruppo di misure. Vengono però incorporate nei risultati delle query come se facessero parte dei dati del cubo.  
  
 È possibile abilitare per la scrittura un intero cubo o soltanto determinate partizioni nel cubo. Le dimensioni abilitate per la scrittura sono diverse ma complementari. Una partizione abilitata per la scrittura consente agli utenti di aggiornare le celle della partizione, mentre una dimensione abilitata per la scrittura consente agli utenti di aggiornare i membri della dimensione. È inoltre possibile utilizzare queste due caratteristiche in combinazione. Una partizione o un cubo abilitato per la scrittura, ad esempio, non deve necessariamente includere dimensioni abilitate per la scrittura. **Argomento correlato:**[dimensioni abilitate per la scrittura](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).  
  
> [!NOTE]  
>  Se si desidera abilitare per la scrittura un cubo con un database Microsoft Access come origine dati, non utilizzare il provider Microsoft OLE DB per driver ODBC nelle definizioni dell'origine dati del cubo, delle partizioni o delle dimensioni. Utilizzare invece il provider Microsoft OLE DB per Jet versione 4.0 o qualsiasi versione del Service Pack di Jet che include OLE per Jet 4.0. Per ulteriori informazioni, vedere l'articolo della Microsoft Knowledge Base [come ottenere il service pack più recente per il motore di Database Microsoft Jet 4.0](http://support.microsoft.com/?kbid=239114).  
  
 Un cubo può essere abilitata per la scrittura solo se tutte le misure utilizzano la **somma** funzione di aggregazione. I gruppi di misure collegati e i cubi locali non possono essere abilitati per la scrittura.  
  
## <a name="writeback-storage"></a>Archiviazione writeback  
 Qualsiasi modifica apportata dall'utente aziendale viene archiviata nella tabella writeback come differenza rispetto al valore attualmente visualizzato. Ad esempio, se un utente finale modifica un valore di cella da 90 a 100, il valore **+ 10** viene archiviato nella tabella writeback, insieme all'ora della modifica e alle informazioni relative all'utente di business che l'ha apportata. Alle applicazioni client viene visualizzato il risultato finale delle modifiche cumulative. In questo modo, il valore originale del cubo viene mantenuto e nella tabella writeback viene memorizzata un itinerario di controllo delle modifiche.  
  
 Le modifiche apportate a celle foglia e non foglia vengono gestite in modo diverso. Una cella foglia rappresenta un'intersezione di una misura e un membro foglia di ogni dimensione a cui fa riferimento il gruppo di misure. Il valore di una cella foglia viene recuperato direttamente dalla tabella dei fatti e non può essere suddiviso ulteriormente tramite il drill-down. Se qualsiasi partizione o un cubo è abilitato per la scrittura, possono essere apportate modifiche alle celle foglia. Le celle non foglia possono essere modificate solo se l'applicazione client consente di distribuire le modifiche tra le celle foglia che compongono la cella non foglia. Questo processo, denominato allocazione, viene gestito tramite l'utilizzo dell'istruzione UPDATE CUBE in espressioni MDX (MultiDimensional Expression). Gli sviluppatori di applicazioni di Business Intelligence possono utilizzare l'istruzione UPDATE CUBE per includere funzionalità di allocazione. Per ulteriori informazioni, vedere [istruzione UPDATE CUBE &#40; MDX &#41; ](../../mdx/mdx-data-manipulation-update-cube.md).  
  
> [!IMPORTANT]  
>  Quando le celle aggiornate non si sovrappongono, la proprietà della stringa di connessione **Update Isolation Level** può essere usata per migliorare le prestazioni di UPDATE CUBE. Per altre informazioni, vedere <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>.  
  
 Indipendentemente dal fatto che un'applicazione client distribuisca le modifiche apportate alle celle non foglia, durante la valutazione delle query le modifiche nella tabella writeback vengono applicate sia alle celle foglia che alle celle non foglia. Gli utenti aziendali possono pertanto verificare gli effetti delle modifiche nell'intero cubo.  
  
 Le modifiche apportate dall'utente aziendale vengono mantenute in una tabella writeback separata che può essere utilizzata come segue:  
  
-   Convertita in una partizione per incorporare le modifiche nel cubo in modo definitivo. Il gruppo di misure verrà impostato automaticamente come di sola lettura. È possibile specificare un'espressione filtro per selezionare le modifiche da convertire.  
  
-   Ignorata in modo da ripristinare lo stato originale della partizione. La partizione verrà impostata automaticamente come di sola lettura.  
  
## <a name="security"></a>Security  
 Un utente aziendale è autorizzato a registrare modifiche nella tabella writeback di un cubo solo se appartiene a un ruolo con autorizzazione in lettura/scrittura per le celle del cubo. È possibile determinare le singole celle del cubo aggiornabili per ogni ruolo. Per ulteriori informazioni, vedere [concedere cubo o modello autorizzazioni &#40; Analysis Services &#41; ](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Dimensioni abilitate per scrittura](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)   
 [Le aggregazioni e progettazione di aggregazioni](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)   
 [Partizioni &#40;Analysis Services - Dati multidimensionali&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Dimensioni abilitate per la scrittura](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  

