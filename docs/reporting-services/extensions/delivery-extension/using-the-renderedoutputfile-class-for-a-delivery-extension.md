---
title: Using the RenderedOutputFile Class for a Delivery Extension (Uso della classe RenderedOutputFile per un'estensione per il recapito) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
caps.latest.revision: "34"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6188e7a78f2351a6c92c3698fbcf7ee58090667d
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a>Utilizzo della classe RenderedOutputFile per un'estensione per il recapito
  La classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> rappresenta un flusso di dati e le informazioni sulle proprietà associate al flusso. La proprietà **Data** della classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> viene usata per rappresentare un report visualizzabile o una risorsa del report come un oggetto **Stream**.  
  
 Il metodo <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> dell'oggetto **Report** restituisce una matrice di uno o più oggetti <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> che insieme costituiscono un singolo report visualizzabile. Il primo oggetto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> è il report visualizzabile. Tutti gli altri oggetti <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> sono risorse che devono essere recapitate insieme ai dati del report (ad esempio, un file HTML e le immagini associate). Le estensioni per il rendering a flusso singolo (IMAGE, PDF, MHTML ed EXCEL) restituiscono solo un oggetto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> nella matrice.  
  
 Per un esempio su come usare la classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>, vedere [ Esempi del prodotto Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione per il recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
