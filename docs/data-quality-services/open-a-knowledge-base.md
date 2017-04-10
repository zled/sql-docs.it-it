---
title: "Apertura di una Knowledge Base | Microsoft Docs"
ms.custom: ""
ms.date: "06/04/2013"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.kb.openkb.f1"
ms.assetid: a5f010a5-b762-41c9-881b-bf0c192dca83
caps.latest.revision: 20
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 20
---
# Apertura di una Knowledge Base
  In questo argomento viene descritto come aprire una Knowledge Base esistente in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) e prepararla per le attività di gestione del dominio, individuazione delle informazioni o aggiunta di criteri di corrispondenza.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 Per aprire una Knowledge Base, è necessario che questa sia già stata creata e pubblicata (se creata da un altro utente) o chiusa (se creata dallo stesso utente).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per aprire una Knowledge Base è necessario disporre del ruolo dqs_kb_editor o dqs_administrator nel database DQS_MAIN.  
  
##  <a name="Open"></a> Apertura di una Knowledge Base  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Client Data Quality](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] fare clic su **Apri Knowledge Base**.  
  
3.  Selezionare una Knowledge Base nella tabella. I domini e le regole di corrispondenza nella Knowledge Base verranno visualizzati nel riquadro nella parte destra della pagina.  
  
    > [!NOTE]  
    >  È possibile eseguire operazioni su una Knowledge Base facendo clic con il pulsante destro del mouse su di essa nella tabella. È possibile aprire la Knowledge Base, salvarla con un nome diverso, sbloccarla, annullare le modifiche apportatevi, rinominarla o visualizzarne le proprietà.  
  
4.  In **Seleziona attività**, selezionare l'attività che si desidera eseguire sulla Knowledge Base:  
  
    -   Selezionare **Gestione dominio** per accedere alle schermate per la modifica dei domini nella Knowledge Base.  
  
    -   Selezionare **Individuazione informazioni** per avviare la procedura guidata che consente di analizzare un campione di dati e di popolare i domini della Knowledge Base con i risultati.  
  
    -   Selezionare **Criteri di corrispondenza** per creare criteri di corrispondenza e aggiungerli alla Knowledge Base.  
  
5.  Fare clic su **Apri**.  
  
    > [!NOTE]  
    >  È inoltre possibile aprire la Knowledge Base facendo clic con il pulsante destro del mouse su di essa e quindi scegliendo Apri. Altri comandi disponibili nel menu di scelta rapida consentono di salvare la Knowledge Base con un nome diverso, sbloccarla, annullare le modifiche apportatevi, rinominarla o visualizzarne le proprietà.  
  
    > [!NOTE]  
    >  Se non è possibile aprire la Knowledge Base perché bloccata, vedere la sezione seguente.  
  
## Apertura di una Knowledge Base recente  
 Le cinque Knowledge Base aperte più recentemente sono visualizzate nell'elenco **Knowledge Base recente** nella home page di DQS. Ciò consente di aprire una Knowledge Base con cui si è lavorato recentemente senza passare per la pagina **Apri Knowledge Base** .  
  
-   Per aprire una Knowledge Base non bloccata e presente nell'elenco delle Knowledge Base recenti, fare clic sulla freccia destra relativa alla Knowledge Base desiderata, quindi selezionare l'attività nella quale avviare la Knowledge Base.  
  
-   Per aprire una Knowledge Base presente nell'elenco delle Knowledge Base recenti ma che è stata bloccata dall'utente che vi sta lavorando, fare clic sulla Knowledge Base e la Knowledge Base verrà aperta nell'attività e nella pagina indicate tra parentesi.  
  
-   Per aprire una Knowledge Base presente nell'elenco delle Knowledge Base recenti ma che è stata bloccata da un altro utente, contattare l'utente per richiederne lo sblocco.  
  
##  <a name="FollowUp"></a> Completamento: Operazioni successive all'apertura di una Knowledge Base  
 Dopo avere aperto una Knowledge Base, questa viene collocata nello stato indicato nella colonna Stato della relativa tabella. Per le attività di individuazione delle informazioni e quelle relative ai criteri di corrispondenza, la Knowledge Base verrà aperta in una pagina di procedura guidata specifica. Per l'attività di gestione del dominio, la Knowledge Base verrà aperta nella pagina di gestione del dominio. Per ulteriori informazioni sugli stati di, vedere [eseguire l'individuazione delle informazioni](../data-quality-services/perform-knowledge-discovery.md), [gestione di un dominio](../data-quality-services/managing-a-domain.md), o [creare un criterio di corrispondenza](../data-quality-services/create-a-matching-policy.md).  
  
##  <a name="Locked"></a> Se la Knowledge Base è bloccata  
 L'icona di blocco nella prima colonna indica se la Knowledge Base è bloccata. Il nome di una Knowledge Base bloccata verrà visualizzato in colore rosso. Una Knowledge Base in corso di modifica da parte di un utente specifico tramite un'attività di Knowledge Base, viene contrassegnata come Bloccata. Una Knowledge Base bloccata non può essere modificata da un secondo utente. L'utente che si occupa della knowledge base può sbloccarla facendo la knowledge base nella tabella nella pagina Apri Knowledge Base e facendo clic su **Unlock**, o mediante la pubblicazione. Quando si posiziona il cursore su una Knowledge Base bloccata, viene visualizzato un suggerimento in DQS che indica chi ha bloccato la Knowledge Base e quando.  
  
##  <a name="State"></a> Stato di una Knowledge Base  
 Nel campo Stato viene indicata la fase di un'attività a cui si trova la Knowledge Base. Se si apre la Knowledge Base, verrà aperta in quella fase.  
  
-   **\< vuoto>**: il campo stato è vuoto per una knowledge base se è stata pubblicata la knowledge base facendo **Pubblica** nell'attività Gestione dominio e fare clic su **Sì-pubblica la knowledge base e Chiudi**.  
  
-   **In lavorazione**: il lavoro sulla Knowledge Base è stato salvato facendo clic su **Pubblica** nell'attività Gestione dominio e quindi su **No - Salva il lavoro relativo alla Knowledge Base e chiudi**.  
  
-   **Gestione dominio**: sono stati immessi dati per un dominio nella Knowledge Base, ma la Knowledge Base non è stata pubblicata e il lavoro rimane nell'attività Gestione dominio. L'attività Individuazione informazioni non è disponibile. Ciò si verifica quando si fa clic su **Chiudi** nella schermata **Gestione dominio** .  
  
-   **Individuazione - Mapping**: la knowledge base è stata chiusa nella **Gestione Knowledge Base: Mapping** pagina. La Knowledge Base è bloccata e le attività di gestione del dominio e di individuazione delle corrispondenze non sono disponibili.  
  
-   **Individuazione - individuazione**: la knowledge base è stata chiusa nella **Gestione Knowledge Base: analizzare** pagina. La Knowledge Base è bloccata e l'attività di gestione del dominio non è disponibile.  
  
-   **Individuazione - Gestione valore**: la Knowledge Base è stata chiusa nella pagina **Gestione Knowledge Base: Gestisci termini di dominio** . La Knowledge Base è bloccata e l'attività di gestione del dominio non è disponibile.  
  
-   **Criteri di corrispondenza - Criteri di corrispondenza**: la Knowledge Base è stata chiusa nella pagina **Criteri di corrispondenza - Criteri di corrispondenza** . La Knowledge Base è bloccata e le attività di gestione del dominio e di individuazione delle informazioni non sono disponibili.  
  
-   **Criteri di corrispondenza - Risultati corrispondenza**: la Knowledge Base è stata chiusa nella pagina **Criteri di corrispondenza - Risultati corrispondenza** . La Knowledge Base è bloccata e le attività di gestione del dominio e di individuazione delle informazioni non sono disponibili.  
  
  