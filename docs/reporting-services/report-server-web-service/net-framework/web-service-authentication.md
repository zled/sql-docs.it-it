---
title: L'autenticazione del servizio Web | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 5e15fa8674a09821becd437e78cfb0bb472e3bc8
ms.openlocfilehash: 37ad9a54e400dbf011d21ecf7227509f33af49da
ms.contentlocale: it-it
ms.lasthandoff: 11/07/2017

---
# <a name="web-service-authentication"></a>Autenticazione del servizio Web
  Per autenticare le chiamate effettuate al servizio Web ReportServer, è possibile utilizzare l'autenticazione di Windows o l'autenticazione di base. Qualsiasi client che effettua richieste SOAP al server di report deve implementare la parte client di uno dei protocolli di autenticazione supportati. Se si utilizza il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], è possibile utilizzare le classi HTTP di codice gestito per implementare l'autenticazione. L'utilizzo di queste API semplifica l'invio delle informazioni di autenticazione insieme alle richieste SOAP.  
  
 Se non si dispone delle credenziali appropriate prima di effettuare una chiamata al servizio Web ReportServer, la chiamata ha esito negativo. In fase di esecuzione, è possibile passare le credenziali al servizio Web impostando la **credenziali** proprietà dell'oggetto che rappresenta il servizio Web prima di chiamare i metodi sul lato client.  
  
 Nelle sezioni seguenti sono inclusi esempi di codice per l'invio delle credenziali utilizzando [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="windows-authentication"></a>Autenticazione di Windows  
 Nel codice seguente vengono passate le credenziali di Windows al servizio Web.  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
ReportingService rs = new ReportingService();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
```  
  
## <a name="basic-authentication"></a>Autenticazione di base  
 Nel codice seguente vengono passate le credenziali di base al servizio Web.  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = New System.Net.NetworkCredential("username", "password", "domain")  
```  
  
```csharp  
ReportingService service = new ReportingService();  
service.Credentials = new System.Net.NetworkCredential("username", "password", "domain");  
```  
  
 Le credenziali devono essere impostate prima di chiamare i metodi del servizio Web ReportServer. Se non si impostano le credenziali, viene visualizzato il codice di errore Errore HTTP 401: Accesso negato. È necessario autenticare il servizio prima di utilizzarlo, ma dopo aver impostato le credenziali, non è necessario impostare nuovamente, purché si continua a utilizzare la stessa variabile di servizio (ad esempio *rs*).  
  
## <a name="custom-authentication"></a>Autenticazione personalizzata  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] include un'API di programmazione che consente agli sviluppatori di progettare e sviluppare estensioni di autenticazione personalizzate, note come estensioni di sicurezza. Per ulteriori informazioni, vedere [Implementing a Security Extension](../../../reporting-services/extensions/security-extension/implementing-a-security-extension.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servizio Web ReportServer](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  

