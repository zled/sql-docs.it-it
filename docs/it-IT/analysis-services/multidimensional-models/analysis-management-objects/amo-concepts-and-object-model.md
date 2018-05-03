---
title: Modello a oggetti e i concetti di AMO | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: amo
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 778007f9cdf5b2c0eea94d9d202545e95476d1c7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="amo-concepts-and-object-model"></a>Modello a oggetti AMO e concetti relativi
  In questo argomento fornisce una definizione di Analysis Management Objects (AMO), come AMO è correlato agli altri strumenti e librerie disponibili nell'architettura di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]e una spiegazione concettuale di tutti gli oggetti AMO principali.  
  
 AMO è una raccolta completa di classi di gestione per [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] che può essere utilizzata a livello di programmazione nello spazio dei nomi di <xref:Microsoft.AnalysisServices> in un ambiente gestito. Le classi sono incluse nel file AnalysisServices.dll, che in genere si trova in cui il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono installati i file, sotto la cartella di \100\SDK\Assemblies\\. Per utilizzare le classi AMO, includere un riferimento a tale assembly nei progetti.  
  
 Tramite AMO in grado di creare, modificare ed eliminare oggetti quali cubi, dimensioni, strutture di data mining e [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database; su tutti questi oggetti, è possibile eseguire azioni dall'applicazione in .NET Framework. È inoltre possibile elaborare e aggiornare le informazioni archiviate nei database di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 AMO non consente di eseguire query sui dati. Per eseguire query sui dati, utilizzare [allo sviluppo con ADOMD.NET](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md).  
  
 In questo argomento sono incluse le sezioni seguenti:  
  
 [AMO nell'architettura di Analysis Services](#AMOintheAnalysisServicesArchitecture)  
  
 [Architettura di AMO](#AMOArchitecture)  
  
 [Utilizzo di AMO](#bkmk_UsingAMO)  
  
 [Automatizzazione delle attività amministrative con AMO](#AutomatingAdministrativeTaskswithAMO)  
  
##  <a name="AMOintheAnalysisServicesArchitecture"></a> AMO nell'architettura di Analysis Services  
 Per motivi strutturali, AMO è destinato alla gestione di oggetti e non all'esecuzione di query sui dati. Se l'utente deve eseguire query [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] dati da un'applicazione client, l'applicazione client deve utilizzare [allo sviluppo con ADOMD.NET](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md).  
  
##  <a name="AMOArchitecture"></a> Architettura di AMO  
 AMO è una libreria completa di classi progettata per gestire un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] da un'applicazione client in codice gestito in .NET Framework versione 2.0.  
  
 La libreria AMO è progettata come una gerarchia di classi in cui è necessario creare un'istanza di determinate classi prima di altre al fine di utilizzarle nel codice. Sono disponibili inoltre classi ausiliarie di cui può essere creata un'istanza in qualsiasi momento nel codice. Prima di utilizzare una delle classi ausiliarie, è probabile tuttavia che l'utente abbia creato un'istanza di una o più delle classi della gerarchia.  
  
 Nella figura seguente viene illustrata una vista di alto livello della gerarchia di AMO in cui sono incluse classi principali. Nella figura viene illustrata la posizione delle classi tra i relativi contenitori e peer. Un oggetto <xref:Microsoft.AnalysisServices.Dimension> appartiene a un oggetto <xref:Microsoft.AnalysisServices.Database> e <xref:Microsoft.AnalysisServices.Server> e può essere creato in qualsiasi momento come un oggetto <xref:Microsoft.AnalysisServices.DataSource> e <xref:Microsoft.AnalysisServices.MiningStructure>. È necessario creare un'istanza di determinate classi peer prima che sia possibile utilizzarne altre. È necessario ad esempio creare un'istanza di <xref:Microsoft.AnalysisServices.DataSource> prima di aggiungere un nuovo oggetto <xref:Microsoft.AnalysisServices.Dimension> o <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
 ![Vista di alto livello di classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-highlevelview-majorobjectshighlighted.gif "vista di alto livello di classi AMO")  
  
 Oggetto *oggetto principale* è una classe che rappresenta un oggetto completo come entità intera e non come parte di un altro oggetto. Gli oggetti principali includono <xref:Microsoft.AnalysisServices.Server>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Dimension> e <xref:Microsoft.AnalysisServices.MiningStructure>, poiché da soli costituiscono entità. Un oggetto <xref:Microsoft.AnalysisServices.Level>, tuttavia, non è un oggetto principale poiché costituisce una parte di un oggetto <xref:Microsoft.AnalysisServices.Dimension>. Gli oggetti principali possono essere creati, eliminati, modificati oppure elaborati indipendentemente da altri oggetti. Gli oggetti secondari sono oggetti che possono essere creati solo come parte della creazione dell'oggetto principale padre e vengono in genere creati in questa fase. I valori per gli oggetti secondari devono essere definiti nel momento della creazione poiché per questo tipo di oggetti non è prevista una creazione predefinita.  
  
 Nella figura seguente vengono illustrati gli oggetti principali contenuti in un oggetto <xref:Microsoft.AnalysisServices.Server>.  
  
 ![Oggetti AMO principali evidenziati](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-majorobjects.gif "oggetti AMO principali evidenziati")  
  
 ![Oggetti AMO principali evidenziati (2)](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-majorobjects-02.gif "oggetti AMO principali evidenziati (2)")  
  
 Nella programmazione con AMO l'associazione tra classi e classi contenute utilizza attributi del tipo di raccolta, ad esempio <xref:Microsoft.AnalysisServices.Server> e <xref:Microsoft.AnalysisServices.Dimension>. Per utilizzare un'istanza di una classe contenuta, è necessario innanzitutto acquisire un riferimento a un oggetto della raccolta che include o può includere la classe contenuta. Successivamente è necessario individuare nella raccolta l'oggetto specifico desiderato, quindi è possibile ottenere un riferimento all'oggetto per iniziare a utilizzarlo.  
  
### <a name="amo-classes"></a>Classi AMO  
 AMO è una libreria di classi progettata per gestire un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] da un'applicazione client. La libreria AMO può essere considerata come un insieme di gruppi di oggetti correlati logicamente utilizzati per eseguire un'attività. Le classi AMO possono essere suddivise in categorie nel modo riportato di seguito:  
  
|Set di classi|Scopo|  
|---------------|-------------|  
|[Classi fondamentali AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)|Classi necessarie per utilizzare qualsiasi altro set di classi.|  
|[Classi OLAP di AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-olap-classes.md)|Classi che consentono di gestire gli oggetti OLAP in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Classi di data mining AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-data-mining-classes.md)|Classi che consentono di gestire gli oggetti di data mining in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Classi di sicurezza AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-security-classes.md)|Classi che consentono di controllare l'accesso ad altri oggetti e di gestire la sicurezza.|  
|[Altre classi e altri metodi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-other-classes-and-methods.md)|Classi e metodi che consentono agli amministratori OLAP o responsabili delle operazioni di data mining di completare le attività giornaliere.|  
  
##  <a name="bkmk_UsingAMO"></a> Utilizzo di AMO  
 AMO risulta particolarmente utile per automatizzare attività ripetitive, ad esempio la creazione di nuove partizioni in un gruppo di misure in base a nuovi dati nella tabella dei fatti o la riesecuzione del training di un modello di data mining con nuovi dati. Tali attività che creano nuovi oggetti vengono eseguite in genere su base mensile, settimanale o trimestrale e il relativo nome basato sui nuovi dati può essere assegnato in modo semplice dall'applicazione.  
  
##### <a name="analysis-services-administrators"></a>Amministratori di Analysis Services  
 Gli amministratori di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] possono utilizzare AMO per automatizzare l'elaborazione di database di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Per la progettazione e la distribuzione di database di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], è necessario utilizzare [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
##### <a name="developers"></a>Sviluppatori  
 Gli sviluppatori possono utilizzare AMO per sviluppare interfacce amministrative per set specificati di utenti. Tali interfacce possono limitare l'accesso agli oggetti di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e impedire agli utenti di eseguire determinate attività. Tramite AMO è possibile creare ad esempio un'applicazione di backup che consente a un utente di visualizzare tutti gli oggetti di database, selezionare uno qualsiasi dei database ed eseguirne il backup in uno dei dispositivi di un set specificato.  
  
 Gli sviluppatori possono inoltre incorporare logica di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nelle applicazioni creando cubi, dimensioni e strutture e modelli di data mining in base all'input dell'utente oppure ad altri fattori.  
  
##### <a name="olap-advanced-users"></a>Utenti OLAP esperti  
 Gli utenti OLAP esperti sono in genere analisti dei dati o altri utenti con esperienza nell'utilizzo dei dati che dispongono di notevoli conoscenze nell'ambito della programmazione e che desiderano migliorare l'analisi dei dati con un utilizzo più approfondito degli oggetti dati. Per utenti che devono lavorare offline, AMO può semplificare notevolmente la creazione automatica di cubi locali prima dell'attivazione di tale modalità.  
  
##### <a name="data-mining-advanced-users"></a>Utenti esperti di operazioni di data mining  
 Per gli utenti esperti in operazioni di data mining, AMO risulta estremamente utile se sono presenti set di modelli di grandi dimensioni di cui è necessario rieseguire periodicamente il training.  
  
##  <a name="AutomatingAdministrativeTaskswithAMO"></a> Automatizzazione delle attività amministrative con AMO  
 La maggior parte delle attività ripetitive vengono progettate, distribuite e gestite meglio se per lo sviluppo viene utilizzato [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] anziché un'applicazione in qualsiasi linguaggio selezionato dall'utente. Per attività ripetitive che non possono essere automatizzate tramite [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], è tuttavia possibile utilizzare AMO. AMO risulta utile inoltre quando si desidera sviluppare un'applicazione specializzata per Business Intelligence tramite [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
##### <a name="automatic-object-management"></a>Gestione automatica degli oggetti  
 AMO consente di creare, aggiornare o eliminare oggetti di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], ad esempio <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube>, oggetti <xref:Microsoft.AnalysisServices.MiningStructure> e <xref:Microsoft.AnalysisServices.MiningModel> relativi al data mining o <xref:Microsoft.AnalysisServices.Role>, in base all'input utente o ai nuovi dati acquisiti. AMO rappresenta la soluzione ideale per applicazioni di installazione che devono distribuire una soluzione sviluppata da un fornitore di software indipendente a un cliente finale. L'applicazione di installazione può verificare l'esistenza di una versione precedente e può aggiornare la struttura, rimuovere gli oggetti non più utili e crearne di nuovi. Se non è presente alcuna versione precedente, l'applicazione può creare qualsiasi elemento da zero.  
  
 AMO può essere particolarmente efficace nella creazione di nuove partizioni basate su nuovi dati ed è in grado di rimuovere partizioni obsolete non più necessarie per il progetto. In una soluzione di analisi finanziaria in cui vengono utilizzati gli ultimi 36 mesi di dati, ad esempio, non appena viene ricevuto un nuovo mese di dati il mese più obsoleto potrebbe essere rimosso. Per ottimizzare le prestazioni, è possibile progettare nuove aggregazioni in base all'utilizzo e applicarle ai 12 mesi più recenti.  
  
##### <a name="automatic-object-processing"></a>Elaborazione automatica di oggetti  
 L'utilizzo di AMO per rispondere a determinati eventi non appartenenti a dati di flusso ordinario e ad attività pianificate che utilizzano [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] consente di eseguire l'elaborazione degli oggetti e di ottenere una disponibilità aggiornata.  
  
##### <a name="automatic-security-management"></a>Gestione automatica della sicurezza  
 La gestione della sicurezza può essere automatizzata per assegnare nuovi utenti a ruoli e autorizzazioni o per rimuovere altri utenti non appena scaduto il tempo a disposizione relativo. Per semplificare la gestione per gli amministratori responsabili della sicurezza, è possibile creare nuove interfacce. Questa operazione può risultare più semplice rispetto all'utilizzo di [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
##### <a name="automatic-backup-management"></a>Gestione automatica dei backup  
 La gestione automatica dei backup può essere realizzata tramite attività di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] o la creazione di applicazioni AMO specializzate eseguite in modo automatico. Utilizzando AMO è inoltre possibile sviluppare interfacce di backup per gli operatori che ne semplificano i processi giornalieri.  
  
##### <a name="tasks-amo-is-not-intended-for"></a>Attività per cui AMO non è stato progettato  
 AMO non consente di eseguire query sui dati. Per eseguire query sui dati di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], ad esempio cubi e modelli di data mining, utilizzare ADOMD.NET da un'applicazione utente. Per ulteriori informazioni, vedere [allo sviluppo con ADOMD.NET](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md).  
  
  
