---
title: Connettersi al database e server tabulare di Analysis Services esistente | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 13900e4aaad52d39a2691fb40d0e419f55f660fc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033391"
---
# <a name="connect-to-existing-analysis-services-tabular-server-and-database"></a>Connettersi al database e server tabulare di Analysis Services esistente
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
In SQL Server 2016 Analysis Services Management Objects (AMO) sono inclusi diversi spazi dei nomi che potrebbero essere utilizzate per configurare una connessione al server. Questo articolo illustra come stabilire una connessione al server utilizzando lo spazio dei nomi Microsoft.AnalysisServices.Tabular per modelli e i database creati di 1200 o superiore a livello di compatibilità. 

Per connettersi a un server Analysis Services, il codice deve creare un'istanza di un oggetto Server e quindi chiamare il metodo Connect su di esso. Una volta connessi, le proprietà dell'oggetto Server verranno visualizzate le impostazioni dell'istanza di Analysis Services corrente. 

Le classi seguenti possono essere utilizzate per le connessioni di livello superiore: 

* Microsoft.AnalysisServices.Server 
* Microsoft.AnalysisServices.Database 
* Microsoft.AnalysisServices.Tabular.Server 
* Microsoft.AnalysisServices.Tabular.Database 

Come si può notare, due spazi dei nomi forniscono la connettività agli oggetti server e database: lo spazio dei nomi Microsoft. AnalysisServices originale per AMO e il nuovo spazio dei nomi Microsoft.AnalysisServices.Tabular per TOM.

Perché due spazi dei nomi per le stesse operazioni? La risposta risiede a valle, a livello di database e il modello, in cui la gerarchia di oggetti diventa specifici della modalità e l'albero del modello è costituito da metadati multidimensionale o tabulare. Per eseguire chiamate nell'albero del modello, l'oggetto Server o il Database viene fornito per entrambi i tipi di modello.

> [!NOTE]  
>  I metadati utilizzati per le operazioni e definizione del modello sono completamente diverso per le due modalità. Suddividendo il linguaggio di definizione dei dati (DDL) in due diversi spazi dei nomi, l'esperienza di sviluppo viene semplificata la presentazione di solo l'API necessaria per un tipo di modello specifico. 

Anche se l'istruzione DDL è diverso, le connessioni a un server sono uguali in tutte le modalità, le versioni ed edizioni. Supporto di un server e connessione al database mediante uno spazio dei nomi consente di scrivere strumenti generici o uno script che si connettono a qualsiasi istanza di Analysis Services o database, senza dover conoscere il tipo di modello è ospitato nel server.  

Questa flessibilità illustra le dipendenze tra gli assembly. Per effettuare chiamate sotto il livello di Database (ad esempio, su un modello all'interno di un database tabulare 1200, o in un cubo, dimensione o un gruppo di misure all'interno di un database multidimensionale o tabulare di 1050-1103), AMO presenta una dipendenza da TOM. 

Al contrario, TOM non dispone delle dipendenze in AMO. Sebbene TOM non può essere utilizzato per esplorare i metadati multidimensionali (cubi), AMO è utilizzabile per esplorare sia multidimensionale e metadati tabulari. 

Per questo motivo, il primo passaggio nella configurazione del progetto richiede l'aggiunta di riferimenti a tutti gli assembly AMO. Visualizzare [installa, riferimento e distribuisce la libreria client di TOM](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md) per informazioni dettagliate. 

> [!NOTE]  
>  Connessioni server e database sono basate sulle classi AMO legacy che ereditano da elemento MajorObject. Anche se gli oggetti principali e secondari non vengono usati in un albero di modelli tabulari, la classe di elemento MajorObject è visibile come classe di base per gli oggetti Server e Database, indipendentemente dal quale API consente di configurare la connessione.  

## <a name="code-example-server-connection"></a>Esempio di codice: connessione al server 

Di seguito è un esempio di codice c# che illustra come connettersi a un'istanza di Analysis Services locale ed elencare le relative proprietà nella finestra della console. 

Questo esempio mostra solo alcune delle proprietà di un oggetto Server, ma sono disponibili, tra cui ServerMode e DefaultCompatibilityLevel altre proprietà.  

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
Quando si esegue questo programma, l'output mostra le proprietà sull'oggetto Server nella finestra della console. 

## <a name="authentication-and-authorization"></a>Autenticazione e autorizzazione 

Un server o una connessione al database di Analysis Services richiede le autorizzazioni amministrative, usate per le operazioni di lettura / scrittura e per passare tramite una richiesta di connessione rappresentata.  

Anche se l'infrastruttura di sicurezza di Analysis Services è stato esteso negli ultimi anni per consentire l'autenticazione personalizzata in condizioni molto specifiche, il metodo solo l'autenticazione esterna supportata è la sicurezza integrata di Windows. Le entità di sicurezza si presuppone che sia valido Windows utente o gruppo gli account di dominio.  

In Windows 2012 e versioni successive, la delega può essere propagata tra domini. In Analysis Services, la delega viene usata solo per modelli DirectQuery. in caso contrario, le connessioni sono dirette o rappresentato. 

## <a name="next-steps"></a>Passaggi successivi 

Dopo aver stabilito una connessione, il passaggio logico successivo è per entrambi i database esistenti di elenco già sul server o forse crea un nuovo database vuoto. I collegamenti seguenti includono esempi di codice in cui vengono illustrate entrambe le attività di base: 

- [Creare e distribuire un database vuoto](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-and-deploy-an-empty-database-analysis-services-amo-tom.md)
- [Elenco dei database esistenti](../../analysis-services/tabular-model-programming-compatibility-level-1200/list-existing-databases-on-a-tabular-server-analysis-services-amo-tom.md)
