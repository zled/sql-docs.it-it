---
title: "Gestire una Knowledge Base | Microsoft Docs"
ms.custom: ""
ms.date: "06/04/2013"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27f306f4-d67c-47f5-b35c-4260cc5d36e3
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Gestire una Knowledge Base
  In questo argomento viene descritto come eseguire le funzioni di gestione su una Knowledge Base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). È possibile eliminare una Knowledge Base, sbloccarla, annullare le modifiche apportatevi, rinominarla e visualizzarne le proprietà.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 Per gestire una Knowledge Base, è necessario che questa sia già stata creata e pubblicata (se creata da un altro utente) o chiusa (se creata dallo stesso utente).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per aprire una Knowledge Base è necessario disporre del ruolo dqs_kb_editor o dqs_administrator nel database DQS_MAIN.  
  
##  <a name="Manage"></a> Gestire una Knowledge Base  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Client Data Quality](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] fare clic su **Apri Knowledge Base**.  
  
3.  Fare clic con il pulsante destro del mouse su una Knowledge Base nella relativa tabella.  
  
4.  Nel menu di scelta rapida è possibile scegliere tra le opzioni seguenti:  
  
    1.  **Aprire**: fare clic per aprire la knowledge base nell'attività selezionata nel **selezionare attività** riquadro.  
  
    2.  **Sbloccare**: È possibile sbloccare la knowledge base se si è l'utente che ha usato la knowledge base in una delle operazioni di gestione del dominio, l'individuazione e l'attività di criteri di corrispondenza e chiuso. Se si sblocca la Knowledge Base, un altro utente potrà aprirla e utilizzarla. Questo comando non è disponibile se la Knowledge Base non si trova in uno stato di un'attività. Per ulteriori informazioni, vedere [aprire una Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
    3.  **Ignorare operazioni**: fare clic su quando la knowledge base è in uno stato di lavorazione, indicato con una voce nel campo stato nella tabella. Questo comando non è disponibile se la Knowledge Base non si trova in uno stato di un'attività e se la Knowledge Base è bloccata. Per ulteriori informazioni, vedere [aprire una Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
    4.  **Rinominare**: fare clic per rendere modificabile per la knowledge base selezionata il campo della Knowledge Base della tabella. Modificare il nome, quindi fare clic sulla Knowledge Base e nel campo per accettare la modifica del nome.  
  
    5.  **Eliminare**: fare clic per rimuovere la knowledge base dal database DQS_MAIN su [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
    6.  **Proprietà**: fare clic per visualizzare le proprietà del database in sola lettura.  
  
        1.  **Knowledge Base origine**: la knowledge base su cui si basa questo database. Operazione facoltativa.  
  
        2.  **Stato**: indica se la knowledge base è **In lavorazione** e se si trova in un'attività di gestione informazioni specifiche, come indicato dopo l'ultima chiusura. Lo stato può essere **In lavorazione**, in cui la knowledge base viene aperta in una sessione di Gestione Knowledge Base, ma non in un'attività specifica, o **In fase di elaborazione** con un'attività di gestione di informazioni, in cui la knowledge base viene aperta in una sessione di gestione di informazioni e in un'attività specifica.  
  
        3.  **È bloccato**: **True** Se la knowledge base è stata bloccata, **False** in caso contrario  
  
        4.  **Contiene contenuto non pubblicato**: True se la knowledge base contiene contenuto non è stato salvato dalla pubblicazione, False se non  
  
        5.  **Bloccato da**: il nome dell'utente che ha chiuso la knowledge base, Bloccandola.  
  
        6.  **Data blocco**: data del blocco  
  
        7.  **Creato da**: il nome dell'utente che ha creato la knowledge base, con la rete che appartiene a  
  
        8.  **Data di creazione**: data della creazione  
  
##  <a name="FollowUp"></a> Completamento: fasi successive alla gestione di una Knowledge Base  
 Dopo avere gestito una Knowledge Base, il passaggio successivo dipende dall'azione intrapresa sulla Knowledge Base:  
  
-   Se la Knowledge Base è stata aperta, l'utente continuerà nell'attività selezionata.  
  
-   Se è stata sbloccata, la Knowledge Base potrà essere aperta e utilizzata da un altro utente nello stato indicato.  
  
-   Se vi sono state annullate le modifiche apportate, la Knowledge Base sarà disponibile nell'ultimo stato pubblicato.  
  
-   Se è stata rinominata, sarà necessario aprire la Knowledge Base rinominata.  
  
-   Se è stata eliminata, sarà necessario selezionare un'altra Knowledge Base o crearne una nuova.  
  
  