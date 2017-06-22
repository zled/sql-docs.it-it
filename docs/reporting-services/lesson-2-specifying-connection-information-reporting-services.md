---
title: 'Lezione 2: Specifica le informazioni di connessione (Reporting Services) | Documenti Microsoft'
ms.custom: 
ms.date: 05/23/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
caps.latest.revision: 53
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 4d0667dec1b59d5560ca24176634dddc5d6d8d18
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Lezione 2: Specifica delle informazioni di connessione (Reporting Services)
Dopo aver aggiunto un [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] impaginati report al progetto Tutorial nella lezione 1, è necessario definire un *origine dati*, ovvero le informazioni di connessione, il report utilizza per accedere ai dati da un database relazionale, database multidimensionale o un'altra origine.  
  
In questa lezione, utilizza il [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] database di esempio come origine dati. In questa esercitazione si presuppone che il database si trovi in un'istanza predefinita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] installato nel computer locale.  
  
### <a name="to-set-up-a-connection"></a>Per impostare una connessione  
  
1.  Nel riquadro **Dati report** , fare clic su **Nuova** , quindi su **Data Source**.  
Se il riquadro **Dati report** non è visualizzato, scegliere **Dati report** dal menu **Visualizza**.  

    ![SSRS-Table-Tutorial-2-New-Data-Source](../reporting-services/media/ssrs-table-tutorial-2-new-data-source.png)
  
   2.  Nella casella **Nome**digitare *AdventureWorks2014*.  
  
3.  Accertarsi che sia selezionata l'opzione **Connessione incorporata** .  
  
4.  In **Tipo**selezionare **Microsoft SQL Server**.  
  
5.  In **Stringa di connessione**digitare quanto segue:  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2014  
    ```  
  
     Per questa stringa di connessione si presuppone che [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], il server di report e il database [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] siano installati nel computer locale e che si disponga dell'autorizzazione per l'accesso al database [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] . Se il database AdventureWorks2014 non è presente nel computer locale, modificare la stringa di connessione e sostituire *localhost* con il nome dell'istanza del server di database.
  
     >[!NOTE]  
    >Se si utilizza [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services oppure un'istanza denominata, è necessario includere nella stringa di connessione le informazioni sull'istanza:  
    >  
    >`Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2014`  
    >  
    >Per altre informazioni sulle stringhe di connessione, vedere: [Data Connections, Data Sources, and Connection Strings in Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
     
  
6.  Fare clic su **Credenziali** nel riquadro sinistro e selezionare **Usa autenticazione di Windows (sicurezza integrata)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] L'origine dati **AdventureWorks2014** verrà aggiunta al riquadro **Dati report** .  
![ssrs_adventureworks_datasource](../reporting-services/media/ssrs-adventureworks-datasource.png)  
## <a name="next-task"></a>Attività successiva  
È stata definita correttamente una connessione al database di esempio [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] . Verrà successivamente creato il report. Vedere [Lezione 3: Definizione di un set di dati per il report tabella &#40;Reporting Services&#41;](../reporting-services/lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## <a name="see-also"></a>Vedere anche  
[Data Connections, Data Sources, and Connection Strings in Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
  


