---
title: Rimozione di un'estensione di recapito | Documenti Microsoft
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
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: e0d806bd57750b4e260ce0ba9fe48e86ac6d7386
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="removing-a-delivery-extension"></a>Rimozione di un'estensione per il recapito
  Per rimuovere un [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] estensione per il recapito, rimuovere semplicemente la **estensione** elemento per l'estensione di recapito dal file di configurazione. Dopo la rimozione delle informazioni di configurazione, l'estensione per il recapito non è più disponibile per il server di report.  
  
 Una volta l'estensione per il recapito corrispondente **estensione** elemento viene rimosso dal file di configurazione, non è registrato con il server di report. Il server di report rimuove la voce dall'elenco di estensioni per il recapito e disattiva qualsiasi sottoscrizione che utilizza tale estensione. Quando un'estensione per il recapito viene rimossa, gli utenti non possono più selezionarla come metodo di notifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
