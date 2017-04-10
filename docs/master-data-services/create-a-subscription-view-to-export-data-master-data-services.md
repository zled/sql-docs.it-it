---
title: "Creare una vista sottoscrizioni per esportare i dati (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "viste sottoscrizioni [Master Data Services], creazione"
  - "creazione di viste sottoscrizioni [Master Data Services]"
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Creare una vista sottoscrizioni per esportare i dati (Master Data Services)
  Creare una vista sottoscrizioni per esportare dati di Master Data Services nei sistemi di sottoscrizione Si sta creando una vista dei dati all'interno di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione di accesso di **Gestione integrazione** area funzionale. Per ulteriori informazioni, vedere [autorizzazioni per aree funzionali & #40; Master Data Services & #41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   È necessario essere un amministratore del modello. Per ulteriori informazioni, vedere [amministratori & #40; Master Data Services & #41;](../master-data-services/administrators-master-data-services.md).  
  
### Per creare e modificare una vista sottoscrizioni  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Gestione integrazione**.  
  
2.  Dalla barra dei menu, fare clic su **Crea viste**.  
  
3.  Nel **viste sottoscrizioni** pagina, fare clic su **Aggiungi** per creare una vista oppure fare clic su **modificare** per modificare una vista. Viene visualizzato un pannello sulla destra.  
  
4.  Nel **Crea vista sottoscrizioni** riquadro, nel **nome** digitare un nome per la visualizzazione.  
  
     Nel **Modifica vista sottoscrizioni** riquadro, nel **nome** digitare il nome aggiornato per la visualizzazione.  
  
5.  Da di **modello** selezionare un modello di elenco.  
  
6.  Selezionare **includono membri eliminato**, includere i membri eliminato nella vista.  
  
7.  Selezionare l'opzione **versione** o **Flag di versione** in **le opzioni della versione**, quindi selezionare dall'elenco corrispondente.  
  
    > [!TIP]  
    >  Creare una vista sottoscrizioni basata su un flag di versione. Quando si blocca una versione, è possibile riassegnare il flag a una versione aperta senza aggiornare la vista sottoscrizioni.  
  
8.  Selezionare l'opzione **entità** o **gerarchia derivata** nel **origini dati** opzione e quindi selezionare dall'elenco corrispondente.  
  
9. Dal **formato** selezionare un formato di visualizzazione di sottoscrizione.  
  
10. Se si sceglie **livelli espliciti** o **livelli derivati** dal **formato** elenco, digitare il numero di livelli della gerarchia da includere nella vista.  
  
11. Fare clic su **Salva**.  
  
## Visualizzare informazioni  
 Per ogni vista creata, viene aggiunta alla griglia una riga con dieci colonne. La tabella seguente descrive le colonne.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|Stato|Stato della vista.<br /><br /> Quando fa clic su **salvare**,  ![Icon for updating status](../master-data-services/media/mds-statusicon-updating.png "Icon for updating status") consente di visualizzare, che indica che sta aggiornando la visualizzazione di immagini.<br /><br /> Se si verificano errori durante la creazione o modifica di una vista, il ![Icon for error status](../master-data-services/media/mds-statusicon-error.png "Icon for error status") immagine viene visualizzata.<br /><br /> In caso contrario, lo stato è OK e ![Icon for OK status](../master-data-services/media/mds-statusicon-ok.png "Icon for OK status") immagine viene visualizzata.|  
|Nome|Nome della vista sottoscrizioni.|  
|Modello|Nome del modello.|  
|Version|Nome della versione.|  
|Flag versione|Nome del flag di versione.|  
|Gerarchie derivata|Nome della gerarchia derivata.|  
|Entità|Nome dell'entità.|  
|Formato|Specifica il tipo di dati nella vista.|  
|Level|Specifica il numero di livelli nella vista, che viene usato solo per i formati di vista di livello esplicito o derivato|  
|Includi membri eliminati|Indica se nella vista sono inclusi i membri eliminati temporaneamente.|  
  
 Quando si fa clic su una vista, vengono visualizzate le informazioni seguenti.  
  
-   **Creato da**: il nome dell'utente che ha creato la vista.  
  
-   **In**: la data e ora di creazione della visualizzazione.  
  
-   **Aggiornato da**: il nome dell'utente che ha aggiornato la visualizzazione.  
  
-   **In**: la data e l'ora dell'ultimo aggiornamento della visualizzazione.  
  
## Vedere anche  
 [Panoramica: Esportazione di dati e 40 #; Master Data Services & #41;](../master-data-services/overview-exporting-data-master-data-services.md)   
 [Eliminare una vista sottoscrizioni & #40; Master Data Services & #41;](../master-data-services/delete-a-subscription-view-master-data-services.md)   
 [Creare un Flag di versione & #40; Master Data Services & #41;](../master-data-services/create-a-version-flag-master-data-services.md)  
  
  