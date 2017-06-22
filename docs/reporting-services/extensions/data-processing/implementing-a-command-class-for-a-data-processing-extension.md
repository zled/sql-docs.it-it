---
title: Implementazione di una classe di comando per un'estensione per l'elaborazione dati | Documenti Microsoft
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
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
caps.latest.revision: 35
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 9e6858a7f5c67508ff30396bb6ec668b908d671f
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a>Implementazione di una classe Command per un'estensione per l'elaborazione dati
  Il **comando** oggetto formula una richiesta e la passa all'origine dati. Il testo del comando può avere forme sintattiche diverse, tra cui testo e XML. Se vengono restituiti risultati, il **comando** restituisce i risultati come oggetto un **DataReader** oggetto.  
  
 Per creare un **comando** classe, implementare <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>. Implementare il <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> impostato per restituire un risultato come un **DataReader** oggetto. Il <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> metodo i **comando** classe deve includere un'implementazione che accetti un <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> enumerazione come argomento. Se si distribuisce l'estensione per l'elaborazione dati in Progettazione report, fornire un'implementazione in grado di gestire un caso <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> nel metodo <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>. Un'implementazione di solo schema viene utilizzata per fornire un elenco di campi a Progettazione report. Il **DataReader** oggetto restituito dal <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> (metodo) deve contenere nome e il tipo di informazioni per i campi o le colonne nel set di risultati.  
  
 Facoltativamente, il **comando** classe può implementare <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>. Questa interfaccia consente a una classe di implementazione di analizzare una query e restituire un elenco di parametri della query. La funzionalità dell'interfaccia <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> viene utilizzata solo in Progettazione report. Quando si implementa <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>, si consente agli utenti di Progettazione report di ricevere una richiesta per i parametri ogni volta che un report viene eseguito in modalità di anteprima. Inoltre, è possibile visualizzare i parametri in di **parametri** scheda del **Set di dati** finestra di dialogo.  
  
> [!NOTE]  
>  Non implementare <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> se l'estensione per l'elaborazione dati personalizzata non supporta i parametri.  
  
 Per un esempio **comando** implementazione della classe, vedere [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementazione di un'estensione di elaborazione dei dati](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
