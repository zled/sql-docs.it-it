---
title: Omissione di valori per gli oggetti del servizio Web facoltativi | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
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
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 727d9ccd8cd1e40d89cfe74291edae92988b407c
ms.openlocfilehash: 3532a470bd036e0128a8df21ca391210cf7209a2
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="omitting-values-for-optional-web-service-objects"></a>Omissione di valori per gli oggetti del servizio Web facoltativi
  Proprietà di alcuni dei tipi complessi del servizio Web ReportServer sono nota come la proprietà specificata associata una proprietà. Il nome della proprietà è costituito dal nome della proprietà originale con l'aggiunta della parola "Specified". La presenza di questa proprietà indica che, a volte, è possibile omettere un valore per la proprietà originale. Si tratta di un risultato diretto della conversione da WSDL (Web Service Description Language) a una classe proxy [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Ad esempio, alla proprietà del servizio Web <xref:ReportService2010.DataSourceDefinition.Enabled%2A> del tipo complesso <xref:ReportService2010.DataSourceDefinition> è associata una proprietà denominata <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>. Se si compila un'applicazione e non si desidera impostare un valore per il <xref:ReportService2010.DataSourceDefinition.Enabled%2A> proprietà, non è necessario fornire un valore per <xref:ReportService2010.DataSourceDefinition.Enabled%2A>; il valore predefinito di **true** viene utilizzato. Tuttavia, è comunque necessario impostare <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> a **false**. Se si specifica un valore per il <xref:ReportService2010.DataSourceDefinition.Enabled%2A> proprietà, è necessario impostare <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> uguale a **true**. È il caso delle proprietà scrivibili. Per le proprietà di sola lettura, non è necessaria alcuna azione.  
  
> [!IMPORTANT]  
>  La mancata definizione di una proprietà con la tecnica indicata in precedenza può causare un comportamento imprevedibile del servizio Web.  
  
 I tipi di dati che richiedono in genere di gestire la proprietà specificata aggiuntiva sono **booleano**, **DateTime**, e **enumerazione**.  
  
 Per un esempio, vedere il metodo <xref:ReportService2010.ReportingService2010.CreateDataSource%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Riferimento tecnico &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
