---
title: Implementazione di un'estensione di elaborazione dei dati | Documenti Microsoft
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
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 1497690ebccc010601542308747240d0e91d89db
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="implementing-a-data-processing-extension"></a>Implementazione di un'estensione per l'elaborazione dati
  Le estensioni per l'elaborazione dati in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] consentono di eseguire la connessione a un'origine dati e di recuperare i dati. Fungono inoltre da ponte tra un'origine dati e un set di dati. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]estensioni per l'elaborazione dati sono modellate in un sottoinsieme di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] interfacce del provider di dati.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Cenni preliminari sulle estensioni di elaborazione dei dati](../../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)  
 Vengono fornite informazioni introduttive per la scrittura di un'estensione per l'elaborazione dati per [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Preparazione all'implementazione di un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/preparing-to-implement-a-data-processing-extension.md)  
 Vengono descritte le interfacce disponibili quando si implementa un'estensione per l'elaborazione dati di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e vengono indicati i casi in cui è necessario implementare un'interfaccia specifica.  
  
 [Creazione di una libreria di estensioni di elaborazione dei dati](../../../reporting-services/extensions/data-processing/creating-a-data-processing-extension-library.md)  
 Vengono descritte le operazioni di assegnazione di uno spazio dei nomi per l'estensione per l'elaborazione dati di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e di compilazione dell'estensione per l'elaborazione dati nella DLL di una libreria.  
  
 [Implementazione di una classe di connessione per un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/implementing-a-connection-class-for-a-data-processing-extension.md)  
 Vengono descritti gli attributi di una connessione e come implementare la propria **connessione** classe per l'estensione di elaborazione dei dati.  
  
 [Implementazione di una classe di comando per un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/implementing-a-command-class-for-a-data-processing-extension.md)  
 Vengono descritti gli attributi di un comando e come implementare la propria **comando** classe per l'estensione di elaborazione dei dati.  
  
 [Implementazione di una classe DataReader per un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/implementing-a-datareader-class-for-a-data-processing-extension.md)  
 Vengono descritti gli attributi di un lettore di dati e come implementare la propria **DataReader** classe per l'estensione di elaborazione dei dati.  
  
 [Utilizzo di un set di dati esterno con Reporting Services](../../../reporting-services/extensions/data-processing/using-an-external-dataset-with-reporting-services.md)  
 Viene descritto come esporre personalizzato **DataSet** oggetti nel server di report per l'utilizzo.  
  
 [Distribuzione di un'estensione di elaborazione dei dati](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)  
 Viene descritto come distribuire un'estensione per l'elaborazione dati.  
  
 [Debug del codice di estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/debugging-data-processing-extension-code.md)  
 Viene descritto come eseguire il debug del codice nelle estensioni per l'elaborazione dati.  
  
 [Rimozione di un'estensione di elaborazione dei dati](../../../reporting-services/extensions/data-processing/removing-a-data-processing-extension.md)  
 Viene descritto come rimuovere un'estensione per l'elaborazione dati da un server di report o da Progettazione report.  
  
 Per un esempio di estensione per l'elaborazione dati completamente implementata, vedere [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
