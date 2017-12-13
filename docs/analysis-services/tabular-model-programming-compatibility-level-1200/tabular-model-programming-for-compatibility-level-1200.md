---
title: "Programmazione del modello tabulare per il livello di compatibilità 1200 | Documenti Microsoft"
ms.custom: 
ms.date: 05/30/2017
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
ms.topic: article
ms.assetid: d343f693-c800-42fe-bb4f-2c38a10919f1
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 5c7a0c3c69a8d4c834cf6a44cd3e588faed2593f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="tabular-model-programming-for-compatibility-level-1200-and-higher"></a>Tabulare modello di programmazione per la compatibilità livello 1200 e versioni successive
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]A partire da livello di compatibilità 1200, i metadati tabulari viene utilizzato per descrivere i costrutti del modello, sostituendo cronologici metadati multidimensionali come descrittori per oggetti del modello tabulare. I metadati per le tabelle, colonne e relazioni sono tabella, colonna e relazioni, anziché gli equivalenti multidimensionali (dimensione e attributo).  
  
È possibile creare nuovi modelli a livello di compatibilità 1200 o superiore tramite le APIs Microsoft.AnalysisServices.Tabular, la versione più recente di SQL Server Data Tools (SSDT), o modificando il **CompatibilityLevel** di un tabulare esistente modello per aggiornarlo (eseguita anche in SSDT). In questo modo associa il modello a versioni più recenti del server, strumenti e le interfacce di programmazione.   
  
L'aggiornamento di una soluzione tabulare esistente è consigliata ma non richiesta. Uno script esistente e soluzioni personalizzate per accedano o gestiscono i modelli tabulari o database possono essere utilizzate come-è. Livelli di compatibilità precedenti sono completamente supportati in SQL Server 2016 usando le funzionalità disponibili in tale livello. Azure Analysis Services supporta solo il livello di compatibilità 1200 e versioni successiva.
  
 Nuovi modelli tabulari verranno richiedono codice diverso e script, riepilogate di seguito.  
  
## <a name="object-model-definitions-as-tabular-metadata-constructs"></a>Definizioni dei modelli di oggetto come i costrutti di metadati tabulari  
 Il modello a oggetti tabulare per i modelli 1200 o superiori viene esposto in JSON tramite la [linguaggio di Scripting del modello tabulare](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) e il linguaggio di definizione dati AMO tramite un nuovo spazio dei nomi, [ Microsoft.AnalysisServices.Tabular](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.aspx)

## <a name="script-for-tabular-models-and-databases"></a>Script per database e i modelli tabulari  
 TMSL è un linguaggio di scripting di JSON per i modelli tabulari, con supporto per la creazione, lettura, aggiornamento, le operazioni di un'eliminazione. È possibile aggiornare i dati tramite TMSL e richiamare operazioni del database per il collegamento, dissociare, backup, ripristino e sincronizzazione.  
  
 PowerShell per AMO accetta script TMSL come input.  
  
 Vedere [Scripting Language &#40; del modello tabulare TMSL &#41; Riferimento](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) e [Analysis Services PowerShell Reference](../../analysis-services/powershell/analysis-services-powershell-reference.md) per ulteriori informazioni.  
  
## <a name="query-languages"></a>Linguaggi di query  
 DAX e MDX sono supportati per tutti i modelli tabulari.  
  
## <a name="expression-language"></a>Linguaggio delle espressioni  
 I filtri e le espressioni usate per creare oggetti calcolati, tra cui le misure e indicatori KPI, vengono formulate in DAX. Vedere [capire DAX nei modelli tabulari](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md) e [DAX Data Analysis Expressions &#40; &#41; in Analysis Services](http://msdn.microsoft.com/library/abb336c9-3346-4cab-b91b-90f93f4575e5).  
  
## <a name="managed-code-for-tabular-models-and-databases"></a>Codice gestito per database e i modelli tabulari  
 AMO include un nuovo spazio dei nomi, Microsoft.AnalysisServices.Tabular, per l'utilizzo di modelli a livello di codice. Vedere [Microsoft. AnalysisServices Namespace](https://msdn.microsoft.com/library/ms146720\(SQL.130\).aspx) per ulteriori informazioni.  
  
> [!NOTE]  
>  Le librerie client Analysis Services Management Objects (AMO), ADOMD.NET e del modello a oggetti tabulare (TOM) è ora destinato al runtime di .NET 4.0.   
  
## <a name="see-also"></a>Vedere anche  
 [Documentazione per gli sviluppatori di Analysis Services](../../analysis-services/analysis-services-developer-documentation.md)   
 [Programmazione del modello tabulare per la compatibilità 1050 1103 tramite i livelli](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)   
 [Riferimento tecnico &#40; SSAS &#41; ](../../analysis-services/powershell/technical-reference-ssas.md) [Aggiornare Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)  
 [Livelli di compatibilità dei database e i modelli tabulari](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)  
  
  
