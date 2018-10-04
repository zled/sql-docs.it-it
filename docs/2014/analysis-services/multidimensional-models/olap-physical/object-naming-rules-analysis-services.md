---
title: Oggetto le regole di denominazione (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], naming
ms.assetid: b338a60d-4802-4b68-862a-6dc6a3f75e48
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: abe054c97e13ffe5428eddfded09fa18b5060aa3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48063391"
---
# <a name="object-naming-rules-analysis-services"></a>Regole di denominazione degli oggetti (Analysis Services)
  In questo argomento vengono descritte le convenzioni di denominazione degli oggetti, come pure le parole e i caratteri riservati che non possono essere utilizzati in nomi di oggetto, codice o script in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
##  <a name="bkmk_Names"></a> Convenzioni di denominazione  
 Ogni oggetto dispone di una proprietà `Name` e `ID` che deve essere univoca nell'ambito della raccolta padre. Ad esempio, due dimensioni possono avere lo stesso nome fintanto che ciascuna risiede in un database diverso.  
  
 Sebbene sia possibile specificarla manualmente, la proprietà `ID` viene di solito generata automaticamente quando viene creato l'oggetto. Si consiglia di non modificare mai la proprietà `ID` una volta avviata la compilazione di un modello. Tutti i riferimenti a un oggetto in un modello si basano sulla proprietà `ID`. Pertanto, la modifica di una proprietà `ID` può danneggiare facilmente il modello.  
  
 Gli oggetti `DataSource` e `DataSourceView` presentano eccezioni rilevanti alle convenzioni di denominazione. L'ID `DataSource` può essere impostato su un punto singolo (.), che non è univoco, come riferimento al database corrente. Una seconda eccezione è `DataSourceView`, che aderisce alle convenzioni di denominazione definite per gli oggetti `DataSet` in .NET Framework, dove la proprietà `Name` viene utilizzata come identificatore.  
  
 Le regole seguenti si applicano alle proprietà `Name` e `ID`.  
  
-   Per i nomi non viene fatta distinzione tra maiuscole e minuscole. Non è possibile avere un cubo denominato "sales" e un altro denominato "Sales" nello stesso database.  
  
-   Gli spazi iniziali o finali non sono consentiti nel nome dell'oggetto, sebbene sia possibile incorporare gli spazi all'interno del nome. Gli spazi iniziali e finali vengono eliminati in modo implicito. Si applica a entrambe le proprietà `Name` e `ID` di un oggetto.  
  
-   Il numero massimo di caratteri consentito è 100.  
  
-   Non esiste alcun particolare requisito per il primo carattere di un identificatore, che può pertanto essere qualsiasi carattere valido.  
  
##  <a name="bkmk_reserved"></a> Caratteri e parole riservate  
 Le parole riservate sono in inglese e si applicano ai nomi di oggetto, non alle didascalie. Se inavvertitamente si utilizza una parola riservata nel nome di un oggetto, viene restituito un errore di convalida. Per i modelli di data mining e multidimensionali, le parole riservate descritte di seguito non possono mai essere utilizzate in un nome di oggetto.  
  
 Per i modelli tabulari, per cui la compatibilità del database è impostata su 1103, le regole di convalida sono meno restrittive per alcuni oggetti, senza la conformità ai requisiti di caratteri estesi e alle convenzioni di denominazione di alcune applicazioni client. I database che soddisfano questi criteri sono soggetti a regole di convalida meno restrittive. In questo caso, è possibile includere in un nome di oggetto un carattere limitato e passare la convalida.  
  
 **Parole riservate**  
  
-   AUX  
  
-   CLOCK$  
  
-   COM1 tramite COM9 (COM1, COM2, COM3 e così via)  
  
-   CON  
  
-   LPT1 tramite LPT9 (LPT1, LPT2, LPT3 e così via)  
  
-   NUL  
  
-   PRN  
  
-   Non è consentito utilizzare NULL come carattere in una stringa all'interno del frammento XML  
  
 **Caratteri riservati**  
  
 Nella tabella seguente sono elencati i caratteri non validi per oggetti specifici.  
  
|Object|Caratteri non validi|  
|------------|------------------------|  
|`Server`|Seguire le convenzioni di denominazione del server Windows quando si denomina un oggetto server. Visualizzare [convenzioni di denominazione (Windows)](/windows/desktop/DNS/naming-conventions) per informazioni dettagliate.|  
|`DataSource`|: / \ * &#124; ? "[] () {} <>|  
|`Level` o `Attribute`|. , ; ' ` : / \ * &#124; ? " & % $ ! + = [] {} \< >|  
|`Dimension` o `Hierarchy`|. , ; ' ` : / \ * &#124; ? " & % $ ! + = [] () {} \<, >|  
|Tutti gli altri oggetti|. , ; ' ` : / \ * &#124; ? " & % $ ! + = () [] {} \< >|  
  
 **Eccezioni: Quando sono consentiti i caratteri riservati**  
  
 Come indicato, i database di un livello specifico di compatibilità e modalità possono avere nomi di oggetto contenenti caratteri riservati. I nomi di oggetto KPI, misura, livello, gerarchia e attributo di dimensione possono contenere caratteri riservati per i database tabulari (1103 o superiore) che consentono l'utilizzo dei caratteri estesi:  
  
|Livello di compatibilità del database e modalità del server|Caratteri riservati consentiti?|  
|--------------------------------------------------|----------------------------------|  
|MOLAP (tutte le versioni)|no|  
|Tabulare - 1050|no|  
|Tabulare - 1100|no|  
|Tabulare - 1130 e superiore|Sì|  
  
 I database possono avere un oggetto ModelType predefinito. L'impostazione predefinita è equivalente a multidimensionale e pertanto non supporta l'utilizzo dei caratteri riservati nei nomi delle colonne.  
  
## <a name="see-also"></a>Vedere anche  
 [Parole riservate MDX](/sql/mdx/mdx-reserved-words)   
 [Le traduzioni &#40;Analysis Services&#41;](../../../analysis-services/translations-analysis-services.md)   
 [XML for Analysis conformità &#40;XMLA&#41;](../../xmla/xml-for-analysis-compliance-xmla.md)  
  
  
