---
title: Utilizzando i metodi del servizio Web protetto | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
caps.latest.revision: 36
author: sabotta
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 802070f070222fba573b52bf1f53b2c6eb8ba8b6
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="using-secure-web-service-methods"></a>Utilizzo di metodi del servizio Web protetti
  Alcuni metodi del servizio Web ReportServer possono richiedere una connessione protetta per essere richiamati. I metodi che richiedono una connessione protetta sono determinati dalle **SecureConnectionLevel** nel file RSReportServer. config. Il valore dell'impostazione è un valore intero con un intervallo valido compreso tra 0 e un numero superiore. Nella tabella seguente vengono descritti questi valori.  
  
|Level|Description|  
|-----------|-----------------|  
|**0**|Livello di sicurezza basso. Le chiamate effettuate all'API SOAP di Reporting Services non richiedono una connessione protetta.|  
|Maggiore di **0**|Livello di sicurezza medio. Tutte le chiamate effettuate all'API SOAP di Reporting Services richiedono una connessione protetta.|  
  
 È possibile utilizzare il metodo <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> del servizio Web per restituire un elenco di metodi del servizio Web che richiedono una connessione protetta in base alla configurazione corrente del server di report. In uno scenario SSL è necessario valutare l'elenco di metodi restituiti da <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> e modificare il nome dello schema dell'URI del servizio Web in "https" o "http", a seconda del metodo chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servizio Web ReportServer](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
