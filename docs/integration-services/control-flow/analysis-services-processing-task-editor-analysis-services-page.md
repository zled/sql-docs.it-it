---
title: "Editor attivit&#224; Elaborazione Analysis Services (pagina Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.asprocessingtask.as.f1"
helpviewer_keywords: 
  - "Editor attività Elaborazione Analysis Services"
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# Editor attivit&#224; Elaborazione Analysis Services (pagina Analysis Services)
  Usare la pagina **Analysis Services** della finestra di dialogo **Editor attività Elaborazione Analysis Services** per specificare una gestione connessione Analysis Services, selezionare gli oggetti analitici da elaborare e impostare le opzioni di elaborazione e di gestione degli errori.  
  
 Quando si elaborano modelli tabulari, tenere presente quanto segue:  
  
1.  Non è possibile effettuare analisi di impatto sui modelli tabulari.  
  
2.  Alcune opzioni di elaborazione per la modalità tabulare non sono esposte, ad esempio Elaborazione deframmentazione e Elabora ricalcolo. È possibile eseguire queste funzioni tramite l'attività Esegui DDL.  
  
3.  Alcune opzioni di elaborazione fornite, ad esempio l'elaborazione di indici, non sono appropriate per i modelli tabulari, pertanto non devono essere utilizzate.  
  
4.  Le impostazioni batch vengono ignorate per i modelli tabulari.  
  
 Per altre informazioni su questa attività, vedere [Attività Elaborazione Analysis Services](../../integration-services/control-flow/analysis-services-processing-task.md).  
  
## Opzioni  
 **Analysis Services - gestione connessione**  
 Consente di selezionare una gestione connessione Analysis Services esistente nell'elenco o di crearne una nuova usando il pulsante **Nuova**.  
  
 **Nuova**  
 Consente di creare una nuova gestione connessione Analysis Services.  
  
 **Argomenti correlati:** [Gestione connessione Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md), [Riferimento all'interfaccia utente della finestra di dialogo Aggiungi gestione connessione Analysis Services](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 **Elenco oggetti**  
 |Proprietà|Description|  
|--------------|-----------------|  
|**Nome oggetto**|Consente di visualizzare i nomi degli oggetti specificati.|  
|**Tipo**|Consente di visualizzare i tipi degli oggetti specificati.|  
|**Opzioni elaborazione**|Consente di selezionare un'opzione di elaborazione nell'elenco.<br /><br /> **Argomenti correlati**: [Elaborazione di un modello multidimensionale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)|  
|**Impostazioni**|Consente di visualizzare le impostazioni di elaborazione per gli oggetti specificati.|  
  
 **Aggiungi**  
 Consente di aggiungere un oggetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] all'elenco.  
  
 **Rimuovi**  
 Selezionare un oggetto, quindi fare clic su **Elimina**.  
  
 **Analisi di impatto**  
 Consente di eseguire un'analisi di impatto sull'oggetto selezionato.  
  
 **Argomenti correlati:** [Finestra di dialogo Analisi di impatto &#40;Analysis Services - Dati multidimensionali&#41;](../Topic/Impact%20Analysis%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
 **Riepilogo impostazioni batch**  
 |Proprietà|Description|  
|--------------|-----------------|  
|**Ordine di elaborazione**|Consente di specificare se gli oggetti devono essere elaborati sequenzialmente o in un batch. Se si utilizza l'elaborazione parallela, consente di specificare il numero di oggetti da elaborare simultaneamente.|  
|**Modalità transazione**|Consente di specificare la modalità di transazione per l'elaborazione sequenziale.|  
|**Errori dimensione**|Consente di specificare il funzionamento dell'attività quando si verificano errori.|  
|**Percorso log degli errori di chiave della dimensione**|Consente di specificare il percorso del file nel quale vengono registrati gli errori.|  
|**Elabora oggetti interessati**|Indica se vengono elaborati anche gli oggetti dipendenti o interessati.|  
  
 **Cambia impostazioni**  
 Consente di modificare le opzioni di elaborazione e la gestione degli errori nelle chiavi della dimensione.  
  
 **Argomenti correlati:** [Finestra di dialogo Cambia impostazioni &#40;Analysis Services - Dati multidimensionali&#41;](../Topic/Change%20Settings%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Elaborazione Analysis Services &#40;pagina Generale&#41;](../../integration-services/control-flow/analysis-services-processing-task-editor-general-page.md)   
 [Attività Esegui DDL Analysis Services](../../integration-services/control-flow/analysis-services-execute-ddl-task.md)  
  
  