---
title: Editor di Query XMLA (Analysis Services - dati multidimensionali) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.editor.xmla.f1
helpviewer_keywords:
- XMLA Query Editor
- Query Editor [XMLA]
ms.assetid: 14623019-7839-4038-9d12-2f8953d2ec04
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 221ea55990b98a9723928f52cd5432f13760cc91
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211431"
---
# <a name="xmla-query-editor-analysis-services---multidimensional-data"></a>Editor di query XMLA (Analysis Services - Dati multidimensionali)
  Utilizzare l'Editor di query XMLA per progettare ed eseguire istruzioni e script scritti nel linguaggio MDX (XMLA).  
  
## <a name="features"></a>Funzionalità  
  
-   È possibile digitare gli script nel riquadro dell'editor di query XMLA.  
  
-   Per eseguire gli script è possibile premere **F5**oppure fare clic su **Esegui** sulla barra degli strumenti oppure scegliere **Esegui** dal menu **Query**. Se è stata selezionata una parte del codice, viene eseguita solo quella parte. Se non è stata eseguita alcuna selezione, verrà eseguito tutto il contenuto dell'editor di query XMLA.  
  
-   Consente di visualizzare metadati per cubi e altri oggetti contenuti in un database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nel riquadro dei metadati.  
  
-   Per informazioni sulla sintassi XMLA, selezionare una parola chiave nell'editor di query XMLA e quindi premere **F1**.  
  
-   Per la Guida dinamica relativa alla sintassi XMLA, scegliere **Guida dinamica** dal menu **?** per aprire il componente. Quando si usa la Guida dinamica, i relativi argomenti vengono visualizzati nella finestra di dialogo **Guida dinamica** mentre si digitano le parole chiave nell'editor di query.  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>Barra degli strumenti degli Editor di SQL Server Analysis Services  
 Quando l'editor di query XMLA è aperto, sulla barra degli strumenti **Editor di SQL Server Analysis Services** sono disponibili i pulsanti seguenti.  
  
|Nome|Definizione|  
|----------|----------------|  
|**Connect**|Consente di aprire la finestra di dialogo **Connetti al server** per stabilire una connessione a un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|  
|**Disconnetti**|Consente di disconnettere l'editor di query XMLA da un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|  
|**Cambia connessione**|Consente di aprire la finestra di dialogo **Connetti al server** per stabilire una connessione a una diversa istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|  
|**Nuova query con connessione corrente**|Consente di aprire una nuova finestra dell'editor di query XMLA utilizzando le stesse informazioni di connessione della finestra dell'editor di query XMLA corrente.|  
|**Database disponibili**|Consente di cambiare la connessione a un diverso database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nella stessa istanza.|  
|**Eseguire**|Consente di eseguire il codice selezionato o, se non è selezionata alcuna parte specifica del codice, di eseguire tutto il codice contenuto nell'editor di query XMLA.|  
|**Analizza**|Consente di controllare la sintassi del codice selezionato. Se non è selezionata alcuna parte di codice, consente di controllare la sintassi di tutto il contenuto della finestra dell'editor di query XMLA.|  
|**Annulla esecuzione query**|Consente di inviare una richiesta di annullamento al server. Alcune query non possono essere annullate immediatamente, ma devono attendere una condizione di annullamento adatta. Quando le query vengono annullate, è possibile che si verifichino ritardi durante il rollback delle transazioni.|  
  
## <a name="xmla-query-editor-window"></a>Finestra dell'editor di query XMLA  
 Nell'editor di query XMLA sono disponibili le opzioni seguenti:  
  
|Nome|Definizione|  
|----------|----------------|  
|**Finestra dell'editor di query**|Consente di digitare istruzioni e script XMLA da eseguire mediante l'editor di query XMLA.<br /><br /> Nel menu di scelta rapida dell'editor di query sono disponibili le opzioni seguenti:<br /><br /> **Taglia**: copia la selezione corrente negli Appunti e rimuove la selezione dalla finestra dell'editor di query.<br />**Copy**: copia la selezione corrente negli Appunti.<br />**Incolla**: Incolla il contenuto degli Appunti nella selezione corrente.<br />**Connetti**: apre la finestra di dialogo **Connetti al server**, per stabilire una connessione a un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].<br />**Disconnettere**: disconnette l'editor di query corrente da un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] istanza.<br />**Disconnetti tutte le query**: disconnette tutti gli editor di query aperta.<br />**Cambia connessione**: consente di aprire la **Connetti al Server** della finestra di dialogo per stabilire una connessione a un altro [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] istanza.<br />**Apri Server in Esplora oggetti**: consente di aprire la [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] istanza a cui è connesso l'editor di query corrente in **Esplora oggetti**.<br />**Eseguire**: esegue il codice selezionato oppure se è selezionato alcun codice, esegue tutto il codice nell'editor di query corrente.<br />**Finestra delle proprietà**: consente di visualizzare il **delle proprietà** finestra in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per la finestra di query corrente.<br />**Opzioni query**: consente di visualizzare il **le opzioni di Query** nella finestra di dialogo.|  
|**Finestra dei risultati**|Consente di visualizzare i risultati di un'istruzione o di uno script XMLA in formato testo.|  
|**Finestra dei messaggi**|Consente di visualizzare informazioni sull'esecuzione di un'istruzione o di uno script XMLA. Ad esempio, in questa finestra vengono visualizzati gli eventuali errori rilevati durante l'esecuzione o il numero di celle recuperate dopo l'esecuzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Editor di Query MDX &#40;Analysis Services - dati multidimensionali&#41;](mdx-query-editor-analysis-services-multidimensional-data.md)   
 [Editor di Query DMX &#40;Analysis Services - Data Mining&#41;](dmx-query-editor-analysis-services-data-mining.md)   
 [Progettazione query e gli editor di testo &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)   
 [Tasti di scelta rapida di SQL Server Management Studio](../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
  
  
