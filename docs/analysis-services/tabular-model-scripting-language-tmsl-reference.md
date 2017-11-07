---
title: Scripting Language (TMSL) riferimento del modello tabulare | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c700d7f8-7e01-4052-a9ad-8200dd4009f2
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 875dd29a77a341e3d40502002488fc0189947c9d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="tabular-model-scripting-language-tmsl-reference"></a>Scripting Language (TMSL) riferimento del modello tabulare

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

  Tabular Model Scripting Language (TMSL) è la sintassi di definizione del modello di comando e oggetti per i database modello tabulare di Analysis Services a livello di compatibilità 1200 o superiore. TMSL comunica con Analysis Services tramite il protocollo XMLA, in cui il [XMLA. Eseguire](../analysis-services/xmla/xml-elements-methods-execute.md) metodo accetta sia basata su JSON **istruzione** script TMSL, nonché gli script tradizionale basato su XML in [Analysis Services Scripting Language &#40; ASSL per XMLA &#41; ](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
 Gli elementi chiave del linguaggio TMSL, tra cui:  
  
-   Metadati tabulari basato sulla semantica di modello tabulare. Un modello tabulare è composta da tabelle, colonne e relazioni. Oggetto equivalente definizioni TMSL sono ora, ovviamente, tabelle, colonne, relazioni e così via.  
  
     Un nuovo motore di metadati supporta le definizioni.  
  
-   Le definizioni degli oggetti sono strutturati come JSON anziché XML.  
  
 Fatta eccezione per il payload è in formato (JSON o XML), TMSL sia ASSL sono funzionalmente equivalenti in modo forniscono comandi e i metadati per i metodi XMLA utilizzati per il trasferimento di comunicazioni e i dati di server.  
  
## <a name="how-to-use-tmsl"></a>Come usare TMSL  
 Il modo più semplice per esplorare gli script TMSL Usa i comandi CREATE, ALTER, DELETE o processo in SQL Server Management Studio (SSMS) su un modello che già noti. Se che si utilizza un modello esistente, è necessario aggiornarlo al livello di compatibilità 1200 o superiore.  
  
1.  Trovare il comando di cui si desidera utilizzare: [comandi nel linguaggio di Scripting del modello tabulare &#40; TMSL &#41;](../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md)  
  
2.  Verificare il riferimento di definizione di oggetto per gli oggetti usati nel comando: [definizioni di oggetti nel linguaggio di Scripting del modello tabulare &#40; TMSL &#41;](../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md)  
  
3.  Scegliere un metodo per l'invio di script TMSL:  
  
    -   Finestra XMLA in Management Studio  
  
    -   **Invoke-ascmd** tramite AMO PowerShell ([cmdlet Invoke-ASCmd](../analysis-services/powershell/invoke-ascmd-cmdlet.md))  
  
    -   [Analysis Services attività Esegui DDL](../integration-services/control-flow/analysis-services-execute-ddl-task.md) in SSIS.  
  
## <a name="model-definition-schema"></a>Schema di definizione del modello  
 La schermata seguente mostra una versione abbreviata di schema, compressa per visualizzare gli oggetti principali.  
  
 ![SSAS_TabularMetadata](../analysis-services/media/ssas-tabularmetadata.JPG "SSAS_TabularMetadata")  
  
## <a name="scripting-languages-in-analysis-services"></a>Linguaggi di scripting in Analysis Services  
 Analysis Services supporta i linguaggi di script ASSL e TMSL. Solo i modelli tabulari creati a livello di compatibilità 1200 o superiore sono descritte nel TMS in formato JSON.  
  
 [Analysis Services Scripting Language &#40; ASSL per XMLA &#41; ](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md) è il linguaggio di script prima e che sia ancora il linguaggio di script solo per i modelli multidimensionali e modelli tabulari con livelli di compatibilità inferiore (1100 o 1103). In ASSL, i modelli tabulari a x 110 sono descritti in termini di multidimensionali, ad esempio **cubo** (per un modello) e **measuregroup** (per una tabella).  
  
> [!NOTE]  
>  In [SQL Server Data Tools (SSDT), è possibile aggiornare un modello tabulare versione precedente per l'utilizzo di TMSL passando i relativi **CompatibilityLevel** su 1200 o superiore. Tenere presente che l'aggiornamento è irreversibile. Prima dell'aggiornamento, eseguire il backup del modello nel caso in cui è necessaria la versione originale in un secondo momento.  
  
 Nella tabella seguente è la matrice di linguaggio di scripting per i modelli di dati di Analysis Services tra le diverse versioni, a livello di compatibilità specifico.  

||||||  
|-|-|-|-|-|  
|**Version**|**Multidimensionale**|**Tabulari 110x**|**Tabulari 1200**| **1400 tabulare** |
|Azure Analysis Services|ND|ND|TMSL|TMSL| 
|SQL Server 2017|ASSL|ASSL|TMSL|TMSL| 
|SQL Server 2016|ASSL|ASSL|TMSL|TMSL| 
|SQL Server 2014|ASSL|ASSL|ND|ND|   
|SQL Server 2012|ASSL|ASSL|ND|ND|  

  
## <a name="see-also"></a>Vedere anche  
 [Livello di compatibilità per i modelli tabulari in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Analysis Services Scripting Language &#40; ASSL per XMLA &#41;](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [Determinare la modalità server di un'istanza di Analysis Services](../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  

