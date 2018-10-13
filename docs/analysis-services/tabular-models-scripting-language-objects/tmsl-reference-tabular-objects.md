---
title: Le definizioni degli oggetti in tabulare modellare Scripting Language (TMSL) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: de968c32f8c00132157a5b1b7a6682adc7148446
ms.sourcegitcommit: b75fc8cfb9a8657f883df43a1f9ba1b70f1ac9fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851746"
---
# <a name="tmsl-reference---tabular-objects"></a>Informazioni di riferimento su TMSL - Oggetti tabulari
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Le applicazioni che creare, utilizzare o amministrare i database tabulari o che si connette a un'istanza di SQL Server 2016 Analysis Services in modalità tabulare, è possibile usare il TMSL Tabular Model Scripting Language () per i comandi e le rappresentazioni di oggetti in formato JSON.  
  
 Questo articolo sono descritti i principali oggetti dello schema TMSL utilizzati negli script generati da SQL Server Management Studio, SQL Server Data Tools (SSDT) e PowerShell per AMO.  
  
 Le definizioni degli oggetti sono in formato JSON e usato nei comandi TMSL, ad esempio Create, Alter e Delete. Visualizzare [comandi in Tabular Model Scripting Language &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md) per un elenco dei comandi.  
  
## <a name="main-objects"></a>Oggetti principali  
 Nella tabella seguente è riportato l'elenco degli oggetti più comunemente usati nello script TMSL.  
  
|||  
|-|-|  
|[Oggetto di database &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|Definisce un database tabulare con livello di compatibilità 1200 o superiore, basato su un modello dello stesso livello.|  
|[Oggetto del modello &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|Definisce un modello tabulare con livello di compatibilità 1200 o superiore.|  
|[Oggetto DataSources &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|Definisce una connessione a un'origine dati utilizzata durante l'importazione per caricare il modello o per pass-through query quando il modello è in modalità DirectQuery.|  
|[Oggetto Tables &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|Specifica le tabelle del modello.|  
|[Oggetto Partitions &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|Definisce l'archiviazione dei set di righe di tabella, incluse le tabelle calcolate.|  
|[Oggetto Relationships &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|Definisce le relazioni tra tabelle.|  
|[Oggetto Roles &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|Definisce le autorizzazioni, appartenenza e i filtri di sicurezza che controllano l'accesso ai dati e operazioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento al linguaggio di scripting per modelli tabulari &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
