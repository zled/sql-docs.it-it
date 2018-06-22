---
title: Esempio di file di input XML con configurazione specificata dall'utente (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: b29c9716-e5c3-4003-9efb-3ade2197b630
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 933cae8582f104d9c70e608ab30ee938c8674175
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065724"
---
# <a name="xml-input-file-sample-with-user-specified-configuration-dta"></a>Esempio di file di input XML con configurazione specificata dall'utente (DTA)
  Copiare e incollare questo esempio di file di input XML che contiene una configurazione specificata dall'utente con l'elemento **Configuration** nell'editor di testo o nell'editor XML preferito. In questo modo sarà possibile eseguire analisi di simulazione che comportano l'uso dell'elemento **Configuration** per specificare un set di strutture di progettazione fisica ipotetiche per il database che si vuole ottimizzare. Per sapere se è possibile migliorare le prestazioni di elaborazione delle query, verrà quindi utilizzata l'Ottimizzazione guidata motore di database per analizzare gli effetti dell'esecuzione di un carico di lavoro rispetto a questa configurazione ipotetica. Questo tipo di analisi ha il vantaggio di valutare la nuova configurazione senza l'overhead dovuto all'effettiva implementazione. Se la configurazione ipotetica non consente di ottenere i miglioramenti delle prestazioni desiderati, è possibile modificarla e analizzarla di nuovo finché non verranno prodotti i risultati necessari.  
  
 Dopo avere copiato questo esempio nello strumento di modifica desiderato, sostituire i valori specificati per gli elementi **Server**, **Database**, **Schema**, **Table**, **Workload**, **TuningOptions**e **Configuration** con i valori per la sessione di ottimizzazione specifica. Per altre informazioni su tutti gli attributi e gli elementi figlio che è possibile usare con questi elementi, vedere [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md). Nell'esempio seguente viene utilizzato solo un subset delle opzioni relative agli attributi e agli elementi figlio disponibili.  
  
## <a name="code"></a>codice  
 [!code-xml[InputFileSamples#UserSpecifiedConfigInputFile](../../snippets/xml/SQL14/dta_xml/inputfilesamples/xml/dta_xml_input_file_samples.xml#userspecifiedconfiginputfile)]  
  
## <a name="comments"></a>Commenti  
  
-   L'eliminazione di strutture di progettazione fisica non è supportata se si specifica la modalità **Absolute** per l'elemento **Configuration** (`Configuration SpecificationMode="Absolute"`).  
  
-   La stessa struttura di progettazione fisica non può essere creata ed eliminata in modalità**Relative** o **Absolute**dell'elemento **Configuration** .  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e utilizzo di Ottimizzazione guidata motore di database](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)   
 [Visualizzare e utilizzare l'output di Ottimizzazione guidata motore di database](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)   
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  