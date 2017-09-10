---
title: Le classi fondamentali AMO | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- data sources [AMO]
- AMO, database objects
- AMO, server objects
- Analysis Management Objects, server objects
- database objects [AMO]
- Analysis Management Objects, database objects
- AMO, data sources
- Analysis Management Objects, data sources
ms.assetid: 440e9287-53a2-4db3-9481-1d2ceb6e5b5a
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e7a693ab79b1c2478042e5faa3a7e886b686a789
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="amo-fundamental-classes"></a>Classi fondamentali AMO
  Le classi fondamentali rappresentano il punto di partenza per l'utilizzo della libreria AMO (Analysis Management Objects). Tali classi consentono di stabilire l'ambiente per gli altri che verranno utilizzati nell'applicazione. Le classi fondamentali includono gli oggetti <xref:Microsoft.AnalysisServices.Server>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource> e <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
 Nella figura seguente viene illustrata la relazione delle classi descritte in questo argomento.  
  
 ![Le classi fondamentali AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-fundamentalclasses.gif "le classi fondamentali AMO")  
  
 In questo argomento sono incluse le sezioni seguenti:  
  
-   [Oggetti server](#ServerObjects)  
  
-   [Oggetti di database](#DatabaseObjects)  
  
-   [Oggetti DataSource e DataSourceView](#DSandDSV)  
  
##  <a name="ServerObjects"></a>Oggetti server  
 Sarà inoltre possibile accedere ai metodi seguenti:  
  
-   Gestione della connessione: Connect, Disconnect, Reconnect e GetConnectionState.  
  
-   Gestione delle transazioni: BeginTransaction, CommitTransaction e RollbackTransaction.  
  
-   Backup e Restore.  
  
-   Esecuzione di istruzioni DDL: Execute, CancelCommand, SendXmlaRequest e StartXmlaRequest.  
  
-   Gestione di metadati: UpdateObjects e Validate.  
  
 Per connettersi a un server, è necessario utilizzare una stringa di connessione, analogamente ad ADOMD.NET e OLE DB. Per ulteriori informazioni, vedere <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>. Il nome del server può essere specificato come una stringa di connessione senza che sia necessario utilizzare un formato della stringa di connessione.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Server> in <xref:Microsoft.AnalysisServices>.  
  
##  <a name="DatabaseObjects"></a>Oggetti di database  
 Per utilizzare un oggetto <xref:Microsoft.AnalysisServices.Database> nell'applicazione, è necessario ottenere un'istanza del database dalla raccolta di database del server padre. Per creare un database, aggiungere un oggetto <xref:Microsoft.AnalysisServices.Database> a una raccolta di database del server e aggiornare la nuova istanza al server. Per eliminare un database, eliminare l'oggetto <xref:Microsoft.AnalysisServices.Database> tramite il relativo metodo Drop.  
  
 È possibile eseguire il backup di database tramite il metodo Backup (dell'oggetto <xref:Microsoft.AnalysisServices.Database> o dell'oggetto <xref:Microsoft.AnalysisServices.Server>), mentre è possibile eseguirne il ripristino solo dall'oggetto <xref:Microsoft.AnalysisServices.Server> tramite il metodo Restore.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Database> in <xref:Microsoft.AnalysisServices>.  
  
##  <a name="DSandDSV"></a>Oggetti DataSource e DataSourceView  
 Le origini dati vengono gestite tramite l'oggetto <xref:Microsoft.AnalysisServices.DataSourceCollection> della classe di database. Per creare un'istanza di <xref:Microsoft.AnalysisServices.DataSource>, è possibile utilizzare il metodo Add di un oggetto <xref:Microsoft.AnalysisServices.DataSourceCollection>, mentre per eliminare un'istanza di <xref:Microsoft.AnalysisServices.DataSource> è possibile utilizzare il metodo Remove di un oggetto <xref:Microsoft.AnalysisServices.DataSourceCollection>.  
  
 Gli oggetti <xref:Microsoft.AnalysisServices.DataSourceView> vengono gestiti dall'oggetto <xref:Microsoft.AnalysisServices.DataSourceViewCollection> nella classe di database.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.DataSource> e <xref:Microsoft.AnalysisServices.DataSourceView> in <xref:Microsoft.AnalysisServices>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices>   
 [Introduzione a classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Programmazione di oggetti fondamentale AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-fundamental-objects.md)  
  
  
