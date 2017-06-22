---
title: Implementazione dell'interfaccia IRenderingExtension | Documenti Microsoft
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
- IRenderingExtension interface
- rendering extensions [Reporting Services], IRenderingExtension interface
ms.assetid: 74b2f2b7-6796-42da-ab7d-b05891ad4001
caps.latest.revision: 43
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 3b5772901cfaabedab1b42db39dcd85c49119509
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="implementing-the-irenderingextension-interface"></a>Implementazione dell'interfaccia IRenderingExtension
  L'estensione per il rendering prende i risultati da una definizione del report combinata con i dati effettivi ed eseguire il rendering dei dati risultanti in un formato che sia possibile utilizzare. La trasformazione dei dati combinati e della formattazione viene eseguita tramite una classe CLR (Common Language Runtime) che implementa <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>. Ciò consente di trasformare il modello a oggetti in un formato di output che può essere utilizzato da un visualizzatore, una stampante o un'altra destinazione di output.  
  
 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> dispone di tre metodi che devono essere codificati:  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A>: consente di eseguire il rendering del report.  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A>: consente di eseguire il rendering di un flusso specifico dal report.  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A>: consente di ottenere informazioni aggiuntive, come icone, necessarie per il report.  
  
 Nelle sezioni seguenti questi metodi vengono descritti in modo più dettagliato.  
  
## <a name="render-method"></a>Metodo Render  
 Il metodo <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> contiene argomenti che rappresentano gli oggetti seguenti:  
  
-   Il *report* che si desidera eseguire il rendering. Questo oggetto contiene proprietà, dati e informazioni sul layout per il report. Il report costituisce la radice dell'albero del modello a oggetti del report.  
  
-   Il *ServerParameters* che contengono l'oggetto dizionario di stringhe con i parametri per il server di report, se presente.  
  
-   Il *deviceInfo* parametro contenenti le impostazioni del dispositivo. Per ulteriori informazioni, vedere [passando Device Information Settings per estensioni per il Rendering](../../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
-   Il *clientCapabilities* parametro che contiene un <xref:System.Collections.Specialized.NameValueCollection> oggetto dizionario che contiene informazioni sul client a cui si esegue il rendering.  
  
-   Il *RenderProperties* che contiene informazioni sul risultato del rendering.  
  
-   Il *createAndRegisterStream* è una funzione di delegato deve essere chiamato per ottenere un flusso per il rendering in.  
  
### <a name="deviceinfo-parameter"></a>Parametro deviceInfo  
 Il *deviceInfo* parametro contiene i parametri di rendering, non i parametri di report. Questi parametri vengono passati all'estensione per il rendering. Il *deviceInfo* valori vengono convertiti in un <xref:System.Collections.Specialized.NameValueCollection> oggetto dal server di report. Gli elementi nel *deviceInfo* parametro vengono trattati come valori tra maiuscole e minuscole. Se la richiesta di rendering deriva da URL di accesso, i parametri URL nel formato `rc:key=value` vengono convertiti in coppie chiave/valore di *deviceInfo* oggetto dizionario. Il codice di rilevamento del browser fornisce inoltre gli elementi seguenti nel *clientCapabilities* dizionario: EcmaScriptVersion, JavaScript, MajorVersion, MinorVersion, Win32, tipo e AcceptLanguage. Qualsiasi coppia di nome/valore di *deviceInfo* parametro che non compresa dall'estensione per il rendering viene ignorato. Nell'esempio di codice seguente viene illustrato un metodo <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> di esempio per il recupero delle icone:  
  
```csharp  
public void GetRenderingResource (CreateStream createStreamCallback, NameValueCollection deviceInfo)  
{  
    string[] iconTagValues = deviceInfo.GetValues("Icon");  
    if ((iconTagValues != null) && (iconTagValues.Length > 0) )  
    {  
        // Create a stream to output to.  
        Stream outputStream = createStreamCallback(m_iconResourceName, "gif", null, "image/gif", false);  
        // Get the GIF image for one of the buttons on the toolbar  
        Image requiredImage = (Image) m_resourcemanager.GetObject(m_iconResourceName  
        // Write the image to the output stream  
        requiredImage.Save(outputStream, requiredImage.RawFormat);  
    }  
    return;  
}  
```  
  
## <a name="renderstream-method"></a>Metodo RenderStream  
 Il metodo <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> consente di eseguire il rendering di un flusso specifico dal report. Tutti i flussi vengono creati durante la chiamata a <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> iniziale, ma i flussi non vengono inizialmente restituiti al client. Questo metodo viene utilizzato per flussi secondari, ad esempio immagini nel rendering HTML o pagine aggiuntive di un'estensione per il rendering di più pagine, come Image/EMF.  
  
## <a name="getrenderingresource-method"></a>Metodo GetRenderingResource  
 Il metodo <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> consente di recuperare le informazioni senza eseguire l'intero rendering del report. In alcuni casi, il report necessita di informazioni che non richiedono il rendering del report stesso. Ad esempio, se è necessaria l'icona associata all'estensione per il rendering, utilizzare il *deviceInfo* parametro contenente il tag singolo  **\<icona >**. In questi casi, è possibile utilizzare il metodo <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione per il Rendering](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Cenni preliminari sulle estensioni di rendering](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)  
  
  
