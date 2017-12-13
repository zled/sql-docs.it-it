---
title: Installare, distribuire e fare riferimento al modello a oggetti tabulare | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e51769f7-aac7-4835-a5ae-91aac04aa476
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 60d264dccf042ec9447d92f17045f238597cd29e
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="install-distribute-and-reference-the-tabular-object-model"></a>Installare, distribuire e fare riferimento al modello a oggetti tabulare
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]In questo articolo viene illustrato come scaricare, fare riferimento e ridistribuire Analysis Services tabulare oggetto modello TOM (), una libreria di c# per la creazione e gestione di database nel codice gestito e i modelli tabulari.  
  
TOM è un'estensione della libreria client AMO (Microsoft.AnalysisServices.dll) fornito con SQL Server 2016. Funziona con i modelli tabulari di destinazione è il motore di metadati tabulari nella versione SQL Server 2016. Per utilizzare TOM, il modello e il database deve essere a livello di compatibilità 1200 o superiore.  

## <a name="amo-tom-assemblies"></a>Assembly AMO TOM

SQL Server 2016 effettua il refactoring e si espande AMO per includere i nuovi assembly di componenti di base, tabulare e JSON. Include anche l'assembly AMO originale, Microsoft.AnalysisServices.dll, che è stato parte di Analysis Services dopo il primo rilascio. Un ristrutturazione AMO offload classi comuni a un assembly e fornisce una divisione logica tra API multidimensionali e tabulari tramite assembly aggiuntivi. 

La tabella seguente descrive ciascun assembly.
  
Assembly  |Funzionalità  |Classi importanti |
---------|---------|--------------  |
Core <br/>Microsoft.AnalysisServices.Core.dll | In genere per il database sia tabulare e multidimensionale. <br/><br/>Fornisce gestione delle eccezioni, generiche connessioni a un'istanza di Analysis Services e un database e l'accesso a proprietà e metodi comuni per gli oggetti Server e Database. <br/><br/>È necessario per qualsiasi soluzione AMO per SQL Server 2016. | Core&nbsp;Server<br/>Core&nbsp;Database<br/>Eccezione AmoException
TOM<br/> Microsoft.AnalysisServices.Tabular.dll, versione 13.0.1601.5 o versione successiva.| Creare e gestire gli oggetti di metadati tabulari. | TOM&nbsp;Server <br/>TOM&nbsp;Database<br /> Modello<br /> Tabella<br /> Colonna<br /> Relazione
  AMO<br /> Microsoft.AnalysisServices.dll| Creare e gestire oggetti di metadati multidimensionali, inclusi i database tabulare 1050-1103. | AMO&nbsp;Server <br />AMO&nbsp;Database <br /> Cube <br /> Dimensione <br /> MeasureGroup 
Json<br/>Microsoft.AnalysisServices.Tabular.Json.dll | Supporto DLL che esegue il wrapping NewtonSoftJson.dll (JSON.NET) per controllare gli aggiornamenti, rimuovendo il rischio di introdurre modifiche funzionali per la serializzazione JSON nei carichi di lavoro di Analysis Services. <br /> <br />Questa DLL esiste come una dipendenza in TOM e non deve essere utilizzato direttamente nel codice. | nessuna.  
  
 ### <a name="understanding-assembly-dependencies"></a>Informazioni sulle dipendenze di assembly
  
Per programmare gli oggetti AMO, la soluzione deve includere i riferimenti alle DLL dipendenti. AMO e TOM dipendono Core perché fornisce le classi di base.

AMO dipende da TOM perché alcune classi nella libreria AMO fare riferimento alle classi da TOM. Ad esempio, l'oggetto di Database AMO è una proprietà modello di tipo modello implementata nella dll TOM. 

![Dipendenze di TOM AMO](../../analysis-services/tabular-model-programming-compatibility-level-1200/media/amo-tom-dependencies.png)

Non è possibile distribuire Microsoft.AnalysisServices.dll senza Microsoft.AnalysisServices.Tabular.dll, ma è possibile fare riferimento a spazi dei nomi corrispondente senza l'altro.

### <a name="choosing-which-namespace-to-use-in-code"></a>Scelta di quale spazio dei nomi da utilizzare nel codice

Nel [gerarchia di oggetti](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md) , qualsiasi oggetto inferiore al Database è una costruzione di metadati tabulari tramite l'oggetto modello o una costruzione metadati multidimensionali tramite un oggetto cubo, dimensione o MeasureGroup. Operazioni di alto livello a livello di Server, Database, ruolo o traccia, deve supportare la scelta di quale spazio dei nomi per fare riferimento a dipenderà i carichi di lavoro il codice.

* Se la soluzione è il livello di compatibilità 1200 o superiore e l'oggetto di Database che si lavora con necessario fornire l'accesso al modello, tabella, colonne e altri oggetti espresse come costruzioni di metadati tabulari, utilizzare Tabular.Server o Tabular.
* Utilizzare AnalysisServices.Server o AnalysisServices.Database se il codice a valle fa riferimento a oggetti multidimensionali, ad esempio cubi, origini dati, DataSourceViews e dimensioni.

È necessario che entrambi gli spazi dei nomi per gli strumenti e applicazioni che supportano una combinazione di tipi di modello e di database. 

Spazio dei nomi principale nel codice di riferimento non è necessaria. le classi base sono classi base create allo scopo di fornire proprietà comuni, quali il nome e descrizione, per gli oggetti principali.  
  
## <a name="determine-whether-amo-and-tom-installation-is-required"></a>Determinare se è necessaria la libreria AMO e TOM installazione  
   
 AMO e TOM sono collegate tra loro in una libreria client singolo. Se già installata un'istanza di SQL Server 2016 Analysis Services, le librerie client o una versione di SQL Server Data Tools destinato a un'istanza SQL Server 2016, Microsoft.AnalysisServices.dll è già installato.  
  
 Per determinare se gli assembly sono già installati, selezionare uno dei percorsi seguenti:
* C:\Windows\Microsoft.NET\assembly\GAC_MSIL
* C:\Program Files\Microsoft SQL Server\130\SDK\Assemblies
* C:\Program Files\Microsoft SQL Server\130\DTS\Tasks
* C:\Program Files\Microsoft SQL Server\MSAS13. MSSQLSERVER\OLAP\bin
 
 Verificare che gli assembly seguenti esistono:
*  Microsoft.AnalysisServices.Core.dll
*  Microsoft.AnalysisServices.dll
*  Microsoft.AnalysisServices.Tabular.dll
*  Microsoft.AnalysisServices.Tabular.Json.dll   
   
## <a name="download-sqlasamo"></a>Scaricare SQL_AS_AMO  
 
 Si noti che Microsoft.AnalysisServices.dll non è disponibile attraverso Gestione NuGet.
  
1. Passare a [pagina di Download del Feature Pack di SQL Server 2016](https://www.microsoft.com/download/details.aspx?id=52676).  
  
2. Fare clic su **Download**.  
  
3. Selezionare l'opzione **\X64\SQL_AS_AMO.msi** o **\X86\SQL_AS_AMO.msi**. È possibile scegliere dei due: AMO e TOM assembly sono indipendenti dalla piattaforma.
  
4. Fare clic su **Avanti** per procedere con il download. I file con estensione msi in si trovano i **Scarica** cartella.  
  
## <a name="install-sqlasamo"></a>Installare SQL_AS_AMO  
  
1. Fare doppio clic su **SQL_AS_AMO.msi** ed eseguire l'installazione.  
  
2. Passare a **C:\Program Files\Microsoft SQL Server\130\SDK\Assemblies** per confermare la posizione di Microsoft.AnalysisServices.Core.dll, Microsoft.AnalysisServices.dll, Microsoft.AnalysisServices.Tabular.dll, e Microsoft.AnalysisServices.Tabular.Json.dll.   
  
## <a name="add-references"></a>Aggiungere riferimenti  
  
1. In **Esplora** > **aggiungere riferimento** > **Sfoglia**.  
2. Passare a **C:\Program Files\Microsoft SQL Server\130\SDK\Assemblies** e selezionare:  
   * AnalysisServices  
   * Microsoft.AnalysisServices.Tabular  
   * Microsoft.AnalysisSerivces.Tabular.Json  
  
3. Scegliere **OK**.  In **Esplora**, verificare gli assembly siano presenti nella cartella riferimenti.
  
4. Nella pagina di codice, aggiungere lo spazio dei nomi analysisservces se i database e i modelli tabulari 1200 o livello di compatibilità superiore. 
  
   ```   
   using Microsoft.AnalysisServices; 
   using Microsoft.AnalysisServices.Tabular;
   ```  
    Facoltativamente, aggiungere Microsoft.AnalysisServces per supportare un set più ampio di connessioni a istanze di Analysis Services che non sono in particolare in SQL Server 2016 in modalità server tabulare. 
 
    Quando si include spazi dei nomi che hanno in comune le classi per gli oggetti Server, Database, ruolo e traccia, è possibile evitare riferimenti ambigui specificando quali lo spazio dei nomi che si desidera utilizzare (ad esempio, Microsoft.AnalysisServices.Tabular.Server crea un'istanza di un Server oggetto con lo spazio dei nomi tabulare).

## <a name="redistribute-amo-and-tom-with-your-application"></a>Ridistribuire AMO e TOM con l'applicazione  
  
Ridistribuzione di AMO e TOM è tramite il **sql_as_amo.msi** pacchetto di installazione. Se si compila un programma di installazione per un'applicazione client che chiama in AMO o TOM, aggiungere **sql_as_amo.msi** per il file eseguibile. Questo è l'unico meccanismo supportato per la ridistribuzione delle librerie client AMO e TOM.  
  
Il pacchetto è indipendente e offre tutti gli assembly richiesti per la chiamata di AMO e TOM nel codice. Altri pacchetti, ad esempio SQL_AS_OLEDB.msi o SQL_AS_ADOMD.msi, non sono richiesti per gli scenari di programmazione TOM.
