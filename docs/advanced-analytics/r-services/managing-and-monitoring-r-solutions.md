---
title: "Gestione e monitoraggio di soluzioni R | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d455f22a-190f-4a28-9088-98a843cd5db2
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# Gestione e monitoraggio di soluzioni R
  Gli amministratori del database devono integrare progetti e priorità in concorrenza all'interno di un singolo punto di contatto: il server di database. È necessario specificare l'accesso ai dati non solo per gli esperti, ma per un'ampia gamma di sviluppatori di report, analisti aziendali e fruitori dei dati aziendali, mantenendo l'integrità degli archivi dei dati operativi e dei report. Nell'organizzazione, l'amministratore di database è una parte fondamentale della compilazione e distribuzione di un'infrastruttura efficace per la scienza dei dati. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre numerosi vantaggi per l'amministratore di database che supporta il ruolo di analisi scientifica dei dati.  
  
-   **Sicurezza.** L'architettura di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] mantiene i database protetto e isola l'esecuzione di sessioni R dall'operazione dell'istanza del database.  
  
     È possibile specificare gli utenti autorizzati a eseguire gli script R e verificare che i dati usati nei processi R siano gestiti tramite gli stessi ruoli di sicurezza definiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Affidabilità:** le sessioni R vengono eseguite in un processo separato per garantire che il server continui a funzionare normalmente anche in caso di problemi della sessione R. Gli account utente fisico con privilegi limitati vengono utilizzati per contenere e isolare le istanze di R.   
  
-   **Governance delle risorse:** È anche possibile tenere sotto controllo la quantità di risorse allocate al runtime di R, per evitare che calcoli di grande entità possano compromettere le prestazioni complessive del server.  
  
  
## Argomenti della sezione  
 [Monitoraggio dei servizi di R](../../advanced-analytics/r-services/monitoring-r-services.md)
 
 [Governance delle risorse per i servizi di R](../../advanced-analytics/r-services/resource-governance-for-r-services.md)
 
[Installazione e gestione dei pacchetti R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md)
  
[Configurazione](../../advanced-analytics/r-services/configuration-sql-server-r-services.md) 

+ [Configurare e gestire Advanced Analytics Extensions](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md)  
  
+  [Modificare il pool di account utente per SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)  

 [Considerazioni sulla sicurezza per il runtime R in SQL Server](../../advanced-analytics/r-services/security-considerations-for-the-r-runtime-in-sql-server.md)  
  
 
  
## Vedere anche  
 [Caratteristiche e attività di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)  
  
  