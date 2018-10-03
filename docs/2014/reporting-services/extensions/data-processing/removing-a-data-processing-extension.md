---
title: Rimozione di un'estensione per l'elaborazione dati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- deleting data processing extensions
- data processing extensions [Reporting Services], removing
- removing data processing extensions
ms.assetid: 1d89e32b-0631-44f6-8178-a57fb791d26d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7a1ad001df3353d4f114ec5ef38af2a7fdc9f142
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200051"
---
# <a name="removing-a-data-processing-extension"></a>Rimozione di un'estensione per l'elaborazione dati
  Per rimuovere un'estensione per l'elaborazione dati, rimuovere semplicemente l'elemento **Extension** per l'estensione dal file di configurazione. Se sono state create voci per un server di report e per Progettazione report, rimuovere l'elemento**Extension** sia dal file RSReportServer.config che dal file RSReportDesigner.config. Dopo la rimozione delle informazioni di configurazione, l'estensione per l'elaborazione dati non è più disponibile per il componente.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../reporting-services-extensions.md)   
 [Implementazione di un'estensione per l'elaborazione dati](implementing-a-data-processing-extension.md)   
 [Libreria di estensioni di Reporting Services](../reporting-services-extension-library.md)  
  
  
