---
title: Implementazione di una classe DataReader per un&quot;estensione per l&quot;elaborazione dati | Documenti Microsoft
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
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
caps.latest.revision: 35
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: fb0f4c2f3ea3137f2e614e688aa5e3823a043e50
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a>Implementazione di una classe DataReader per un'estensione per l'elaborazione dati
  Il **DataReader** oggetto consente a un client recuperare un flusso forward-only in sola lettura di dati da un'origine dati. Vengono restituiti come la query viene eseguita e vengono archiviati nel buffer di rete nel client fino a quando non ne fanno richiesta utilizzando il **lettura** metodo il **DataReader** classe. Per creare un **DataReader** classe, implementare <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> e implementare facoltativamente <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>. Utilizzando un **DataReader** oggetto aumenta le prestazioni dell'applicazione recuperando i dati appena sono disponibile, anziché attendere che tutti i risultati della query restituita e (per impostazione predefinita) l'archiviazione solo una riga alla volta in memoria, riducendo l'overhead di sistema.  
  
 Dopo aver creato un'istanza del **comando** (classe), si crea un **DataReader** oggetto chiamando **Command. ExecuteReader** per recuperare le righe dall'origine dati. Il **DataReader** implementazione deve fornire due funzionalità di base: accesso forward-only sul risultato del imposta ottenuto eseguendo un comando e l'accesso ai tipi di colonna, nomi e valori all'interno di ogni riga. I client utilizzano il **lettura** metodo il **DataReader** per ottenere una riga dai risultati della query.  
  
 In Progettazione Report, il **DataReader** oggetto viene utilizzato per recuperare un elenco di campi, nonché informazioni sullo schema relative a set di risultati. Questa operazione viene eseguita implementando il **GetName**, **GetValue**, **GetFieldType,** e **GetOrdinal** metodi il <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> interfaccia.  
  
 L'interfaccia <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> consente di fornire informazioni di aggregazione specifiche per il set di risultati. Per un esempio **DataReader** implementazione della classe, vedere [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementazione di un'estensione di elaborazione dei dati](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
