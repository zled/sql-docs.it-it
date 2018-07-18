---
title: Livello di compatibilità per i modelli tabulari in Analysis Services | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fd70a673744d2e401e8a28f6ce2c533434e1c75e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="compatibility-level-for-analysis-services-tabular-models"></a>Livello di compatibilità per i modelli tabulari di Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Il *livello di compatibilità* fa riferimento a una versione specifici comportamenti nel motore di Analysis Services. Ad esempio, DirectQuery e i metadati degli oggetti tabulari sono disponibili implementazioni diverse a seconda del livello di compatibilità. In generale, è necessario scegliere il livello di compatibilità più recente supportato dal server.

  **Il livello di compatibilità più recente è 1400** 
  
Le caratteristiche principali del livello di compatibilità 1400 includono:

*  Nuova infrastruttura per importare i modelli tabulari e di integrazione applicativa dei dati con supporto per TOM APIs e gli script TMSL. In questo modo il supporto per origini dati aggiuntive, ad esempio l'archiviazione Blob di Azure. Dati aggiuntivi origini sarà incluso in futuro gli aggiornamenti.
*  La trasformazione dei dati e le funzionalità di mashup di dati usando recupera dati ed M espressioni in SSDT.
*  Le misure ora supportano una proprietà di righe di dettaglio con un'espressione DAX, l'abilitazione di strumenti di Business Intelligence, ad esempio Microsoft Excel drill-down di dati dettagliati da un report aggregato. Ad esempio, quando gli utenti finali di visualizzare le vendite totali per una regione e un mese, è possibile visualizzare i dettagli ordine associato. 
*  Sicurezza a livello di oggetto per i nomi di tabelle e colonne, oltre ai dati all'interno di essi.
*  Supporto migliorato per le gerarchie incomplete.
*  Monitoraggio delle prestazioni e miglioramenti.

  
## <a name="supported-compatibility-levels-by-version"></a>Livelli di compatibilità supportato dalla versione
  
|||  
|-|-|- 
|**Livello di compatibilità**|**Versione del server**| 
|1400|Azure Analysis Services, SQL Server 2017 |  
|1200|Azure Analysis Services, SQL Server 2017, SQL Server 2016| 
|1103|SQL Server 2017*, SQL Server 2016, SQL Server 2014, SQL Server 2012 SP1|  
|1100|SQL Server 2017*, SQL Server 2016, SQL Server 2014, SQL Server 2012 SP1, SQL Server 2012| 

\* i livelli di compatibilità 1100 e 1103 sono deprecati in SQL Server 2017.
  
## <a name="set-compatibility-level"></a>Livello di compatibilità impostato 
 Quando si crea un nuovo progetto di modello tabulare in SQL Server Data Tools (SSDT), è possibile specificare il livello di compatibilità sul **progettazione di modelli tabulari** finestra di dialogo. 
  
 ![ssas_tabularproject_compat1200](../../analysis-services/tabular-models/media/ssas-tabularproject-compat1200.png)  
  
 Se si seleziona il **non visualizzare più questo messaggio** opzione, tutti i progetti successivi verranno utilizzato il livello di compatibilità è specificato come predefinito. È possibile modificare il livello di compatibilità predefinito in SSDT in **Strumenti** > **Opzioni**.  
  
 Per aggiornare un progetto di modello tabulare in SSDT, impostare il **livello di compatibilità** proprietà nel modello **proprietà** finestra. Tenere presente, l'aggiornamento del livello di compatibilità è irreversibile.
  
## <a name="check-compatibility-level-for-a-database-in-ssms"></a>Controllare il livello di compatibilità per un database in SSMS  
 In SQL Server Management Studio, fare clic sul nome del database > **proprietà** > **livello di compatibilità**.  
  
## <a name="check-supported-compatibility-level-for-a-server-in-ssms"></a>Controllare il livello di compatibilità supportato per un server in SSMS  
 In SSMS fare clic con il pulsante destro del mouse sul nome del server > **Proprietà** > **Livello di compatibilità supportato**.  
  
 Questa proprietà specifica il massimo livello di compatibilità di un database che verrà eseguito nel server. Il livello di compatibilità supportato è di sola lettura e non può essere modificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Livello di compatibilità di un database multidimensionale](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Novità di Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Creare un nuovo progetto di modello tabulare](../../analysis-services/tabular-models/create-a-new-tabular-model-project-analysis-services.md)  
  
  
