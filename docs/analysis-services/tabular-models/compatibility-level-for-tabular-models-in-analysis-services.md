---
title: "Livello di compatibilit&#224; per i modelli tabulari in Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.versioncompat.f1"
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
caps.latest.revision: 27
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 27
---
# Livello di compatibilit&#224; per i modelli tabulari in Analysis Services
  Il *livello di compatibilità* di un modello o un database fa riferimento a un set di comportamenti specifici della versione nel motore di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. È possibile creare modelli con qualsiasi livello di compatibilità supportato per ottenere i comportamenti di una particolare versione. Ad esempio, le implementazioni di DirectQuery e dei metadati degli oggetti tabulari sono diverse a seconda del livello di compatibilità assegnato.  
  
 **SQL Server 2016 RTM (1200)**, in breve il livello di compatibilità 1200, è stato introdotto in SQL Server 2016 e si applica solo ai modelli tabulari.  I modelli tabulari con livello di compatibilità 1200 potranno essere eseguiti solo su un'istanza tabulare di [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].  
  
 Per creare o aggiornare un modello tabulare, usare SQL Server Data Tools (SSDT) e impostare la proprietà **Livello di compatibilità** quando si crea il progetto o nel file **model.bim** dopo aver creato il progetto.  
  
> [!NOTE]  
>  I modelli multidimensionali seguono un percorso delle versioni indipendente in termini di livelli di compatibilità. Quando i numeri sono uguali, come nel caso di 1103, si tratta di una coincidenza. Vedere [Livello di compatibilità di un database multidimensionale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md) per altre informazioni.  
  
## Livelli di compatibilità supportati per i database modello tabulari  
 Analysis Services supporta i livelli di compatibilità seguenti, applicabili sia ai modelli che ai database.  La versione dello strumento usata per creare un modello determina se sono disponibili i livelli di compatibilità superiori.  
  
||||  
|-|-|-|  
|Livello di compatibilità|Versione del server|Versione dello strumento di modellazione|  
|1200|Solo nelle istanze di SQL Server 2016|[Solo SQL Server Data Tools per Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkID=690931) <sup>1</sup><br /><br /> L'argomento [Novità di Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md) descrive le funzionalità disponibili a questo livello.|  
|1103|SQL Server 2016<br /><br /> SQL Server 2014<br /><br /> SQL Server 2012 SP1|[SQL Server Data Tools per Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkID=690931) <sup>2</sup><br /><br /> [SQL Server Data Tools per Business Intelligence (Visual Studio 2013)](https://www.microsoft.com/en-us/download/details.aspx?id=42313)<br /><br /> [SQL Server Data Tools per Business Intelligence (Visual Studio 2012)](http://www.microsoft.com/en-us/download/details.aspx?id=36843)|  
|1100|SQL Server 2016<br /><br /> SQL Server 2014<br /><br /> SQL Server 2012 SP1<br /><br /> SQL Server 2012|[SQL Server Data Tools per Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkID=690931) <sup>1</sup><br /><br /> [SQL Server Data Tools per Business Intelligence (Visual Studio 2013)](https://www.microsoft.com/en-us/download/details.aspx?id=42313)<br /><br /> [SQL Server Data Tools per Business Intelligence (Visual Studio 2012)](http://www.microsoft.com/en-us/download/details.aspx?id=36843)<br /><br /> Business Intelligence Development Studio (eseguito nella shell di Visual Studio 2010 e installato tramite il programma di installazione di SQL Server)|  
  
 <sup>1</sup> È possibile usare SQL Server Data Tools per Visual Studio 2015 per distribuire un modello tabulare 1100 o 1103 nelle versioni precedenti di Analysis Services.  
  
 <sup>2</sup> I livelli di compatibilità 1100, 1103 e 1200 sono tutti validi per i progetti di modello tabulare in SQL Server Data Tools per Visual Studio 2015, ma è possibile distribuire ed eseguire solo un modello 1200 in un'istanza di SQL Server 2016 di Analysis Services.  
  
## Impostare il livello di compatibilità durante la creazione o l'aggiornamento di un modello tabulare in SSDT  
 In fase di creazione di un nuovo progetto di modello tabulare in SQL Server Data Tools (SSDT), è possibile specificare il livello di compatibilità nella finestra di dialogo delle **opzioni per il nuovo progetto tabulare**.  
  
 ![ssas_tabularproject_compat1200](../../analysis-services/tabular-models/media/ssas-tabularproject-compat1200.jpg "ssas_tabularproject_compat1200")  
  
 È inoltre possibile specificare un livello di compatibilità predefinito se si seleziona l'opzione **Non visualizzare più questo messaggio**. In tutti i progetti successivi verrà utilizzato il livello di compatibilità specificato. È possibile modificare il livello di compatibilità predefinito in SSDT in **Strumenti** > ** Opzioni**.  
  
 Per aggiornare un progetto di modello tabulare, impostare la proprietà **Livello di compatibilità** nella finestra **Proprietà** del modello su **SQL Server 2016 RTM (1200)**.  Per ulteriori informazioni, vedere [Upgrade Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md) .  
  
> [!NOTE]  
>  Per creare un modello tabulare, è possibile basarlo su una cartella di lavoro di Power Pivot importata. Per impostazione predefinita, Power BI Desktop crea automaticamente modelli tabulari con il livello di compatibilità 1200. Le versioni precedenti delle cartelle di lavoro di Power Pivot, tuttavia, potrebbero avere il livello 1100. Quando si usa una cartella di lavoro meno recente, ricordarsi di modificare la proprietà **Livello di compatibilità** per aggiornare il livello.  
  
## Controllare il livello di compatibilità per un database in SSMS  
 In SSMS fare clic con il pulsante destro del mouse sul nome del database > **Proprietà** > **Livello di compatibilità**.  
  
## Controllare il livello di compatibilità supportato per un server in SSMS  
 In SSMS fare clic con il pulsante destro del mouse sul nome del server > **Proprietà** > **Livello di compatibilità supportato**.  
  
 Questa proprietà specifica il livello di compatibilità massimo per un database che verrà eseguito nel server.  Il livello di compatibilità supportato è di sola lettura e non può essere modificato.  
  
## Vedere anche  
 [Livello di compatibilità di un database multidimensionale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Novità di Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Importare da Power Pivot &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)   
 [Creare un nuovo progetto di modello tabulare &#40;Analysis Services&#41;](../../analysis-services/tabular-models/create-a-new-tabular-model-project-analysis-services.md)  
  
  