---
title: "Finestra di dialogo Configura log SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.configuredtslogs.containers.f1"
  - "sql13.dts.designer.configuredtslogs.loggingdetails.f1"
  - "sql13.dts.designer.configuredtslogs.providersandlogs.f1"
helpviewer_keywords: 
  - "Configura log SSIS - finestra di dialogo"
ms.assetid: 4b980275-cd9a-4943-8c36-727d51f9a484
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Finestra di dialogo Configura log SSIS
  Utilizzare la finestra di dialogo **Configura log SSIS** per definire le opzioni di registrazione per un pacchetto.  
  
 **Per saperne di più**  
  
1.  [Apertura della finestra di dialogo Configura log SSIS](#open_dialog)  
  
2.  [Configurazione delle opzioni nel riquadro Contenitori](#container)  
  
3.  [Configurazione delle opzioni nella scheda Provider e log](#provider)  
  
4.  [Configurazione delle opzioni nella scheda Dettagli](#detail)  
  
##  <a name="open_dialog"></a> Apertura della finestra di dialogo Configura log SSIS  
 **Per aprire la finestra di dialogo Configura log SSIS**  
  
-   In Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] scegliere **Registrazione** nel menu **SSIS** .  
  
##  <a name="container"></a> Configurazione delle opzioni nel riquadro Contenitori  
 Utilizzare il riquadro **Contenitori** della finestra di dialogo **Configura log SSIS** per abilitare il pacchetto e i relativi contenitori per la registrazione.  
  
### Opzioni  
 **Contenitori**  
 Nella visualizzazione gerarchica selezionare le caselle di controllo in modo da abilitare il pacchetto e i relativi contenitori per la registrazione:  
  
-   Se deselezionato, il contenitore non è abilitato per la registrazione. Selezionarlo per abilitare la registrazione.  
  
-   Se visualizzato in grigio, il contenitore utilizza le opzioni di registrazione dell'elemento padre. Questa opzione non è disponibile per il pacchetto.  
  
-   Se selezionato, il contenitore definisce opzioni di registrazione specifiche.  
  
 Se si desidera impostare le opzioni di registrazione per un contenitore visualizzato in grigio, fare doppio clic sulla casella di controllo corrispondente al contenitore in questione. Al primo clic la casella di controllo viene deselezionata e al secondo clic viene selezionata, consentendo di scegliere il provider di log da utilizzare e di specificare le informazioni da registrare.  
  
##  <a name="provider"></a> Configurazione delle opzioni nella scheda Provider e log  
 Usare la scheda **Provider e log** della finestra di dialogo **Configura log SSIS** per creare e configurare log per l'acquisizione di eventi di runtime.  
  
### Opzioni  
 **Tipo provider**  
 Consente di selezionare un tipo di logger nell'elenco.  
  
 **Aggiungi**  
 Consente di aggiungere un log del tipo specificato alla raccolta di logger del pacchetto.  
  
 **Nome**  
 Consente di abilitare o disabilitare log per contenitori o attività selezionati nel riquadro **Contenitori** della finestra di dialogo **Configura log SSIS** usando le caselle di controllo. Il campo del nome è modificabile. Utilizzare il nome predefinito per il provider oppure digitare un nome descrittivo univoco.  
  
 **Description**  
 Il campo della descrizione è modificabile. Fare clic nel campo e quindi modificare la descrizione predefinita del log.  
  
 **Configurazione**  
 Selezionare una gestione connessione esistente nell'elenco oppure fare clic su \<**Nuova connessione...**> per creare una nuova gestione connessione. A seconda del tipo di logger, è possibile configurare una gestione connessione OLE DB o una gestione connessione file. Il logger per il registro eventi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] non necessita di connessioni.  
  
 Argomenti correlati: [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md) e [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md)  
  
 **Delete**  
 Selezionare un provider di log e fare clic su **Elimina**.  
  
##  <a name="detail"></a> Configurazione delle opzioni nella scheda Dettagli  
 Utilizzare la scheda **Dettagli** della finestra di dialogo **Configura log SSIS** per indicare gli eventi da abilitare per la registrazione e specificare le informazioni da registrare. Le informazioni selezionate saranno valide per tutti i provider di log nel pacchetto. Non è ad esempio possibile scrivere informazioni nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] diverse da quelle specificate in un file di testo.  
  
### Opzioni  
 **Eventi**  
 Consente di abilitare o disabilitare gli eventi per la registrazione.  
  
 **Description**  
 Consente di visualizzare una descrizione dell'evento.  
  
 **Avanzate**  
 Consente di selezionare o deselezionare gli eventi da registrare, nonché le informazioni da registrare per ogni evento. Fare clic su **Standard** per nascondere tutti i dettagli di registrazione, ad eccezione dell'elenco di eventi. Per la registrazione sono disponibili le informazioni seguenti:  
  
|Valore|Description|  
|-----------|-----------------|  
|**Computer**|Nome del computer in cui si è verificato l'evento registrato.|  
|**Operatore**|Nome utente dell'utente che ha avviato il pacchetto.|  
|**SourceName**|Nome del pacchetto, contenitore o attività in cui si è verificato l'evento registrato.|  
|**SourceID**|Identificatore univoco globale (GUID, Global Unique Identifier) del pacchetto, contenitore o attività in cui si è verificato l'evento registrato.|  
|**ExecutionID**|Identificatore univoco globale dell'istanza di esecuzione del pacchetto.|  
|**MessageText**|Messaggio associato alla voce di log.|  
|**DataBytes**|Riservato per utilizzi futuri.|  
  
 **Basic**  
 Consente di selezionare o deselezionare gli eventi da registrare. Questa opzione può essere utilizzata per nascondere i dettagli di registrazione, ad eccezione dell'elenco di eventi. Se si seleziona un evento, per impostazione predefinita verranno selezionati anche tutti i relativi dettagli di registrazione. Fare clic su **Avanzate** per visualizzarli.  
  
 **Load**  
 Consente di specificare un file XML esistente da utilizzare come modello per l'impostazione delle opzioni di registrazione.  
  
 **Salvare**  
 Consente di salvare i dettagli di configurazione come modello in un file XML.  
  
  