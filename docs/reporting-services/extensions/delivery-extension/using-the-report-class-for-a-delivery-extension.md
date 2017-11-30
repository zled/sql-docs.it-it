---
title: Using the Setting Class for a Delivery Extension (Uso della classe Setting per un'estensione per il recapito) | Microsoft Docs
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
caps.latest.revision: "34"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f74c4848721333e0cebb1d7292c28646b3f07fe7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="using-the-report-class-for-a-delivery-extension"></a>Utilizzo della classe Report per un'estensione per il recapito
  La classe <xref:Microsoft.ReportingServices.Interfaces.Report> rappresenta un report nel database del server di report. Qualsiasi sottoscrizione è associata a un report specifico. Il report è incluso nella notifica. L'estensione per il recapito può utilizzare l'oggetto <xref:Microsoft.ReportingServices.Interfaces.Report> incluso nella notifica per eseguire il rendering del report. L'oggetto <xref:Microsoft.ReportingServices.Interfaces.Report> contiene inoltre proprietà specifiche del report, ad esempio l'URL del report nel server di report e il nome del report. Tutte queste proprietà possono essere utilizzate come parte del provider di recapito.  
  
 Per il rendering di un report, è possibile utilizzare il metodo <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> della classe <xref:Microsoft.ReportingServices.Interfaces.Report>. Il metodo <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> restituisce una matrice di uno o più oggetti <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> che comprendono un singolo report visualizzabile. Il primo oggetto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> è il report visualizzabile. Tutti gli altri oggetti <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> sono risorse che devono essere recapitate insieme ai dati del report (ad esempio, un file HTML e le immagini associate). Le estensioni per il rendering a flusso singolo (IMAGE, PDF, MHTML ed Excel) restituiscono solo un oggetto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> nella matrice.  
  
 L'oggetto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> che contiene il flusso del report può essere incluso come parte di un recapito.  
  
 Per un esempio su come usare la classe <xref:Microsoft.ReportingServices.Interfaces.Report>, vedere [Esempi del prodotto SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889)  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione per il recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)   
 [Uso della classe RenderedOutputFile per un'estensione per il recapito](../../../reporting-services/extensions/delivery-extension/using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  
