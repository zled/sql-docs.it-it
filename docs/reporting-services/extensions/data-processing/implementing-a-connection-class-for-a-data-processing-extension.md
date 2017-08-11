---
title: Implementazione di una classe di connessione per un'estensione per l'elaborazione dati | Documenti Microsoft
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
- connections [Reporting Services], data processing extensions
- Connection class
- data processing extensions [Reporting Services], connections
ms.assetid: 7047d29e-a2c9-4e6f-ad02-635851a38ed7
caps.latest.revision: 42
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 19f059c0041cc9effc48e0db9c4b5ef1a504d020
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="implementing-a-connection-class-for-a-data-processing-extension"></a>Implementazione di una classe Connection per un'estensione per l'elaborazione dati
  Il **connessione** oggetto rappresenta una connessione al database o una risorsa simile ed è il punto di partenza per gli utenti di un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] estensione per l'elaborazione dati. Rappresenta le connessioni al server di database, sebbene qualsiasi entità con un comportamento simile può essere esposto come un **connessione**.  
  
 Per implementare un **connessione** dell'oggetto, creare una classe che implementa <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> e facoltativamente implementa <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>.  
  
 Nell'implementazione è necessario assicurarsi che prima dell'esecuzione dei comandi venga creata e aperta una connessione. Assicurarsi che l'implementazione richieda ai client di aprire e chiudere le connessioni in modo esplicito, anziché lasciare che l'implementazione apra e chiuda le connessioni in modo implicito per il client. Dopo aver stabilito la connessione, eseguire i controlli di sicurezza. Richiedendo una connessione esistente per le altre classi nell'estensione per l'elaborazione dati di [!INCLUDE[ssRS](../../../includes/ssrs-md.md)], è possibile garantire che vengano sempre eseguiti i controlli di sicurezza quando si utilizza l'origine dati.  
  
 Le proprietà della connessione desiderata vengono rappresentate come stringa di connessione. È consigliabile che l'estensione per l'elaborazione dati di [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] supporti la proprietà <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection.ConnectionString%2A> utilizzando il sistema familiare di coppia nome/valore definito da OLE DB.  
  
> [!NOTE]  
>  **Connessione** gli oggetti sono spesso elevato utilizzo di risorse per ottenere, pertanto è opportuno considerare il pool di connessioni o altre tecniche per risolvere questo problema.  
  
 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> eredita da <xref:Microsoft.ReportingServices.Interfaces.IExtension>. È necessario implementare l'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IExtension> come parte dell'implementazione della classe Connection. L'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IExtension> consente a una classe di implementare un nome di estensione localizzato e di elaborare le informazioni di configurazione specifiche dell'estensione archiviate nel file di configurazione di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Il **connessione** oggetto contiene i <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A> proprietà tramite l'implementazione di <xref:Microsoft.ReportingServices.Interfaces.IExtension>. È consigliabile che le estensioni per l'elaborazione dati di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] supportino la proprietà <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A>, in modo che gli utenti possano visualizzare un nome familiare e localizzato per l'estensione in un'interfaccia utente, ad esempio Gestione report.  
  
 <xref:Microsoft.ReportingServices.Interfaces.IExtension>consente inoltre il **connessione** oggetto da recuperare ed elaborare i dati di configurazione personalizzati archiviati nel file RSReportServer. config. Per ulteriori informazioni sull'elaborazione dei dati di configurazione personalizzati, vedere il metodo <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A>.  
  
 La classe che implementa <xref:Microsoft.ReportingServices.Interfaces.IExtension> non viene scaricata dalla memoria quando vengono scaricate le altre classi delle estensioni per l'elaborazione dati. Per questo motivo, è possibile utilizzare il **estensione** classe per archiviare informazioni sullo stato tra le connessioni o per archiviare i dati che possono essere memorizzati nella cache in memoria. Il **estensione** classe rimane in memoria purché il server di report è in esecuzione.  
  
 È possibile estendere il **connessione** classe per includere il supporto per le credenziali in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] implementando <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>. Quando si implementa il <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.IntegratedSecurity%2A>, <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.UserName%2A>, e <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.Password%2A> le proprietà del <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> interfaccia, si abilita il **la sicurezza integrata** casella di controllo e **Username** e **Password** caselle di testo del **origine dati** finestra di dialogo in Progettazione Report. In questo modo, è possibile consentire a Progettazione report di archiviare e recuperare le credenziali per le origini dati che supportano l'autenticazione. Le credenziali vengono archiviate in modo protetto e utilizzate quando viene eseguito il rendering dei report in modalità di anteprima.  
  
> [!NOTE]  
>  L'implementazione di <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> richiede in modo implicito che vengano implementati i membri delle interfacce <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> e <xref:Microsoft.ReportingServices.Interfaces.IExtension>.  
>   
>  Per un esempio **connessione** implementazione della classe, vedere [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementazione di un'estensione di elaborazione dei dati](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
