---
title: "Prerequisiti per le procedure dettagliate per l&#39;analisi scientifica dei dati (SQL Server R Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 0b0582b8-8843-4787-94a8-2e28bdc04fb2
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Prerequisiti per le procedure dettagliate per l&#39;analisi scientifica dei dati (SQL Server R Services)
È consigliabile eseguire le procedure dettagliate in una workstation R che possa connettersi a un computer con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sulla stessa rete. È anche possibile eseguire la procedura dettagliata in un computer che abbia sia [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che l'ambiente di sviluppo R. 
  
  
## <a name="install-sql-server-2016-r-services-in-database"></a>Installare SQL Server 2016 R Services (In-Database)  
È necessario avere accesso a un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] installato. Per altre informazioni sulla configurazione di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], vedere [Configurare SQL Server R Services (In-Database](https://msdn.microsoft.com/library/mt696069.aspx).  
  
  
> [!IMPORTANT]  
> Assicurarsi di usare [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] o versione successiva. Le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supportano l'integrazione con R. Tuttavia, è possibile usare i database SQL precedenti come origine dati ODBC.  
  
## <a name="install-an-r-development-environment"></a>Installare un ambiente di sviluppo R  
Per completare questa procedura dettagliata nel computer, è necessario un ambiente di sviluppo R o qualsiasi altro strumento da riga di comando che consenta di eseguire comandi di R.    
  
- **R Tools per Visual Studio** è un plug-in gratuito che offre Intellisense, debug e supporto per Microsoft R Server e SQL Server R Services. Per scaricarlo, vedere [R Tools per Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx).  
    
- **Microsoft R Client** è uno strumento di sviluppo leggero che supporta lo sviluppo in R con i pacchetti ScaleR. Per ottenerlo, vedere [Introduzione a Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started).
  
- **RStudio** è uno degli ambienti più diffusi per lo sviluppo di R. Per altre informazioni, vedere [https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/).  
  
    Tuttavia, non è possibile completare questa esercitazione usando un'installazione generica di RStudio o di un altro ambiente. È anche necessario installare i pacchetti R e le librerie di connettività per Microsoft R Open. Per altre informazioni, vedere [Configurare un client per l'analisi scientifica dei dati](https://msdn.microsoft.com/library/mt696067.aspx).  

- Quando si installa [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)], per impostazione predefinita vengono installati gli strumenti di R, ad esempio R.exe, RTerm.exe, RScripts.exe. Se non si vuole installare un IDE, è possibile usare questi strumenti.  
  
  
## <a name="get-permissions-to-connect-to-sql-server"></a>Ottenere le autorizzazioni per connettersi a SQL Server  
In questa procedura dettagliata verrà stabilità la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire gli script e caricare i dati. A tale scopo, è necessario avere un account di accesso valido nel server di database.  È possibile usare un account di accesso SQL o un'autenticazione integrata di Windows. Chiedere all'amministratore del database di creare un account nel server con i privilegi seguenti nel database in cui sarà usato R:  
  
-   Creare database, tabelle, funzioni e stored procedure    
-   Inserire dati in una tabella  
  
  
## <a name="start-the-walkthrough"></a>Avviare la procedura dettagliata  
[Lezione 1: Preparare i dati &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
