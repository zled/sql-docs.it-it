---
title: Fornisce argomenti di metodo del servizio Web | Documenti Microsoft
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
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
caps.latest.revision: 38
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 761571f88c2321c823dc240cfa9bb3ba75d9414b
ms.contentlocale: it-it
ms.lasthandoff: 08/12/2017

---
# <a name="supplying-web-service-method-arguments"></a>Impostazione degli argomenti dei metodi del servizio Web
  Un metodo del servizio Web ReportServer invia una richiesta al servizio a un URL specifico utilizzando SOAP tramite HTTP. Il servizio riceve la richiesta, la elabora e restituisce una risposta. Queste richieste e risposte hanno il formato di documenti XML.  
  
## <a name="optional-parameters"></a>Parametri facoltativi  
 In alcuni casi, un metodo del servizio Web può avere parametri di input facoltativi. Anche se un parametro di input per un metodo del servizio Web è facoltativo, è comunque necessario includerlo e impostare il valore del parametro **null** (**nulla** in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]). Impostando un valore di parametro **null** imposta il valore dell'elemento per il parametro nella richiesta SOAP per **null**.  
  
 Nell'esempio seguente viene utilizzato il metodo <xref:ReportService2010.ReportingService2010.CreateFolder%2A> per creare una nuova cartella denominata Product Sales nella cartella Sales. Fornendo un **null** valore per le proprietà della cartella, nessuna proprietà specifiche dell'utente vengono forniti per la cartella:  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a>Tipi di dati complessi  
 La classe principale del servizio Web ReportServer è <xref:ReportService2010.ReportingService2010> e viene utilizzata per richiamare le operazioni SOAP o i metodi Web della classe proxy. Per supportare questa classe e i relativi metodi, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] include tipi di dati complessi definiti dall'utente specifici dei parametri di input e output dei metodi del servizio Web. Questi tipi di dati complessi fanno parte della classe proxy generata, che è possibile utilizzare quando si sviluppa nel [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ambiente.  
  
 Quando si genera una classe proxy, i tipi di dati complessi definiti nel file WSDL vengono rappresentati dalle classi proxy, che includono proprietà che corrispondono ai vari elementi SOAP dei tipi di dati complessi. Le sequenze di questi tipi di dati diventano matrici di oggetti che è possibile enumerare nel codice. In questo modo, non è più necessario utilizzare direttamente le strutture XML inviate nei messaggi SOAP. La conversione viene gestita da [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servizio Web ReportServer](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Riferimento tecnico &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  

