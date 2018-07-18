---
title: Le definizioni degli oggetti nella tabella del modello Scripting Language (TMSL) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 458f39a28295abe431be00ca59fc49d56dd29cb7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="tmsl-reference---tabular-objects"></a>Riferimento TMSL - oggetti tabulari
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Le applicazioni di creare, utilizzare o amministrare i database tabulari o che si connettono a un'istanza di SQL Server 2016 Analysis Services in modalità tabulare, è possibile utilizzare il protocollo Tabular Model Scripting Language (TMSL) per comandi e le rappresentazioni di oggetti in formato JSON.  
  
 Questo articolo sono descritti i principali oggetti dello schema TMSL utilizzati negli script generati da SQL Server Management Studio, SQL Server Data Tools (SSDT) e PowerShell per AMO.  
  
 Le definizioni degli oggetti in JSON e utilizzati in comandi TMSL come Create, Alter ed eliminare. Vedere [comandi Tabular Model Scripting Language &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md) per un elenco dei comandi.  
  
## <a name="main-objects"></a>Oggetti principali  
 Nella tabella seguente è riportato l'elenco degli oggetti più comunemente usati nello script TMSL.  
  
|||  
|-|-|  
|[Oggetto di database &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|Definisce un database tabulare con livello di compatibilità 1200 o superiore, in base a un modello dello stesso livello.|  
|[Oggetto del modello &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|Definisce un modello tabulare a livello di compatibilità 1200 o superiore.|  
|[Oggetto di origini dati &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|Definisce una connessione a un'origine dati utilizzata durante l'importazione per caricare il modello o per pass-through query quando il modello è in modalità DirectQuery.|  
|[Oggetto tabelle &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|Specifica le tabelle del modello.|  
|[Oggetto di partizioni &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|Definisce l'archiviazione dei set di righe di tabella, incluse le tabelle calcolate.|  
|[Oggetto le relazioni &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|Definisce le relazioni tra tabelle.|  
|[Oggetto di ruoli &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|Definisce le autorizzazioni, appartenenza e i filtri di sicurezza che controllano l'accesso ai dati e operazioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento al linguaggio di scripting per modelli tabulari &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
