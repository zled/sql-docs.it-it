---
title: "Eseguire un file script di Reporting Services | Microsoft Docs"
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
  - "script [Reporting Services], esecuzione"
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
caps.latest.revision: 36
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 36
---
# Eseguire un file script di Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] - I file script vengono eseguiti dal prompt dei comandi usando l'ambiente di script di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (RS.exe). RS.exe dispone di molti argomenti del prompt dei comandi disponibili per l'utilizzo. Per altre informazioni sulle opzioni del prompt dei comandi, vedere [Utilità RS.exe &#40;SSRS&#41;](../../reporting-services/tools/rs-exe-utility-ssrs.md). Per altri esempi di script, vedere [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## Esempi di righe di comando  
  
-   Eseguire Script.rss nell'ambiente di script che definisce il server di report di destinazione. Per impostazione predefinita, viene applicata l'autenticazione di Windows:  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver  
    ```  
  
-   Eseguire Script.rss nell'ambiente di script che specifica un nome utente e una password per l'autenticazione delle chiamate al servizio Web:  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   Eseguire Script.rss nell'ambiente di script che specifica un timeout del server di 30 secondi:  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver -l 30  
    ```  
  
-   Eseguire Script.rss nell'ambiente di script che specifica una variabile globale degli script denominata *report*.  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver -v report="Company Sales"  
    ```  
  
-   Eseguire Script.rss nell'ambiente di script che specifica che le operazioni del servizio Web nel file script vengono eseguite come batch.  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver -b  
    ```  
  
## Vedere anche  
 [Riferimento tecnico &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  