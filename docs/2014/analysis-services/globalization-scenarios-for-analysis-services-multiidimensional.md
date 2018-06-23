---
title: Scenari di globalizzazione per Analysis Services multidimensionale | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- multiple language support [Analysis Services]
- languages [Analysis Services]
- SSAS, international considerations
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- SQL Server Analysis Services, international considerations
- Analysis Services, international considerations
ms.assetid: e8af85ff-ef33-4659-a003-bb34578eb2a2
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5d45b44c6536a7fc95543bebdbc9468c61fdf75b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171126"
---
# <a name="globalization-scenarios-for-analysis-services-multiidimensional"></a>Scenari di globalizzazione per Analysis Services multidimensionale
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Archivia e gestisce dati e metadati in entrambi i modelli tabulari e multidimensionali dati multilingue. L'archiviazione dei dati è in formato Unicode (UTF-16) nei set di caratteri che usano la codifica Unicode. Se in un modello di dati si caricano dati ANSI, i caratteri vengono archiviati usando elementi di codice Unicode equivalenti.  
  
 Le implicazioni del supporto Unicode consentono a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] di archiviare i dati in una qualsiasi lingua supportata dai sistemi operativi client e server Windows, permettendo la lettura, la scrittura, l'ordinamento e il confronto dei dati in qualsiasi set di caratteri usato in un computer Windows. Le applicazioni client BI che utilizzano i dati di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] possono rappresentare i dati nella lingua scelta dall'utente, supponendo che i dati esistano in tale lingua nel modello.  
  
 Il supporto della lingua può avere diversi significati a seconda degli utenti. L'elenco seguente risponde ad alcune domande comuni relative al modo in cui Analysis Services supporta le lingue.  
  
-   I dati, come già indicato, vengono archiviati in un qualsiasi set di caratteri con codifica Unicode presente in un sistema operativo client Windows.  
  
-   Anche i metadati, ad esempio nomi di oggetti, identificatori e descrizioni, possono essere in qualsiasi alfabeto e lingua Unicode. Ciò vale anche quando gli strumenti e l'ambiente sono in un'altra lingua. Ad esempio, in un ambiente di sviluppo che usa la lingua inglese e le regole di confronto in caratteri latini in tutto lo stack, è possibile includere nel modello un oggetto che usa caratteri cirillici nel nome.  
  
     Solo per i modelli multidimensionali, le didascalie e i membri dell'attributo possono essere espressi come traduzioni. È possibile definire una o più traduzioni e quindi usare un identificatore delle impostazioni locali per determinare la traduzione che viene restituita al client. Per altre informazioni, vedere la sezione [Funzionalità](#bkmk_features) di seguito.  
  
-   Errore, avviso e messaggi informativi restituiti dal [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] motore (msmdsrv) sono localizzati in 43 lingue supportate da Office e Office 365. Per ricevere i messaggi in una lingua specifica non è necessaria alcuna configurazione. Le impostazioni locali dell'applicazione client determinano quali stringhe vengono restituite.  
  
-   I file di configurazione (msmdsrv.ini) e PowerShell per AMO sono disponibili solo in lingua inglese.  
  
-   I file di log conterranno un insieme di messaggi localizzati e in lingua inglese, supponendo che sia stato installato un Language Pack nel server Windows in cui viene eseguito Analysis Services.  
  
-   La documentazione e gli strumenti, ad esempio [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] e [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)], sono tradotti nelle lingue seguenti: cinese semplificato, cinese tradizionale, francese, tedesco, italiano, giapponese, coreano, portoghese (Brasile), russo e spagnolo. Per utilizzare una versione specifica della lingua degli strumenti, installare una versione specifica della lingua di SQL Server (ad esempio, installare la versione tedesca di SQL Server Management Studio in tedesco) oppure eseguire il programma di installazione autonomo nella lingua di destinazione per [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)].  
  
 Analysis Services consente di impostare la lingua, le regole di confronto e le traduzioni in modo indipendente in tutta la gerarchia degli oggetti.  
  
 Gli scenari abilitati tramite lingua, regole di confronto e traduzioni includono:  
  
-   Un unico modello di dati fornisce più didascalie tradotte in modo che i nomi dei campi e i valori vengano visualizzati nella lingua scelta dall'utente. Per le società che operano in paesi bilingue come Canada, Belgio o Svizzera, il supporto di più lingue nelle applicazioni client e server è un requisito di codifica standard. Questo scenario viene abilitato tramite traduzioni e conversioni di valuta. Per altre informazioni e collegamenti, vedere la sezione [Funzionalità](#bkmk_features) di seguito.  
  
-   Gli ambienti di sviluppo e di produzione sono posizionati geograficamente in diversi paesi. È sempre più comune sviluppare una soluzione in un paese e quindi distribuirla in un altro. È essenziale sapere impostare le proprietà della lingua e delle regole di confronto se occorre preparare una soluzione sviluppata in una lingua, per distribuirla in un server che usa un altro Language Pack. L'impostazione di queste proprietà consente di eseguire l'override delle impostazioni predefinite ereditate che vengono recuperate dal sistema host originale. Per altre informazioni, vedere la sezione [Languages and Collations &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md) per informazioni dettagliate sull'impostazione delle proprietà.  
  
##  <a name="bkmk_features"></a> Funzionalità per la creazione di una soluzione multidimensionale globalizzata  
 [!INCLUDE[applies](../includes/applies-md.md)] Solo i modelli di dati multidimensionali  
  
 A livello di client, le applicazioni globalizzate che utilizzano o manipolare [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dati multidimensionali è possono utilizzare le funzionalità multilingue e multiculturali in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]:  
  
-   [Le traduzioni &#40;Analysis Services&#41; ](translations-analysis-services.md) consentono di incorporare più didascalie per un singolo oggetto, dove ogni stringa tradotta può coesistere con altre traduzioni. È possibile usare [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] per definire le traduzioni per la didascalia, la descrizione e i tipi di account per cubi, misure, dimensioni e attributi. È possibile recuperare i dati e i metadati dagli oggetti di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in cui le traduzioni sono state definite automaticamente fornendo un identificatore delle impostazioni locali quando si esegue la connessione a un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
     Una lezione su come usare questa funzionalità è disponibile nella [Lezione 9: Definizione di prospettive e traduzioni](lesson-9-defining-perspectives-and-translations.md) dell'esercitazione su [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   [Conversioni di valuta &#40;Analysis Services&#41; ](currency-conversions-analysis-services.md) viene eseguita tramite script MDX specializzati che convertono le misure contenenti dati di valuta. È possibile usare la Configurazione guidata funzionalità di Business Intelligence in [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] per generare uno script MDX che utilizzi una combinazione di dati e metadati di dimensioni, attributi e gruppi di misure per la conversione di misure contenenti dati di valuta.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Lingue e regole di confronto &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md)|Specifica la lingua predefinita e le regole di confronto di Windows per un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Le scelte influiscono sui dati e metadati gestiti da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|  
|[Le traduzioni &#40;Analysis Services&#41;](translations-analysis-services.md)|Definire le traduzioni per un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database e gli oggetti contenuti nel database. Questo argomento illustra come [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] risolve le richieste di dati e metadati tradotti da parte delle applicazioni client.|  
|[Conversioni di valuta &#40;Analysis Services&#41;](currency-conversions-analysis-services.md)|Definisce una conversione di valuta usando la Configurazione guidata funzionalità di Business Intelligence.|  
|[Suggerimenti e procedure consigliate per la globalizzazione &#40;Analysis Services&#41;](globalization-tips-and-best-practices-analysis-services.md)|Analizza diverse procedure di progettazione e codifica che consentono di evitare i problemi correlati ai dati multilingue.|  
  
## <a name="see-also"></a>Vedere anche  
 [Internazionalizzazione delle applicazioni Windows](http://msdn.microsoft.com/library/windows/desktop/dd318661%28v=vs.85%29.aspx)   
 [Vai Developer Center sulla globalizzazione](http://msdn.microsoft.com/goglobal/bb871628.aspx)   
 [Scrittura Windows di App Store con progettazione adattiva basata sulle impostazioni locali](http://blogs.windows.com/buildingapps/2014/03/06/writing-windows-store-apps-with-locale-based-adaptive-design/)   
 [Lo sviluppo di applicazioni Windows universali con c# e XAML](http://www.microsoftvirtualacademy.com/training-courses/developing-universal-windows-apps-with-c-and-xaml)  
  
  