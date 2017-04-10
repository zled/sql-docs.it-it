---
title: "Lezione 2: Specifica delle informazioni di connessione (Reporting Services) | Microsoft Docs"
ms.custom: ""
ms.date: "05/23/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
caps.latest.revision: 53
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 51
---
# Lezione 2: Specifica delle informazioni di connessione (Reporting Services)
Dopo aver aggiunto un report al progetto Tutorial, è necessario definire un'*origine dati*, vale a dire informazioni di connessione usate dal report per accedere ai dati da un database relazionale, da un database multidimensionale o da un'altra risorsa.  
  
In questa lezione verrà usato come origine dati il database di esempio [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)]. L'esercitazione presuppone che il database si trovi in un'istanza predefinita del [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] di [!INCLUDE[ssDE](../includes/ssde-md.md)] installata nel computer locale.  
  
### Per impostare una connessione  
  
1.  Nel riquadro **Dati report**, fare clic su **Nuova**, quindi su **Origine dati**.  
Se il riquadro **Dati report** non è visualizzato, scegliere **Dati report** dal menu **Visualizza**.  
  
   2.  Nella casella **Nome** digitare *Adventureworks2014*.  
  
3.  Accertarsi che sia selezionata l'opzione **Connessione incorporata**.  
  
4.  In **Tipo** selezionare **Microsoft SQL Server**.  
  
5.  In **Stringa di connessione** digitare quanto segue:  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2014  
    ```  
  
Per questa stringa di connessione si presuppone che [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], il server di report e il database [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] siano installati nel computer locale e che si disponga dell'autorizzazione per l'accesso al database [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)]. Se il database AdventureWorks2014 non è presente nel computer locale, modificare la stringa di connessione e sostituire *localhost* con il nome dell'istanza del server di database.
   
  
 > [!NOTE]  
 > Se si utilizza [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services oppure un'istanza denominata, è necessario includere nella stringa di connessione le informazioni sull'istanza:  
 >   
 > `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2014`  
 >   
 > Per altre informazioni sulle stringhe di connessione, vedere:  
 > *  [Data Connections, Data Sources, and Connection Strings in Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
    > * [Finestra di dialogo Proprietà origine dati, Generale](../Topic/Data%20Source%20Properties%20Dialog%20Box,%20General.md)  
        
  
6.  Fare clic su **Credenziali** nel riquadro sinistro e selezionare **Usa autenticazione di Windows (sicurezza integrata)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] L'origine dati [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] verrà aggiunta al riquadro **Dati report**.  
![ssrs_adventureworks_datasource](../reporting-services/media/ssrs-adventureworks-datasource.png)  
## Attività successiva  
È stata definita correttamente una connessione al database di esempio [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)]. Verrà successivamente creato il report. Vedere [Lezione 3: Definizione di un set di dati per il report tabella &#40;Reporting Services&#41;](../reporting-services/lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## Vedere anche  
[Finestra di dialogo Proprietà origine dati, Generale](../Topic/Data%20Source%20Properties%20Dialog%20Box,%20General.md)  
[Data Connections, Data Sources, and Connection Strings in Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
  
