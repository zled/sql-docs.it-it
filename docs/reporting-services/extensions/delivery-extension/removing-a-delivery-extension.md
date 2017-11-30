---
title: Rimozione di un'estensione per il recapito | Microsoft Docs
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
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
caps.latest.revision: "31"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: fa353bad5d7ba36330aca71fcb0d329ff0c606a6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="removing-a-delivery-extension"></a>Rimozione di un'estensione per il recapito
  Per rimuovere un'estensione per il recapito di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], rimuovere semplicemente l'elemento **Extension** per l'estensione dal file di configurazione. Dopo la rimozione delle informazioni di configurazione, l'estensione per il recapito non è più disponibile per il server di report.  
  
 Dopo aver rimosso l'elemento **Extension** corrispondente di un'estensione per il recapito dal file di configurazione, l'estensione non è più registrata nel server di report. Il server di report rimuove la voce dall'elenco di estensioni per il recapito e disattiva qualsiasi sottoscrizione che utilizza tale estensione. Quando un'estensione per il recapito viene rimossa, gli utenti non possono più selezionarla come metodo di notifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione per il recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
