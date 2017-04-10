---
title: "Formati di dati per l&#39;importazione o l&#39;esportazione bulk (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-bulk-import-export"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "formati dati [SQL Server], scelta"
  - "importazione in blocco [SQL Server], formati di dati"
ms.assetid: 73fe6741-9437-4b26-b030-28b863e74399
caps.latest.revision: 29
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 29
---
# Formati di dati per l&#39;importazione o l&#39;esportazione bulk (SQL Server)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può accettare dati nel formato dati di tipo carattere o nel formato dati binario nativo. Utilizzare il formato carattere se vengono spostati dati tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un'altra applicazione (ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel) o un altro server di database (ad esempio Oracle o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). È possibile utilizzare il formato nativo unicamente se si trasferiscono dati tra due istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Contenuto dell'argomento:**  
  
-   [Formati di dati per l'importazione o l'esportazione bulk](#ComponentsAndConcepts)  
  
-   [Attività correlate](#RelatedTasks)  
  
##  <a name="ComponentsAndConcepts"></a> Formati di dati per l'importazione o l'esportazione bulk  
 Nella tabella seguente viene indicato quale formato di dati è generalmente appropriato utilizzare in base alla modalità di rappresentazione dei dati e all'origine o destinazione dell'operazione.  
  
|Operazione|Nativo|nativi Unicode|Carattere|carattere Unicode|  
|---------------|------------|--------------------|---------------|-----------------------|  
|Trasferimenti bulk di dati tra più istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite un file di dati che non contiene caratteri estesi o DBCS (Double-Byte Character Set). A meno che non venga utilizzato un file di formato, la definizione delle tabelle deve essere identica.|Sì*|—|—|—|  
|Per le colonne **sql_variant** è consigliabile usare il formato di dati nativo perché, a differenza dei formati carattere o Unicode, mantiene i metadati per ogni valore **sql_variant**.|Sì|—|—|—|  
|Trasferimenti bulk di dati tra più istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite un file di dati contenente caratteri estesi o DBCS.|—|Sì|—|—|  
|Importazione bulk di dati da un file di testo creato da un altro programma.|—|—|Sì|—|  
|Esportazione bulk di dati in un file di testo che verrà utilizzato in un altro programma.|—|—|Sì|—|  
|Trasferimenti bulk di dati tra più istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite un file di dati contenente dati Unicode e che non contiene caratteri estesi o DBCS.|—|—|—|Sì|  
  
 \* Metodo più veloce per l'esportazione in blocco di dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se si usa **bcp**.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Usare il formato nativo per importare o esportare dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Usare il formato carattere per importare o esportare dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Usare il formato Unicode nativo per importare o esportare dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Usare il formato carattere Unicode per importare o esportare dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Importare dati in formato nativo e carattere da versioni precedenti di SQL Server](../../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
## Vedere anche  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Specificare i formati di dati per la compatibilità con bcp &#40;SQL Server&#41;](../../relational-databases/import-export/specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)  
  
  