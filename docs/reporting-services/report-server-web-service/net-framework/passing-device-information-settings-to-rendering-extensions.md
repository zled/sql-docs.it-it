---
title: Il passaggio di impostazioni informazioni dispositivo a estensioni di Rendering | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
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
- device information settings [Reporting Services]
- Render method
- Report Server Web service, device information settings
- Web service [Reporting Services], device information settings
- XML Web service [Reporting Services], device information settings
- passing device information [Reporting Services]
- rendering extensions [Reporting Services], device information settings
- rendering [Reporting Services], settings
- device information settings [Reporting Services], about device information settings
- extensions [Reporting Services], device information settings
ms.assetid: fe718939-7efe-4c7f-87cb-5f5b09caeff4
caps.latest.revision: 47
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: dfbc65590c676278c89ca2646dae0d347abcd3ee
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="passing-device-information-settings-to-rendering-extensions"></a>Passaggio delle impostazioni relative alle informazioni sul dispositivo alle estensioni per il rendering
  In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]le impostazioni relative alle informazioni sul dispositivo vengono usate per passare i parametri di rendering a un'estensione per il rendering. Le impostazioni nel servizio Web ReportServer vengono passate come elemento XML **DeviceInfo** ed elaborate dal server di report. Poiché le impostazioni delle informazioni sul dispositivo dispongono di valori predefiniti, sono considerate argomenti facoltativi nel processo di rendering. È tuttavia possibile usare le impostazioni delle informazioni sul dispositivo per personalizzare il rendering ed eseguire l'override dei valori predefiniti forniti dal server.  
  
 È possibile specificare le impostazioni delle informazioni sul dispositivo in vari modi. A livello di codice è possibile usare il metodo Render. Se si accede a un report tramite il relativo URL, è possibile specificare le informazioni sul dispositivo come parametri URL. È inoltre possibile modificare le impostazioni sulle informazioni sul dispositivo nei file di configurazione di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] per specificare a livello globale i parametri di rendering. Per ulteriori informazioni su come specificare i parametri di rendering a livello globale, vedere [personalizzare i parametri di estensione per il Rendering in RSReportServer. config](../../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md).  
  
## <a name="passing-device-information-using-the-render-method"></a>Passaggio di informazioni sul dispositivo tramite il metodo Render  
 To pass device information settings to a rendering extension, use the **M:Microsoft.WSSUX.ReportingServicesWebService.RSExecutionService2005.ReportExecutionService.Render(System.String,System.String,System.String@,System.String@,System.String@,Microsoft.WSSUX.ReportingServicesWebService.RSExecutionService2005.Warning[]@,System.String[]@)** method. La stringa XML seguente, ad esempio, può essere passata per il <xref:ReportExecution2005.ReportExecutionService.Render%2A> metodo per creare un frammento HTML durante il rendering in HTML.  
  
```  
<DeviceInfo>  
   <HTMLFragment>True</HTMLFragment>  
</DeviceInfo>  
```  
  
 Quando viene eseguito il rendering di un report come frammento HTML, il contenuto del report si trova all'interno di un elemento TABLE senza l'utilizzo di un elemento HTML o BODY. È possibile usare il frammento HTML per incorporare il report in un documento HTML esistente. Per altre informazioni sulle impostazioni delle informazioni sul dispositivo per l'output HTML, vedere [HTML Device Information Settings](../../../reporting-services/html-device-information-settings.md).  
  
## <a name="passing-device-information-using-url-access"></a>Passaggio delle informazioni sul dispositivo con accesso tramite URL  
 È inoltre possibile passare le impostazioni delle informazioni sul dispositivo con accesso tramite URL. Le impostazioni relative alle informazioni sul dispositivo vengono passate come parametri URL. È possibile passare al server di report la stringa di accesso tramite URL per generare un report visualizzabile senza la barra degli strumenti del visualizzatore HTML.  
  
```  
http://<Server Name>/reportserver?/SampleReports/Sales Order Detail&rs:Command=Render&rs:Format=HTML4.0&rc:Toolbar=False  
```  
  
 Per ulteriori informazioni, vedere [specificare Device Information Settings in un URL](../../../reporting-services/specify-device-information-settings-in-a-url.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni del dispositivo per il Rendering delle estensioni &#40; Reporting Services &#41;](../../../reporting-services/device-information-settings-for-rendering-extensions-reporting-services.md)   
 [Personalizzare i parametri di estensione per il Rendering in RSReportServer. config](../../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
