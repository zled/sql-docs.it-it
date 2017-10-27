---
title: Personalizzare la web part Visualizzatore Report | Documenti Microsoft
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 38f23cf5d75c47be55e1820a4421a507a73df54e
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="customize-the-report-viewer-web-part"></a>Personalizzare la web part Visualizzatore Report

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

È possibile utilizzare la web part Visualizzatore Report per visualizzare i report eseguiti in un server di report configurato per l'integrazione con SharePoint. I report che è possibile visualizzare includo file di definizione dei report, con estensione rdl, e report di Generatore report. I report vengono automaticamente aperti nella web part Visualizzatore Report in una nuova pagina, ma è anche possibile aggiungere una web part Visualizzatore Report a una pagina web esistente o un sito se desideri che un determinato report in modo che siano sempre visibili nella pagina.

> [!NOTE]
> Sebbene abbiano lo stesso nome, il Visualizzatore Report di web part che viene installato tramite il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aggiuntivo è diversa dalla web part Visualizzatore Report inclusa nel file RSWebParts.cab. Le istruzioni in questo argomento sono specificamente per la web part di Visualizzatore Report installata tramite il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aggiuntivo.

 È possibile personalizzare la web part Visualizzatore Report nei modi seguenti:  
  
-   Modificare l'aspetto della web part impostando le proprietà.  
  
-   Scegliere le caratteristiche di report interattive disponibili sull'apposita barra degli strumenti.  
  
-   Specificare quali aree di visualizzazione rendere disponibili. La web part Visualizzatore Report dispone di un'area di visualizzazione di report, un'area dei parametri e un'area credenziali.  
  
 Non è possibile estendere la web part di Visualizzatore Report per supportare diversi tipi di file e non è possibile sostituire la barra degli strumenti report con una barra degli strumenti personalizzata o aggiungere nuove funzionalità per la barra degli strumenti esistente. Se è necessaria la personalizzazione delle funzionalità standard, è necessario creare una parte web personalizzato.  

## <a name="setting-web-part-properties"></a>Impostazione delle proprietà delle web part

 Una web part include proprietà personalizzate che consentono di configurare funzionalità specifiche. Una web part dispongono inoltre di proprietà comuni che sono standard per tutte le web part.  
  
### <a name="change-default-properties"></a>Modificare le proprietà predefinite

 La web part Visualizzatore Report ha proprietà predefinite che sono la soluzione ideale per l'apertura di report su richiesta da una raccolta o cartella. Per impostazione predefinita, vengono visualizzati tutti i controlli disponibili sulla barra degli strumenti e altezza e larghezza vengono impostate per utilizzare tutto lo spazio disponibile nella pagina web. Se si desidera modificare le proprietà predefinite, è possibile personalizzare la web part tramite **Impostazioni sito**.  
  
1.  Scegliere **Impostazioni sito** dal menu **Azioni sito**.  
  
2.  In raccolte fare clic su **web part**.  
  
3.  Fare clic su **ReportViewer.dwp**.  
  
4.  Aprire il riquadro degli strumenti e impostare le proprietà che si desidera utilizzare.  
  
### <a name="customize-an-embedded-report-viewer-in-a-web-page"></a>Personalizzare un visualizzatore di Report incorporati in una pagina web

 È possibile impostare proprietà per adattare il Visualizzatore di Report all'interno di una pagina web. Al visualizzatore possono essere applicati lo stesso stile e gli stessi colori della pagina che lo contiene. È possibile nascondere completamente o in parte la barra degli strumenti, la mappa documento e l'area dei parametri per sfruttare al massimo l'area di visualizzazione del report all'interno dello spazio assegnato. Il report utilizza sempre gli stili definiti al momento della sua creazione. Non è possibile personalizzare l'aspetto del report dopo la pubblicazione in una raccolta di SharePoint.  
  
 Se si intende incorporare la web part Visualizzatore Report in una pagina web, è necessario impostare il **URL del Report** proprietà a un determinato report. In caso contrario, nel Visualizzatore report verranno visualizzate le istruzioni per il collegamento di un report. Non è possibile personalizzare o rimuovere le istruzioni.  
  
### <a name="custom-properties-of-the-report-viewer-web-part"></a>Proprietà personalizzate della web part Visualizzatore Report

 Quando si impostano le proprietà personalizzate, tenere presente che alcune proprietà vengono utilizzate solo quando la web part Visualizzatore Report è incorporata in una pagina. Tra le proprietà personalizzabili ci sono il titolo, l'altezza, la larghezza, il tipo di colore e la zona. Altre proprietà, ad esempio le impostazioni relative alla barra degli strumenti e le impostazioni relative ai parametri, vengono utilizzate indipendentemente dal fatto che Visualizzatore report sia incorporato in una pagina o apra un report in modalità Pagina intera.  
  
 Le proprietà personalizzate della web part Visualizzatore Report sono elencate di seguito.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|Report|Percorso completo di un report presente nel sito di SharePoint corrente oppure in un sito disponibile nella stessa farm o applicazione Web. Se si desidera impostare proprietà aggiuntive, per ottenere risultati ottimali fare clic su Applica dopo avere specificato l'URL del report.|  
|Destinazione collegamento ipertestuale|Codice HTML standard che specifica il frame di destinazione per la visualizzazione dei contenuti collegati nel documento corrente. Per i report che includono collegamenti ipertestuali a siti Web esterni, è possibile specificare se un documento di destinazione sostituisce il report esistente nella finestra corrente oppure viene aperto in una nuova finestra del browser. I valori validi includono **_Top**, **_Blank**e **_Self**. **_Top** usa la finestra corrente, **_Blank** carica il documento in una nuova finestra del browser e **_Self** apre il documento nel frame corrente. Sebbene **Parent** è un valore valido per l'attributo di destinazione in formato HTML, utilizzare tale valore per una web part Visualizzatore Report è incorporata in una pagina.|  
|Generazione automatica di web part di titolo|Titolo generato che include il nome della web part Visualizzatore Report seguito dal nome del report, separati da un trattino. Se il report non ha titolo, verrà utilizzato il nome di file del report. Il titolo è visibile quando si aggiunge una web part a una pagina. Se questa casella di controllo è selezionata, il titolo verrà generato a ogni aggiornamento della pagina.|  
|Generazione automatica dell'interfaccia web part Collegamento dettagli per il titolo|Un collegamento ipertestuale generato automaticamente visualizzato di sopra della web part. È possibile fare clic sul collegamento per aprire il report in una nuova pagina, in modalità Pagina intera.|  
|Mostra voce di menu Generatore report|Visualizza o nasconde l'opzione del menu **Azioni** che consente di aprire Generatore report.|  
|Mostra voce di menu di sottoscrizione|Visualizza o nasconde l'opzione del menu **Azioni** che consente di creare una sottoscrizione per il report.|  
|Mostra voce di menu di stampa|Visualizza o nasconde l'opzione del menu **Azioni** che consente di stampare il report.|  
|Mostra voce di menu di esportazione|Visualizza o nasconde l'opzione del menu **Azioni** che consente di esportare il report.|  
|Mostra pulsante di aggiornamento|Visualizza o nasconde il pulsante di aggiornamento sulla barra degli strumenti.|  
|Mostra controlli per la navigazione tra le pagine|Visualizza o nasconde i pulsanti per la navigazione nel report sulla barra degli strumenti. Questa opzione consente di modificare la visibilità di tutti i controlli per la navigazione.|  
|Mostra pulsante Indietro|Visualizza o nasconde il pulsante Indietro sulla barra degli strumenti.|  
|Mostra controlli di ricerca|Visualizza o nasconde i controlli di ricerca sulla barra degli strumenti. I controlli di ricerca consentono a un utente di cercare testo nel report di cui è stato eseguito il rendering. Questa opzione consente di modificare la visibilità di tutti i controlli di ricerca.|  
|Mostra controllo zoom|Visualizza o nasconde il controllo zoom sulla barra degli strumenti.|  
|Mostra pulsante feed ATOM|Visualizza o nasconde il pulsante del feed ATOM sulla barra degli strumenti.<br /><br /> ![htmlviewer_datafeed](../../reporting-services/media/htmlviewer-datafeed.gif "htmlviewer_datafeed")|  
|Posizione barra degli strumenti|Determina la posizione della barra degli strumenti all'interno del visualizzatore di report. I valori validi includono **Top** e **Bottom**.|  
|Area dei messaggi di richiesta|I valori validi includono **Visualizzato**, **Compresso**e **Nascosto**. **Visualizzato** consente di visualizzare l'area Parametri per i report che includono valori con parametri e richiedono l'input dell'utente prima dell'esecuzione. Usare **Hidden** se tutti i parametri del report sono specificati e non si vuole visualizzare l'area relativa.|  
|Larghezza area parametri|È possibile specificare l'unità di misura e il valore. Il valore predefinito è 200 pixel. L'unico requisito per questa proprietà è che il valore sia maggiore di zero.|  
|Mappa documento|Controllo per la navigazione del report che viene definito nel report e consente di accedere con un clic a sezioni specifiche del report. È disponibile nei report HTML. La mappa documento è visualizzata in un'area comprimibile accanto all'area di visualizzazione del report. I valori validi includono **Visualizzato**, **Compresso**e **Nascosto**. Se una mappa documento viene definita per un report, l'area viene espanso per impostazione predefinita, a meno che non contrassegnata come nascosta o compressa nelle proprietà di web part. Se la mappa documento è compressa, sarà possibile fare clic sulla freccia per espanderla.|  
|Larghezza area mappa documento|È possibile specificare l'unità di misura e il valore. Il valore predefinito è 200 pixel. L'unico requisito per questa proprietà è che il valore sia maggiore di zero.|  
|Carica parametri|Consente di recuperare le proprietà dei parametri per il report. Non tutti i report utilizzano parametri. Se il report non dispone di parametri, non verrà restituito alcun valore. Mentre si impostano le proprietà per un report appena caricato, è possibile che venga visualizzato un errore per segnalare che la connessione all'origine dei dati è stata eliminata. In questo caso, reimpostare la connessione e quindi completare l'impostazione delle proprietà dei parametri, dopo aver specificato la connessione. Per ulteriori informazioni su come impostare la connessione, vedere [crea e Gestisci origini dati condivise &#40; Reporting Services in SharePoint integrata modalità &#41; ](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76).<br /><br /> Per ottenere risultati ottimali, fare clic su **Applica** prima di fare clic su Carica parametri.<br /><br /> Dopo il caricamento delle proprietà dei parametri, è possibile impostarle come avviene normalmente nella pagina delle proprietà dei parametri del report. Per ulteriori informazioni su come impostare i parametri, vedere [imposta parametri in un Report pubblicato &#40; Reporting Services in SharePoint integrata modalità &#41; ](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).|  

## <a name="customizing-the-toolbar"></a>Personalizzare la barra degli strumenti

 La barra degli strumenti è visualizzata sotto il titolo e si estende nella parte superiore del report. Include il menu **Azioni** , oltre a controlli per la navigazione dei report impaginati, l'aggiornamento e lo zoom. È disponibile anche un controllo mappa documento per i report che dispongono di una mappa documento. Nel menu **Azioni** sono disponibili comandi per l'esportazione del report, la ricerca di testo o numeri nel report, la stampa del report e l'apertura del report in Generatore report.  
  
 Non è possibile aggiungere nuovi comandi al menu  **Azioni** , ma è possibile personalizzare il menu modificando le opzioni visibili agli utenti. Per modificare la visibilità dei pulsanti della barra degli strumenti e controlli, si modificano le opzioni di **visibilità degli elementi della barra degli strumenti** sezione della web part. È inoltre possibile rimuovere il comando **Stampa** o formati di esportazione specifici, rendendo non disponibili tali caratteristiche sul server di report. I controlli per la navigazione tra le pagine sono disponibili solo per i report che includono interruzioni di pagina. In caso contrario il report è costituito da una singola pagina di lunghezza variabile. Il pulsante**Aggiorna** consente di rielaborare il report usando i parametri correnti. Per visualizzare tutti i controlli su una riga, impostare la larghezza complessiva della web part su almeno 400 pixel.  

## <a name="customizing-the-viewing-area"></a>Personalizzazione dell'area di visualizzazione

 L'area di visualizzazione viene utilizzata per la visualizzazione dei report ed è condivisa con le aree Parametri e Credenziali, se vengono utilizzate. Se è necessario immettere credenziali, verrà visualizzata un'area di visualizzazione report vuota con accanto l'area Credenziali. Tale area viene chiusa dopo l'immissione delle credenziali e l'avvio del report. Il testo visualizzato per richiedere l'impostazione delle credenziali può essere personalizzato modificando le proprietà di connessione all'origine dei dati. Per ulteriori informazioni, vedere [crea e Gestisci origini dati condivise &#40; Reporting Services in SharePoint integrata modalità &#41; ](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76).  
  
 L'area Parametri contiene alcuni campi in cui è possibile immettere valori prima dell'esecuzione del report e viene utilizzata solo se la definizione del report include parametri. Quando vengono visualizzate le aree parametri o le credenziali, la visualizzazione di report è regolata per utilizzare la parte rimanente della web part. È possibile impostare le proprietà della web part per personalizzare la larghezza dei parametri. È inoltre possibile specificare le etichette da visualizzare accanto ai singoli parametri della pagina. Per ulteriori informazioni su come modificare i parametri, vedere [imposta parametri in un Report pubblicato &#40; Reporting Services in SharePoint integrata modalità &#41; ](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).  
  
## <a name="see-also"></a>Vedere anche

 [Web part Visualizzatore di report in un sito di SharePoint](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
 [Aggiungere la web part Visualizzatore Report a una pagina web](../../reporting-services/report-server-sharepoint/add-the-report-viewer-web-part-to-a-web-page.md)  

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

