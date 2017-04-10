---
title: "Creazione di un dominio | Microsoft Docs"
ms.custom: ""
ms.date: "11/08/2011"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.kb.createdomain.f1"
ms.assetid: 5c4828f5-bd51-4c29-b3de-87b7d2f2d3e5
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# Creazione di un dominio
  In questo argomento viene descritto come creare un dominio in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). I valori nel dominio sono una rappresentazione semantica dei dati in un campo. Per ulteriori informazioni sui domini, vedere [gestione di un dominio](../data-quality-services/managing-a-domain.md).  
  
 Sono disponibili due modi per creare un nuovo dominio. Il primo viene utilizzato durante il passaggio di mapping dell'attività di individuazione delle informazioni, quando è in corso l'analisi di un campione di dati per aggiungere informazioni a una Knowledge Base nuova o esistente. Il secondo viene utilizzato durante l'attività di gestione del dominio, quando anziché modificare un dominio esistente, se ne crea uno nuovo.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 Per creare un dominio, è necessario avere creato e aperto una Knowledge Base.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per creare un dominio, è necessario disporre del ruolo dqs_kb_editor o dqs_administrator nel database DQS_MAIN.  
  
##  <a name="Discovery"></a> Creare un dominio nell'attività di individuazione delle informazioni  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Client Data Quality](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale di [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , fare clic su **Apri Knowledge Base** , quindi selezionare una Knowledge Base o fare clic su **Nuova Knowledge Base** e immettere le proprietà per la nuova Knowledge Base.  
  
3.  Selezionare **Individuazione informazioni** come attività, quindi fare clic su **Crea** per creare la nuova Knowledge Base, oppure **Apri** per aprirne una esistente.  
  
4.  Nella pagina **Mappa** specificare una connessione all'origine dati. Per ulteriori informazioni, vedere [Perform Knowledge Discovery](../data-quality-services/perform-knowledge-discovery.md).  
  
5.  Nel **mapping** tabella, selezionare una colonna di origine dall'elenco a discesa per il **colonna di origine** colonna di una riga vuota. Se non esiste alcun dominio corrispondente, fare clic su di **creare un dominio** icona.  
  
##  <a name="DomainManagement"></a> Creare un dominio nell'attività di gestione del dominio  
  
1.  Nella schermata iniziale di [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , fare clic su **Apri Knowledge Base** , quindi selezionare una Knowledge Base o fare clic su **Nuova Knowledge Base** e immettere le proprietà per la nuova Knowledge Base.  
  
2.  Selezionare **Gestione dominio** come attività, quindi fare clic su **Crea** per creare la nuova Knowledge Base, oppure **Apri** per aprirne una esistente.  
  
3.  Nel **Domain Management** pagina, fare clic su di **creare un dominio** icona sopra l'elenco di domini.  
  
##  <a name="Properties"></a> Impostare le proprietà di un dominio  
  
1.  Nel **Crea dominio** finestra di dialogo immettere un nome univoco per la knowledge base e una descrizione di un massimo di 256 caratteri.  
  
    > [!NOTE]  
    >  Per ulteriori informazioni sulle proprietà del dominio, vedere [Imposta proprietà dominio](../data-quality-services/set-domain-properties.md).  
  
2.  Dal **tipo di dati** selezionare un tipo di dati per i valori nel dominio. Il tipo di dati può essere **stringa** (impostazione predefinita), **Data**, **Integer**, o **decimale**.  
  
3.  Selezionare **utilizza valori iniziali** per specificare che il valore iniziale in un gruppo di sinonimi venga restituito invece un valore che è un sinonimo. Deselezionare **utilizza valori iniziali** per specificare che ogni valore di sinonimo verrà restituito nel formato corretto o e non viene sostituita dal valore iniziale per il gruppo.  
  
4.  Se il tipo di dati è **stringa**, selezionare **Normalizza stringa** per rimuovere i caratteri speciali nei valori di dominio, migliorando la probabilità di corrispondenze.  
  
5.  Dal **formato Output in** -elenco a discesa, selezionare la formattazione che verrà applicata quando i valori dei dati nel dominio. La formattazione è specifica del tipo di dati selezionato nel passaggio 2, come mostrato nell'elenco seguente:  
  
    -   Per un valore stringa, è possibile specificare di restituire la stringa tutta in maiuscole, tutta in minuscole o solo con l'iniziale maiuscola.  
  
    -   Per un valore data, è possibile specificare il formato del giorno, del mese e dell'anno.  
  
    -   Per un valore intero, è possibile specificare il tipo di maschera del formato da applicare.  
  
    -   Per un valore decimale, è possibile specificare la precisione e il tipo di maschera del formato da applicare.  
  
     Selezione **Nessuno** nel **formato Output in** riepilogo indica che verrà applicato alcun formato nell'elenco.  
  
6.  Se il tipo di dati è **stringa**, nel **Language** -elenco a discesa, selezionare la lingua del correttore ortografico si desidera applicare se si abilita il correttore ortografico.  
  
7.  Se il tipo di dati è **stringa**, selezionare **Abilita correttore ortografico** per eseguire il correttore ortografico su tutti i valori stringa durante l'inserimento nel dominio.  
  
8.  Se il tipo di dati è **stringa**, selezionare **Disabilita algoritmi di errore di sintassi** per popolare il dominio senza verificare i valori di stringa degli errori di sintassi.  
  
9. Scegliere **OK**.  
  
10. Fare clic su **Fine** per completare l'attività di gestione del dominio, come descritto in [End the Domain Management Activity](../Topic/End%20the%20Domain%20Management%20Activity.md).  
  
##  <a name="FollowUp"></a> Completamento: fasi successive alla creazione di un dominio  
 Dopo avere creato un dominio, è possibile eseguire ulteriori attività di gestione del dominio, quali l'individuazione delle informazioni per aggiungere informazioni al dominio o l'aggiunta di criteri di corrispondenza al dominio. Per ulteriori informazioni, vedere [eseguire l'individuazione delle informazioni](../data-quality-services/perform-knowledge-discovery.md), [gestione di un dominio](../data-quality-services/managing-a-domain.md), o [creare un criterio di corrispondenza](../data-quality-services/create-a-matching-policy.md).  
  
  