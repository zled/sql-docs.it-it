---
title: Using the RenderedOutputFile Class for a Delivery Extension (Uso della classe RenderedOutputFile per un'estensione per il recapito) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: extensions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 956af796d7192325f5f6170be4908da8f97f8ad2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a>Utilizzo della classe RenderedOutputFile per un'estensione per il recapito
  La classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> rappresenta un flusso di dati e le informazioni sulle proprietà associate al flusso. La proprietà **Data** della classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> viene usata per rappresentare un report visualizzabile o una risorsa del report come un oggetto **Stream**.  
  
 Il metodo <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> dell'oggetto **Report** restituisce una matrice di uno o più oggetti <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> che insieme costituiscono un singolo report visualizzabile. Il primo oggetto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> è il report visualizzabile. Tutti gli altri oggetti <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> sono risorse che devono essere recapitate insieme ai dati del report (ad esempio, un file HTML e le immagini associate). Le estensioni per il rendering a flusso singolo (IMAGE, PDF, MHTML ed EXCEL) restituiscono solo un oggetto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> nella matrice.  
  
 Per un esempio su come usare la classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>, vedere [ Esempi del prodotto Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione per il recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
