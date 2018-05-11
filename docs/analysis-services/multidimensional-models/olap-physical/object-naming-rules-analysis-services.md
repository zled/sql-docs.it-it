---
title: Le regole di denominazione (Analysis Services) dell'oggetto | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: de44fa30f1dcb32bb4e0e847fdff5a01dd9c9a86
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="object-naming-rules-analysis-services"></a>Regole di denominazione degli oggetti (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  In questo argomento vengono descritte le convenzioni di denominazione degli oggetti, come pure le parole e i caratteri riservati che non possono essere utilizzati in nomi di oggetto, codice o script in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
##  <a name="bkmk_Names"></a> Convenzioni di denominazione  
 Ogni oggetto dispone di un **nome** e **ID** proprietà che devono essere univoci all'interno dell'ambito della raccolta padre. Ad esempio, due dimensioni possono avere lo stesso nome fintanto che ciascuna risiede in un database diverso.  
  
 Sebbene sia possibile specificare manualmente il **ID** viene in genere generato automaticamente quando viene creato l'oggetto. Non modificare mai il **ID** una volta avviata la compilazione di un modello. Tutti i riferimenti agli oggetti in un modello si basano le **ID**. Pertanto, la modifica un **ID** facilmente può causare il danneggiamento del modello.  
  
 **DataSource** e **DataSourceView** oggetti presentano eccezioni rilevanti alle convenzioni di denominazione. **Origine dati** ID può essere impostato su un punto singolo (.), che non è univoco, come un riferimento al database corrente. Una seconda eccezione è **DataSourceView**, che aderisce alle convenzioni di denominazione definite per **DataSet** oggetti in .NET Framework, in cui il **nome** viene utilizzato come il identificatore.  
  
 Le regole seguenti si applicano a **nome** e **ID** proprietà.  
  
-   Per i nomi non viene fatta distinzione tra maiuscole e minuscole. Non è possibile avere un cubo denominato "sales" e un altro denominato "Sales" nello stesso database.  
  
-   Gli spazi iniziali o finali non sono consentiti nel nome dell'oggetto, sebbene sia possibile incorporare gli spazi all'interno del nome. Gli spazi iniziali e finali vengono eliminati in modo implicito. Si applica a entrambe le **nome** e **ID** di un oggetto.  
  
-   Il numero massimo di caratteri consentito è 100.  
  
-   Non esiste alcun particolare requisito per il primo carattere di un identificatore, che può pertanto essere qualsiasi carattere valido.  
  
##  <a name="bkmk_reserved"></a> Caratteri e le parole riservate  
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
  
|Oggetto|Caratteri non validi|  
|------------|------------------------|  
|**Server**|Seguire le convenzioni di denominazione del server Windows quando si denomina un oggetto server. Vedere [convenzioni di denominazione (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms682856\(v=vs.85\).aspx) per informazioni dettagliate.|  
|**DataSource**|: / \ * &#124; ? "[] () {} <>|  
|**Livello** o **attributo**|tramite tabelle annidate. , ; ' ` : / \ * &#124; ? " & % $ ! + = [] {} < >|  
|**Dimensione** o **gerarchia**|tramite tabelle annidate. , ; ' ` : / \ * &#124; ? " & % $ ! + = [] () {} \<, >|  
|Tutti gli altri oggetti|tramite tabelle annidate. , ; ' ` : / \ * &#124; ? " & % $ ! + = [] () {} < >|  
  
 **Eccezioni: Quando i caratteri riservati consentiti**  
  
 Come indicato, i database di un livello specifico di compatibilità e modalità possono avere nomi di oggetto contenenti caratteri riservati. I nomi di oggetto KPI, misura, livello, gerarchia e attributo di dimensione possono contenere caratteri riservati per i database tabulari (1103 o superiore) che consentono l'utilizzo dei caratteri estesi:  
  
|Livello di compatibilità del database e modalità del server|Caratteri riservati consentiti?|  
|--------------------------------------------------|----------------------------------|  
|MOLAP (tutte le versioni)|no|  
|Tabulare - 1050|no|  
|Tabulare - 1100|no|  
|Tabulare - 1130 e superiore|Sì|  
  
 I database possono avere un oggetto ModelType predefinito. L'impostazione predefinita è equivalente a multidimensionale e pertanto non supporta l'utilizzo dei caratteri riservati nei nomi delle colonne.  
  
## <a name="see-also"></a>Vedere anche  
 [Parole riservate MDX](../../../mdx/mdx-reserved-words.md)   
 [Supporto delle traduzioni in Analysis Services](../../../analysis-services/translation-support-in-analysis-services.md)   
 [XML for Analysis conformità &#40;XMLA&#41;](../../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)  
  
  
