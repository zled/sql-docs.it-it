---
title: "Partizionamento con le tabelle temporali | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "04/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 313714b8-4ad1-4c14-93a3-7f628a334a51
caps.latest.revision: 11
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 11
---
# Partizionamento con le tabelle temporali
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  È possibile usare il partizionamento in modo indipendente nella tabella di cronologia e in quella corrente. Tuttavia, il partizionamento non può essere usato per modificare il contenuto dei dati senza il controllo delle versioni di sistema.  
  
> [!NOTE]  
>  Il partizionamento è una funzionalità di Enterprise Edition.  
  
-   **Tabella corrente:**  
  
    -   L'operazione **SWITCH IN** nella tabella corrente può essere usata per facilitare il caricamento di dati e l'esecuzione di query quando **SYSTEM_VERSIONING** è **ON**  
  
    -   L'operazione **SWITCH OUT** non è consentita mentre **SYSTEM_VERSIONING** è **ON**  
  
-   **Tabella di cronologia:**  
  
    -   L'operazione **SWITCH OUT** dalla tabella di cronologia può essere eseguita mentre **SYSTEM_VERSIONING** è **ON** per ripulire porzioni di dati di cronologia non più rilevanti.  
  
    -   L'operazione **SWITCH IN** non è consentita quando **SYSTEM_VERSIONING** è **ON** perché può invalidare la coerenza dei dati temporali.  
  
## Questo articolo è stato utile? Commenti e suggerimenti  
 Quali informazioni si stanno cercando? La ricerca ha restituito i risultati desiderati? Microsoft incoraggia gli utenti a inviare i propri commenti per migliorare i contenuti Inviare eventuali commenti all'indirizzo [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Partitioning%20with%20Temporal%20Tables%20page)  
  
## Vedere anche  
 [Tabelle temporali](../../relational-databases/tables/temporal-tables.md)   
 [Introduzione alle tabelle temporali con controllo delle versioni di sistema](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Verifiche di coerenza del sistema della tabella temporale](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Considerazioni e limitazioni delle tabelle temporali](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [Sicurezza di una tabella temporale](../../relational-databases/tables/temporal-table-security.md)   
 [Gestire la conservazione dei dati cronologici nelle tabelle temporali con controllo delle versioni di sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Tabelle temporali con controllo delle versioni di sistema con tabelle con ottimizzazione per la memoria](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Funzioni e viste per i metadati delle tabelle temporali](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  