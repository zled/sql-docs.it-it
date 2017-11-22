---
title: Progettazione di modelli tabulari | Documenti Microsoft
ms.date: 10/19/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ASVS.BIDTOOLSET.TOPLEVSEMMODUIENTRY.F1
ms.assetid: 45735c57-2a95-4e45-8994-7242df6c9c5f
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 388c20c5fffdd584b2923341db13c7bf634f289b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="tabular-model-designer-ssas"></a>Progettazione di modelli tabulari (SSAS)
La progettazione di modelli tabulari fa parte di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], integrato con Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], con modelli di tipi di progetto aggiuntivi espressamente ideati per lo sviluppo di soluzioni di modelli tabulari professionali.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] viene installato come un download Web gratuito. Per informazioni dettagliate, vedere [Scaricare SQL Server Data Tools (SSDT)](../../ssdt/download-sql-server-data-tools-ssdt.md).    
  
##  <a name="bkmk_benefits"></a> Vantaggi  
 Quando si installa [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], i nuovi modelli di progetto per la creazione di modelli tabulari vengono aggiunti ai tipi di progetto disponibili. Dopo aver creato un nuovo progetto di modello tabulare utilizzando uno dei modelli, è possibile iniziare la creazione di modelli utilizzando gli appositi strumenti e procedure guidate.  
  
 Oltre ai nuovi modelli e strumenti per la creazione di soluzioni di modelli multidimensionali e tabulari professionali, nell'ambiente di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sono disponibili funzionalità di debug e ciclo di vita di progetti che assicurano la creazione delle soluzioni BI più efficienti per l'organizzazione. Per ulteriori informazioni su [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vedere la pagina relativa all' [introduzione a Visual Studio](http://go.microsoft.com/fwlink/?LinkId=206389).  
  
##  <a name="bkmk_proj_temp"></a>Modelli di progetto  
 Quando si installa [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ai tipi di progetto di Business Intelligence vengono aggiunti i modelli relativi al progetto di modello tabulare seguenti:  
  
 **Progetto tabulare di Analysis Services**  
 Questo modello può essere utilizzato per creare un nuovo progetto di modello tabulare vuoto. I livelli di compatibilità vengono specificati quando si crea il progetto.
  
 **Importa da server (tabulare)**  
 Questo modello può essere utilizzato per creare un nuovo progetto di modello tabulare estraendo i metadati da un modello tabulare esistente in Analysis Services.  
  
 I modelli meno recenti hanno livelli di compatibilità precedenti. È possibile aggiornare modificando la proprietà a livello di compatibilità dopo l'importazione della definizione di modello.  
  
 **Importa da PowerPivot [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**  
 Questo modello viene utilizzato per creare un nuovo progetto di modello tabulare estraendo i metadati e i dati da un file [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] .  
  
##  <a name="bkmk_wind_men"></a> Finestre e menu  
 Nell'ambiente di creazione di modelli tabulari di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] sono inclusi gli elementi seguenti:  
  
### <a name="designer-window"></a>Finestra di progettazione  
 La finestra di progettazione viene utilizzata per creare modelli tabulari fornendo una rappresentazione visiva del modello. Quando si apre il file Model.bim, il modello viene visualizzato nella finestra di progettazione. È possibile creare un modello nella finestra di progettazione utilizzando due modalità di visualizzazione diverse:  
  
 **Visualizzazione di dati**  
 Nella Vista dati sono visualizzate le tabelle in formato griglia tabulare. Le misure possono essere definite anche utilizzando la relativa griglia che può essere visualizzata per ogni tabella solo nella Vista dati.  
  
 **Vista diagramma**  
 Nella Vista diagramma sono visualizzate le tabelle, con le relative relazioni, in formato grafico. È possibile filtrare colonne, misure, gerarchie e indicatori KPI, nonché scegliere di visualizzare il modello utilizzando una prospettiva definita.  
  
 La maggior parte delle attività di creazione dei modelli può essere effettuata con entrambe le viste.  
  
### <a name="view-code-window"></a>Finestra Visualizza codice  
 È possibile visualizzare il codice dietro a un file Model.bim quando si fa clic con il pulsante destro del mouse su **Visualizza codice** nel file in Esplora soluzioni. Per i modelli tabulari a livello di compatibilità 1200 e versioni successiva, la definizione del modello viene espressa in JSON.  
  
 È necessaria una versione completa di Visual Studio con l'editor JSON. È possibile scaricare e installare l' [edizione gratuita di Visual Studio Community](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) se non sono necessarie le funzionalità aggiuntive delle edizioni commerciali.  
  
### <a name="solution-explorer"></a>Esplora soluzioni  
 Nella finestra Esplora soluzioni viene presentata la soluzione attiva come contenitore logico per un progetto di modello tabulare e gli elementi associati. Nel progetto di modelli (con estensione smproj) sono contenuti solo un oggetto References (vuoto) e il file Model.bim. È possibile aprire elementi di progetto per modificarli ed effettuare altre attività di gestione direttamente da questa vista.  
  
 In genere, nelle soluzioni di modelli tabulari è contenuto un solo progetto; tuttavia in una soluzione possono essere inclusi anche altri progetti, ad esempio un progetto Integration Services o Reporting Services. È possibile aggiungere un qualsiasi numero di file a condizione che non siano dello stesso tipo dei file del progetto di modello tabulare, che la proprietà Azione di compilazione sia impostata su Nessuna o che la proprietà Copia nella directory di output sia impostata su Non copiare.  
  
 Per visualizzare Esplora soluzioni, fare clic sul menu **Visualizza** , quindi su **Esplora soluzioni**.  

### <a name="tabular-model-explorer"></a>Esplora modelli tabulari
  Primo disponibile nella versione di agosto 2016 (14.0.60812.0) di [SQL Server Data Tools](https://msdn.microsoft.com/mt186501), Esplora modello tabulare consente di passare oggetti di metadati nei modelli tabulari.

 Per visualizzare Esplora modelli tabulari, fare clic su **Visualizza** > **Altre finestre**e quindi su **Esplora modelli tabulari**.
   
  ![Esplora modelli tabulari](../../analysis-services/tabular-models/media/tabular-model-explorer.png) 
  
 Esplora modello tabulare consente di organizzare gli oggetti di metadati in una struttura ad albero che lo schema di un modello tabulare è molto simile. Origini dati, Prospettive, Relazioni, Ruoli, Tabelle e Traduzioni corrispondono agli oggetti dello schema di primo livello. Esistono alcune eccezioni, in particolare KPI e Misure, che tecnicamente non sono oggetti di primo livello, ma oggetti figlio delle varie tabelle nel modello. Tuttavia, avendo consolidato contenitori di primo livello per tutti i KPI e tutte le misure, è più facile usare questi oggetti, in particolare se il modello include un numero molto elevato di tabelle. Le misure sono anche elencate all'interno delle tabelle padre corrispondenti, per offrire una visualizzazione chiara delle effettive relazioni padre-figlio. Se si seleziona una misura nel contenitore Misure di primo livello, la stessa misura viene selezionata anche nella raccolta figlio all'interno della tabella e viceversa.  
 
 I nodi degli oggetti in Esplora modelli tabulari sono collegati alle opzioni di menu appropriate che fino a questo momento erano nascoste nei menu Modello, Tabella e Colonna in Visual Studio. È possibile fare clic con il pulsante destro del mouse su un oggetto per esplorare le opzioni per il tipo di oggetto. Non tutti i tipi di nodo di oggetto sono già associati a un menu contestuale, ma nelle prossime versioni verranno introdotti altri miglioramenti e opzioni aggiuntive. 

 Esplora modelli tabulari offre anche una pratica funzionalità di ricerca. Basta digitare una parte del nome nella casella Cerca perché Esplora modelli tabulari limiti la visualizzazione albero alle corrispondenze. 
  
### <a name="properties-window"></a>Finestra Proprietà  
 Nella finestra Proprietà sono elencate le proprietà dell'oggetto selezionato. Gli oggetti seguenti dispongono di proprietà che possono essere visualizzate e modificate nella finestra Proprietà:  
  
-   Model.bim  
  
-   Tabella  
  
-   Colonna  
  
-   Misura  
  
 Le proprietà del progetto consentono solo di visualizzare il nome e la cartella del progetto nella finestra Proprietà. Ai progetti sono inoltre associate opzioni di distribuzione aggiuntive e impostazioni del server di distribuzione che è possibile specificare utilizzando una finestra di dialogo delle proprietà modale. Per visualizzare queste proprietà, in **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.  
  
 Nei campi della finestra Proprietà sono incorporati diversi controlli che si aprono quando si fa clic su di essi. Il tipo di controllo di modifica dipende dalla proprietà specifica. Nei controlli sono inclusi caselle di modifica, elenchi a discesa e collegamenti a finestre di dialogo personalizzate. Le proprietà visualizzate in grigio sono di sola lettura.  
  
 Per visualizzare la finestra **Proprietà** , fare clic sul menu **Visualizza** , quindi su **Finestra Proprietà**.  
  
### <a name="error-list"></a>Elenco errori  
 Nella finestra Elenco errori sono contenuti i messaggi sullo stato del modello:  
  
-   Notifiche sulle procedure consigliate di sicurezza.  
  
-   Requisiti per l'elaborazione dati.  
  
-   Informazioni sugli errori semantici per le colonne calcolate, le misure e filtri di riga per i ruoli. Per le colonne calcolate, è possibile fare doppio clic sul messaggio di errore per passare all'origine dell'errore.  
  
-   Errori di convalida della modalità DirectQuery.  
  
 Per impostazione predefinita, l' **Elenco errori** non viene visualizzato a meno che non venga restituito un errore. Tuttavia, la finestra **Elenco errori** può essere visualizzata in qualsiasi momento. Per visualizzare la finestra **Elenco errori** , fare clic sul menu **Visualizza** , quindi su **Elenco errori**.  
  
### <a name="output"></a>Output  
 Le informazioni sulla compilazione e sulla distribuzione vengono visualizzate nella finestra **Output** , oltre che nella finestra di dialogo dello stato di avanzamento modale. Per visualizzare la finestra **Output** , fare clic sul menu **Visualizza** , quindi su Output.  
  
### <a name="menu-items"></a>Voci di menu  
 Quando si installa [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vengono aggiunte ulteriori voci di menu specifiche per la creazione di modelli tabulari alla barra dei menu di Visual Studio. Il menu **Modello** può essere utilizzato per avviare l'Importazione guidata dati, visualizzare connessioni esistenti, elaborare dati dell'area di lavoro ed elaborare l'area di lavoro del modello in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. Il menu **Tabella** viene utilizzato per creare e gestire relazioni tra tabelle, creare e gestire misure nonché per specificare impostazioni della tabella di dati, opzioni di calcolo ed altre proprietà della tabella. Con il menu **Colonna** è possibile aggiungere ed eliminare colonne in una tabella, nascondere e visualizzare colonne, nonché specificare altre proprietà della colonna quali i tipi di dati e i filtri. È possibile compilare e distribuire soluzioni di modelli tabulari dal menu **Compila** . Le funzioni Copia/Incolla sono incluse nel menu **Modifica** .  
  
 Oltre a queste voci di menu, vengono aggiunte ulteriori impostazioni alle opzioni di Analysis Services accessibili tramite le voci del menu Strumenti.  
  
### <a name="toolbar"></a>Barra degli strumenti  
 La barra degli strumenti di Analysis Services consente un accesso rapido e semplice ai comandi per la creazione di modelli utilizzati più frequentemente.  
  
##  <a name="bkmk_vsint"></a>Integrazione di Visual Studio  
 **Controllo del codice sorgente**  
 I progetti di Analysis Services sono integrati con il plug-in del controllo del codice sorgente selezionato. Se Visual Studio è stato configurato in modo che venga utilizzato il controllo del codice sorgente, è possibile utilizzare l'archiviazione in Esplora Soluzioni o l'estrazione. Per configurare l'utilizzo di Team Foundation Server, vedere [Configurare Visual Studio con Team Foundation Version Control](http://msdn.microsoft.com/library/ms253064.aspx). Sono supportati anche molti plug-in del controllo del codice sorgente di terze parti.  
  
 **Tipi di carattere**  
 Nei modelli tabulari viene usato il tipo di carattere ambiente di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per controllare i tipi di carattere nella visualizzazione. Può essere necessario modificare questo tipo di carattere se quello predefinito di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] non dispone di tutti i caratteri Unicode necessari per la lingua in uso. Per modificare i tipi di carattere, fare clic sul menu **Strumenti** , quindi su **Opzioni**e infine su **Tipi di carattere e colori**.  
  
 **Tasti di scelta rapida**  
 I tasti di scelta rapida di Analysis Services possono essere configurati o mappati di nuovo tramite Strumenti->Opzioni ->finestra di dialogo Tastiera. Alcuni tasti di scelta rapida [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] globali, ad esempio quelli di compilazione, salvataggio, debug, nuovo progetto e così via, sono supportati nel contesto di progettazione di modelli tabulari. Altri collegamenti specifici della progettazione di modelli tabulari sono disponibili nel contesto di Analysis Services.  
  
## <a name="see-also"></a>Vedere anche  
 [Progetti di modello tabulare &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/tabular-model-projects-ssas-tabular.md)   
 [Proprietà &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/properties-ssas-tabular.md)  
  
  
