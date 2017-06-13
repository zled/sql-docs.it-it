---
title: Rimozione di un&quot;estensione di recapito | Documenti Microsoft
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
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
caps.latest.revision: 31
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 81cadbc6eb9b176555b8d5dd5f63ac827e84d7f6
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="removing-a-delivery-extension"></a>Rimozione di un'estensione per il recapito
  Per rimuovere un [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] estensione per il recapito, rimuovere semplicemente la **estensione** elemento per l'estensione di recapito dal file di configurazione. Dopo la rimozione delle informazioni di configurazione, l'estensione per il recapito non è più disponibile per il server di report.  
  
 Una volta l'estensione per il recapito corrispondente **estensione** elemento viene rimosso dal file di configurazione, non è registrato con il server di report. Il server di report rimuove la voce dall'elenco di estensioni per il recapito e disattiva qualsiasi sottoscrizione che utilizza tale estensione. Quando un'estensione per il recapito viene rimossa, gli utenti non possono più selezionarla come metodo di notifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
