---
title: Connettersi al server tabulare di Analysis Services esistente e database | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 05be704e-4ee4-4101-b5ce-96fdda18c639
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9f8282029d3f20075ed35b29e1af913a882075da
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="connect-to-existing-analysis-services-tabular-server-and-database"></a>Connettersi al database e server tabulare di Analysis Services esistente
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]In SQL Server 2016 Analysis Services Management Objects (AMO) include diversi spazi dei nomi utilizzato per impostare una connessione al server. In questo articolo viene illustrato come stabilire una connessione al server utilizzando lo spazio dei nomi Microsoft.AnalysisServices.Tabular per i modelli e i database creati di 1200 o livello di compatibilità superiore. 

Per connettersi a un server Analysis Services, il codice deve creare un'istanza di un oggetto Server, quindi chiamare il metodo Connect su di esso. Una volta connessi, le proprietà dell'oggetto Server rifletterà le impostazioni dell'istanza di Analysis Services corrente. 

Per le connessioni di livello superiore, è possono utilizzare le classi seguenti: 

* Microsoft. AnalysisServices 
* Microsoft.AnalysisServices.Database 
* Microsoft.AnalysisServices.Tabular.Server 
* Microsoft.AnalysisServices.Tabular.Database 

Come si può notare, due spazi dei nomi fornire la connettività al server e oggetti di database: spazio dei nomi Microsoft. AnalysisServices originale per AMO e il nuovo spazio dei nomi Microsoft.AnalysisServices.Tabular per TOM.

Motivo per cui due spazi dei nomi per le stesse operazioni? La risposta è dovuto a valle, a livello di database e il modello, in cui la gerarchia di oggetti diventa specifico della modalità e l'albero del modello è costituito da metadati multidimensionale o tabulare. Per eseguire chiamate nell'albero del modello, viene fornito l'oggetto Server o Database per entrambi i tipi di modello.

> [!NOTE]  
>  I metadati utilizzati per le operazioni e di definizione del modello sono completamente diverso per le due modalità. Suddividendo il linguaggio di definizione dei dati (DDL) in due spazi dei nomi distinti, viene semplificata l'esperienza di sviluppo tramite la presentazione delle API necessaria per un tipo di modello specifico. 

Anche se l'istruzione DDL diversa, le connessioni a un server siano gli stessi in tutti i metodi, versioni e le edizioni. Supporto di un server e la connessione al database mediante uno spazio dei nomi consente di scrivere strumenti generici o uno script che si connettono a qualsiasi istanza di Analysis Services o database, senza dover conoscere il tipo di modello è ospitato nel server.  

Questa flessibilità viene le dipendenze tra gli assembly. Per effettuare chiamate sotto il livello di Database (ad esempio, un modello all'interno di un database tabulari 1200, o su un cubo, una dimensione o un gruppo di misure all'interno di un database multidimensionale o tabulare di 1050-1103), AMO presenta una dipendenza TOM. 

Al contrario, TOM non presentano dipendenza AMO. Sebbene TOM non può essere utilizzato per esplorare i metadati multidimensionali (cubi), è possibile utilizzare AMO per esplorare i metadati in formato tabulare e multidimensionale. 

Per questo motivo, il primo passaggio nella configurazione di progetto richiede l'aggiunta di riferimenti a tutti gli assembly AMO. Vedere [installare, riferimento e distribuire la libreria client di TOM](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md) per informazioni dettagliate. 

> [!NOTE]  
>  Connessioni server e database sono basate sulle classi AMO legacy che ereditano da MajorObject. Anche se gli oggetti principali e secondari non sono utilizzati in una struttura ad albero del modello tabulare, la classe MajorObject è visibile come classe base per gli oggetti Server e Database, indipendentemente dall'API consentono di configurare la connessione.  

## <a name="code-example-server-connection"></a>Esempio di codice: connessione al server 

Di seguito è un esempio di codice c# che illustra come connettersi a un'istanza di Analysis Services locale ed elencare le proprietà in una finestra della console. 

In questo esempio mostra solo alcune delle proprietà di un oggetto Server, ma sono disponibili altre proprietà, tra cui ServerMode e DefaultCompatibilityLevel.  

```
using System; 
using Microsoft.AnalysisServices.Tabular; 

namespace TOMSamples 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // 
            // Connect to the local default instance of Analysis Services 
            // 
            string ConnectionString = "DataSource=localhost"; 


            // 
            // The using syntax ensures the correct use of the 
            // Microsoft.AnalysisServices.Tabular.Server object. 
            // 
            using (Server server = new Server()) 
            { 
                server.Connect(ConnectionString); 

 
                Console.WriteLine("Connection established successfully."); 
                Console.WriteLine(); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.WriteLine("Server name:\t\t{0}", server.Name); 
                Console.WriteLine("Server product name:\t{0}", server.ProductName); 
                Console.WriteLine("Server product level:\t{0}", server.ProductLevel); 
                Console.WriteLine("Server version:\t\t{0}", server.Version); 
                Console.ResetColor(); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```
Quando si esegue il programma, l'output mostra le proprietà sull'oggetto Server in una finestra della console. 

## <a name="authentication-and-authorization"></a>Autenticazione e autorizzazione 

Un server o una connessione al database di Analysis Services richiede autorizzazioni amministrative, utilizzate per le operazioni di lettura / scrittura e per passare a una richiesta di connessione rappresentata.  

Anche se l'infrastruttura di sicurezza di Analysis Services è stato esteso negli ultimi anni, per consentire l'autenticazione personalizzata in condizioni molto specifiche, è supportato solo l'autenticazione esterna sicurezza integrata di Windows. Entità di sicurezza vengono considerate validi utente o gruppo di account di dominio Windows.  

In Windows 2012 e versioni successive, la delega può essere propagata tra domini. In Analysis Services, la delega viene utilizzata solo per i modelli DirectQuery. in caso contrario, le connessioni sono dirette o rappresentato. 

## <a name="next-steps"></a>Passaggi successivi 

Una volta stabilita una connessione, un passaggio successivo logico è per entrambi i database esistenti di elenco già sul server oppure di creare un nuovo database vuoto. I collegamenti seguenti sono esempi di codice che illustrano entrambe queste attività di base: 

- [Creare e distribuire un database vuoto](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-and-deploy-an-empty-database-analysis-services-amo-tom.md)
- [Elenco dei database esistenti](../../analysis-services/tabular-model-programming-compatibility-level-1200/list-existing-databases-on-a-tabular-server-analysis-services-amo-tom.md)
