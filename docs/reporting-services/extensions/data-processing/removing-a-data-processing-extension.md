---
title: Rimozione di un'estensione di elaborazione dei dati | Documenti Microsoft
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
- deleting data processing extensions
- data processing extensions [Reporting Services], removing
- removing data processing extensions
ms.assetid: 1d89e32b-0631-44f6-8178-a57fb791d26d
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: e59120a2297617d9234dac070cb5c99b4d564d65
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="removing-a-data-processing-extension"></a>Rimozione di un'estensione per l'elaborazione dati
  Per rimuovere un'estensione per l'elaborazione dati, eliminare semplicemente il **estensione** elemento per l'estensione di elaborazione dei dati dal file di configurazione. Se sono state create voci per un server di report e progettazione Report, rimuovere il **estensione** elemento dal file RSReportServer. config e RSReportDesigner. config. Dopo la rimozione delle informazioni di configurazione, l'estensione per l'elaborazione dati non è più disponibile per il componente.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementazione di un'estensione di elaborazione dei dati](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
