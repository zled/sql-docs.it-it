---
title: Introduzione al modello a oggetti tabulare (TOM) in Analysis Services AMO | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 57a4a934-ecd0-4365-8147-d36899d86751
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: ab4bfb890124538878fd4d618dee05d393a4864c
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="introduction-to-the-tabular-object-model-tom-in-analysis-services-amo"></a>Introduzione al modello a oggetti tabulare (TOM) in Analysis Services AMO

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Il modello a oggetti tabulare (TOM) è un'estensione della libreria client servizi oggetto AMO (Analysis Management), creata per supportare scenari di programmazione per modelli tabulari compilati a livello di compatibilità 1200 e versioni successiva. Come con gli oggetti AMO, TOM fornisce un modo programmatico per gestire le funzioni amministrative quali la creazione di modelli, importazione e aggiornamento dei dati e l'assegnazione di ruoli e autorizzazioni.  
  
TOM espone metadati tabulari nativo, ad esempio **modello**, **tabelle**, **colonne**, e **relazioni** oggetti.  Una vista di alto livello dell'albero del modello oggetto riportata di seguito viene illustrato come correlazione tra le parti componenti.  
  
 Poiché TOM è un'estensione della libreria AMO, tutte le classi che rappresentano nuovi oggetti tabulari, introdotti in SQL Server 2016 vengono implementate in un nuovo assembly Microsoft.AnalysisServices.Tabular.dll. Classi di uso generale di AMO sono state spostate all'assembly AnalysisServices. Il codice sarà necessario fare riferimento a entrambi gli assembly.
Vedere [installare, distribuire e fare riferimento al modello a oggetti tabulare &#40; Microsoft.AnalysisServices.Tabular &#41; ](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md) per informazioni dettagliate.  
  
 Attualmente, l'API è disponibile solo per codice gestito in .NET framework. Per esaminare l'elenco completo di programmazione di opzioni, incluso il supporto del linguaggio di script e query, vedere [di programmazione del modello tabulare per 1200 a livello di compatibilità](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md).  
  
## <a name="tabular-object-model-hierarchy"></a>Gerarchia del modello a oggetti tabulare  
 Dal punto di vista logico, tutti gli oggetti tabulari formano una struttura ad albero, la cui radice è un **modello**, discende dal Database. **Server** e **Database** non sono considerati "tabulare" poiché questi oggetti possono anche rappresentare un database multidimensionale ospitato in un server in esecuzione in modalità multidimensionale o un modello tabulare con un livello di compatibilità inferiore livello che non usano metadati tabulari per le definizioni degli oggetti. 
  
 Ad eccezione di **AttributeHierarchy**, **KPI**, e **LinguisticMetadata**, ogni oggetto figlio può essere un membro di una raccolta. Ad esempio, il **modello** oggetto contiene una raccolta di **tabella** oggetti (tramite il **tabelle** proprietà), con ogni **tabella** oggetto contenente una raccolta di **colonna** oggetti e così via.  
  
 Il discendente di livello più basso di qualsiasi oggetto padre nella gerarchia è un **annotazione** oggetto che può essere utilizzato facoltativamente estendere lo schema, purché si forniscono il codice per gestirla.  
  
 ![diagramma della gerarchia oggetto](../../analysis-services/tabular-model-programming-compatibility-level-1200/media/ssastomobjectmodeldiagram.png "diagramma gerarchia degli oggetti")  
  
## <a name="tom-and-other-related-technologies"></a>TOM e altre tecnologie correlate

TOM si basa sull'infrastruttura di AMO, che consente inoltre multidimensionale e i database tabulari con livelli di compatibilità inferiore a 1200.

Questo fatto ha alcune implicazioni pratiche.
Prima di tutto, quando si gestiscono gli oggetti che non sono specificati nei metadati tabulari (ad esempio un **Server** o **Database**), è necessario sfruttare le parti dello stack AMO esistente che descrivono gli oggetti. Con l'API legacy è il concetto di oggetti principali e secondari che forniscono granulare descrizioni dello stato dell'oggetto come individuato dal server o salvati nel server. Espone i metodi per la classe MajorObject nello spazio dei nomi Microsoft. AnalysisServices **aggiornamento** e **aggiornamento**. Gli oggetti secondari sono solo l'aggiornamento o salvati tramite l'oggetto principale che li contiene.

Al contrario, quando si gestiscono gli oggetti che fanno parte di metadati tabulari (ad esempio **modello** o **tabella**), è sfruttare uno stack tabulare completamente nuovo. In questo stack, gli aggiornamenti sono specifici, ovvero tutti gli oggetti di metadati (derivato dal **MetadataObject** classe nello spazio dei nomi Microsoft.AnalysisServices.Tabular) possono essere salvati singolarmente nel server. In genere, è necessario individuare l'intero **modello**, quindi apportare modifiche a oggetti di metadati specifici (ad esempio **tabella** o **colonna**), quindi chiamare  **Model.SaveChanges()** metodo (che è in grado di riconoscere le modifiche apportate dall'utente a livello di granularità fine), l'invio di comandi al server per aggiornare solo gli oggetti modificati.

### <a name="tom-and-xmla"></a>TOM e XMLA

In transito, TOM utilizza il protocollo XMLA per comunicare con il server Analysis Services e per gestire gli oggetti. Quando si gestiscono gli oggetti non tabulari, TOM utilizza [ASSL](../scripting/analysis-services-scripting-language-assl-for-xmla.md), l'estensione di Analysis Services Scripting Language di XMLA. Quando si gestiscono oggetti tabulari, TOM utilizza il protocollo tabulare di SSAS, anche un'estensione di XMLA. Vedere [documentazione relativa al protocollo MS-SSAS-T SQL Server Analysis Services tabulare](https://msdn.microsoft.com/library/mt719260.aspx) per ulteriori informazioni.

### <a name="tom-and-json"></a>TOM e JSON

Metadati tabulari, in cui sono strutturato come documenti JSON, dispone di un nuovo comando e oggetti modello sintassi di definizione tramite il linguaggio di Scripting del modello tabulare [TMSL](../tabular-model-scripting-language-tmsl-reference.md). Il linguaggio di scripting utilizza JSON per il corpo di richieste e risposte.

Sebbene sia TMSL e TOM esporre oggetti stesso (**tabella**, **colonna**e così via) e le stesse operazioni (**crea**, **eliminare**,  **Aggiorna**), TOM non utilizza TMSL in transito (il protocollo viene utilizzato MS-SSAS tabulare, invece, come evidenziato in precedenza).

Come un utente, è possibile scegliere se gestire i database tabulari tramite la libreria di TOM dal programma in c# o script di PowerShell o script TMSL eseguita tramite PowerShell, SQL Server Management Studio (SSMS) o un processo di SQL Server Agent.

La decisione di utilizzare uno o l'altro verrà verso il basso per le specifiche delle proprie esigenze. La libreria di TOM fornisce le funzionalità più complete rispetto a TMSL. In particolare, mentre TMSL offre solo le operazioni a livello di Database, tabella, partizione o ruolo, TOM consente operazioni più dettagliati. Per generare o aggiornare i modelli a livello di codice, è necessario l'effettiva entità dell'API nella libreria TOM.
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione del modello tabulare per il livello di compatibilità 1200](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)   
 [Livello di compatibilità per i modelli tabulari in Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
[PowerShell per Analysis Services](../../analysis-services/powershell/analysis-services-powershell-reference.md)
  

