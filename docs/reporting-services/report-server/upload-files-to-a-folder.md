---
title: "Caricare file in una cartella | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pubblicazione di report [Reporting Services], caricamento di file"
  - "report [Reporting Services], pubblicazione"
  - "caricamento di report [Reporting Services]"
  - "caricamento di file [Reporting Services]"
  - "file [Reporting Services], caricamento"
  - "file [Reporting Services]"
  - "cartelle [Reporting Services], caricamento di file"
ms.assetid: 2f99a288-d4aa-4c64-b310-e457a2aef2c5
caps.latest.revision: 42
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 42
---
# Caricare file in una cartella
  È possibile caricare file dal file system e archiviarli come elementi gestiti in un database del server di report. La funzionalità di un file caricato dipende dal tipo di file.  
  
-   Il caricamento di un file con estensione rdl equivale alla pubblicazione di un report.  
  
-   Qualsiasi altro tipo di file caricato viene aggiunto al database del server di report come singolo oggetto binario. I file vengono pubblicati in un server di report come risorse e possono essere file di qualsiasi tipo. Se l'estensione del file corrisponde a un tipo MIME noto, viene utilizzata un'icona specifica per identificare il tipo di risorsa. In caso contrario, la risorsa viene indicata da un'icona di file generico.  
  
> [!NOTE]  
>  Non è possibile caricare un file di origine dei dati del report con estensione rds per creare un'origine dei dati condivisa. Un file con estensione rds viene utilizzato solo in Progettazione report. Tale file non fornisce il contenuto per un elemento dell'origine dati condivisa definito e gestito tramite Gestione report. In alternativa al caricamento è possibile creare uno script per la creazione di un'origine dei dati condivisa in base a un file con estensione rds.  
  
 La dimensione massima del file per gli elementi caricati è stabilita da [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. Per impostazione predefinita, il valore per la dimensione massima è pari a 4 MB.  
  
 I file caricati in un database del server di report sono visualizzati nella gerarchia di cartelle con le icone seguenti.  
  
 ![Icona di report](../../reporting-services/report-server/media/hlp-16doc.png "Icona di report")  
Icona di report  
  
 ![Icona di modello](../../reporting-services/report-server/media/model-icon.png "Icona di modello")  
Icona di modello di report  
  
 ![Icona di risorsa generica](../../reporting-services/report-server/media/hlp-16file.png "Icona di risorsa generica")  
Icona di risorsa generica  
  
 I file caricati vengono inseriti automaticamente nella cartella selezionata. È pertanto possibile passare alla cartella desiderata prima di caricare il file oppure spostare il file nella cartella desiderata dopo averlo caricato.  
  
 Per caricare un file, utilizzare Gestione report La possibilità o meno di caricare file in un server di report dipende dalle attività incluse nell'assegnazione di ruolo. Se vengono utilizzate le impostazioni di sicurezza predefinite, gli amministratori locali possono aggiungere elementi a un server di report. Se è attivata la funzionalità Report personali, qualsiasi utente con una cartella Report personali disporrà dell'autorizzazione per caricare elementi in quella cartella. Se si utilizzano assegnazioni di ruolo personalizzate, tali assegnazioni devono includere attività che supportano la gestione delle cartelle.  
  
|Per|Includere queste attività|  
|----------------|-------------------------|  
|Caricamento di un file con estensione rdl in una cartella|Gestione di report|  
|Caricamento di qualsiasi file come oggetto binario|Gestione di risorse|  
|Visualizzazione del contenuto di una cartella|Visualizzazione di risorse, Visualizzazione di report|  
  
## Vedere anche  
 [Gestione report &#40;modalità nativa SSRS&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)   
 [Concessione di autorizzazioni in un server di report in modalità nativa](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [Attività e autorizzazioni](../../reporting-services/security/tasks-and-permissions.md)   
 [Caricare un file o un report &#40;Gestione report&#41;](../../reporting-services/reports/upload-a-file-or-report-report-manager.md)  
  
  