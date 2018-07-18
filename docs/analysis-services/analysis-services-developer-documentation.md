---
title: Documentazione per sviluppatori di Analysis Services | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 978819f3b8af369942dde2c3c18d6ca117489633
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="analysis-services-developer-documentation"></a>Guida per gli sviluppatori (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

In Analysis Services, quasi tutti gli oggetti e un carico di lavoro è programmabile ed è spesso più approcci tra cui scegliere.  Le opzioni includono scrittura di codice gestito, script o mediante standard aperti come XMLA e MSOLAP se i requisiti della soluzione precludono l'utilizzo di .NET framework.

## <a name="what-you-can-accomplish-in-code"></a>Cosa è possibile eseguire nel codice
Gli scenari di programmazione tipici includono server e la distribuzione del database, amministrazione, modello e la creazione del database e accesso ai dati dai report che utilizzano dati di Analysis Services e applicazioni personalizzate. Comune a tutti questi scenari è una fisso architettura e oggetto definizione gerarchia, con operazioni ben definite che comprendono la definizione di dati, elaborazione e i carichi di lavoro di query.

Anche se gli oggetti e i carichi di lavoro sono programmabili, non sono estendibili. In particolare, è possibile creare cartucce dati personalizzate che recuperano dati da origini dati non supportato, personalizzano o sostituire i comportamenti di motore di formula o di archiviazione, né creare nuovi tipi di metadati degli oggetti in un server, un database o un modello.

Per approfondire ulteriormente l'ultimo punto sulla creazione di nuovi tipi di oggetto: mentre è possibile creare un nuovo tipo di oggetto, è possibile creare oggetti calcolati compilati in base alle espressioni o codice in fase di esecuzione. Non tutti gli elementi del modello deve essere predefiniti e il mapping a una struttura di dati esistente. Inoltre, è possibile estendere lo schema tramite le annotazioni in AMO per passare informazioni specifiche dell'oggetto all'applicazione client.

## <a name="choose-a-platform-or-approach-to-development"></a>Scegliere una piattaforma o un approccio per lo sviluppo
Analysis Services sono disponibili diversi modi per personalizzare una soluzione tramite codice, ma la maggior parte degli sviluppatori di utilizzano l'API gestita o lo script.

- Includono le API gestite [AMO e TOM](http://msdn.microsoft.com/library/mt436122.aspx) per la definizione di dati e le attività amministrative, e [ADOMD.NET](http://msdn.microsoft.com/library/mt465769.aspx) per supportare le query dal codice client. In SQL Server 2016, AMO viene aggiornato per utilizzare i nuovi metadati tabulari per i modelli creati o aggiornati a livello di compatibilità 1200 o superiore.

- Script spesso possibile ottenere gli stessi risultati di un programma eseguibile, possibilmente con minore.

  - È possibile scrivere script di PowerShell usando i componenti di PowerShell per Analysis Services che chiamano direttamente i tipi AMO. All'interno di PowerShell, è anche possibile creare ed eseguire ASSL/XMLA o script TMSL (in JSON).

  - ASSL e TMSL sono linguaggi di script che forniscono gli oggetti utilizzati in individuano ed eseguono le operazioni. Il tipo di script utilizzati dipende dal server, database o un modello sottostante.

  - I modelli tabulari o database a livello di compatibilità 1200 e versioni successiva è possibile utilizzare il Tabular Model Scripting Language (TMSL), che è in JSON.

  - I modelli multidimensionali e modelli tabulari con livelli di compatibilità 1050-1103 utilizzano Analysis Services Scripting Language (ASSL), che è l'estensione di Analysis Services dello standard aperto XMLA.

  - È possibile generare script ASSL o TMSL in Management Studio. È inoltre possibile utilizzare **Visualizza codice** in SQL Server Data Tools per visualizzare la definizione del modello in ASSL o TMSL.

- Sebbene sia possibile compilare una soluzione basata su standard aperto XMLA e MDX, è piuttosto raro a tale scopo. Alcuna documentazione diverso da XMLA e riferimento a MDX per e la maggior parte dei forum di supporto e community disegna da esperienze con .NET o tecnologie (MSOLAP) native.

## <a name="programming-in-analysis-services"></a>Programmazione in Analysis Services
[Programmazione di Data Mining](../analysis-services/data-mining-programming.md) vengono descritti gli approcci di compilazione di soluzioni contenenti oggetti di data mining.

[Programmazione del modello multidimensionale](../analysis-services/multidimensional-models/multidimensional-model-programming.md) vengono descritte le attività di sviluppo e approcci per l'integrazione di oggetti del modello multidimensionale in una soluzione personalizzata.

[Programmazione tabulare modello 1200 a livello di compatibilità e successive](../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)
**New in SQL Server 2016**.  Vengono riepilogate le interfacce e i linguaggi di script utilizzati per l'utilizzo di modello tabulare 1200 e modelli superiori a livello di codice.

[Programmazione di modello tabulare per compatibilità livelli 1050 e 1103](../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md) questa documentazione è destinata agli sviluppatori che supportano i modelli tabulari con livelli di compatibilità precedenti. Vengono descritte le estensioni CSDL che definiscono un modello tabulare nella sintassi XML. Sono inoltre incluse informazioni sulla sintassi e le definizioni di modello a oggetti tabulari.

[Analysis Services Management Objects (AMO)](https://msdn.microsoft.com/library/mt436122.aspx) documentazione di riferimento per sviluppatori per il provider gestito, Analysis Services Management Objects (AMO) per l'amministrazione, tra cui l'elaborazione e di definizione dei dati.

[ADOMD.NET](http://msdn.microsoft.com/library/mt465769.aspx) documentazione di riferimento per sviluppatori per il provider gestito, ADOMD.NET, utilizzato per i dati a livello di codice i carichi di lavoro di accesso e la query.

[Set di righe dello Schema di Analysis Services](../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md) descrive i set di righe dello schema che forniscono informazioni sullo stato di server, le operazioni server e gli oggetti di database.

[XML for Analysis &#40;XMLA&#41; riferimento](../analysis-services/xmla/xml-for-analysis-xmla-reference.md) concetti XMLA descrive utili per comprendere come contributo di XMLA alla soluzione personalizzata. Viene inoltre descritto il livello di conformità con la specifica XMLA 1.1.

[Analysis Services Scripting Language &#40;ASSL per XMLA&#41; ](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md) vengono descritte le estensioni ASSL a XMLA. ASSL fornisce i linguaggi DDL e DML per i modelli tabulari di Analysis Services che integrano la specifica XMLA.

[Tabular Model Scripting Language &#40;TMSL&#41; riferimento](../analysis-services/tabular-model-scripting-language-tmsl-reference.md) TMSL è una rappresentazione JSON di modelli tabulari a livello di compatibilità 1200 o superiore. Le definizioni degli oggetti sono basate su costrutti di metadati tabulari come tabella, colonna e relazione piuttosto che i metadati multidimensionali che potrebbero essere poco note, se si ha esperienza di modellazione dei dati di Analysis Services in modalità tabulare.

[Analysis Services PowerShell Reference](../analysis-services/powershell/analysis-services-powershell-reference.md) documenta i cmdlet usati per le funzioni amministrative e di utilizzo generale **Invoke-ASCmd** cmdlet che accetta qualsiasi script o una query come input.

## <a name="see-also"></a>Vedere anche
[Riferimento tecnico ](../analysis-services/powershell/technical-reference-ssas.md) 
 [riferimenti al linguaggio di espressioni e Query &#40;Analysis Services&#41;](http://msdn.microsoft.com/library/gg492188.aspx)
