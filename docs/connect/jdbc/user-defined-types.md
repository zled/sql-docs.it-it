---
title: Tipi definiti dall'utente | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19a71b27-b788-43a3-a76d-fe3001a6f016
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ed2b0bb8227a1b430bcd30b1d41460862c8db325
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="user-defined-types"></a>Tipi definiti dall'utente
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Tipi definiti dall'utente (UDT) sono stati introdotti in [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] per consentire agli sviluppatori di estendere il sistema di tipi scalari del server archiviando oggetti common language runtime (CLR) in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database. Tipi definiti dall'utente possono contenere più elementi e possono assumere comportamenti, a differenza dei tipi di dati alias tradizionali, costituiti da una singola [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] il tipo di dati di sistema. In precedenza, i tipi definiti dall'utente erano limitati a una dimensione massima di 8 kilobyte. In [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)], è stato aggiunto il supporto per tipi definiti dall'utente maggiore di 64 kilobyte. A partire dalla versione 3.0, il driver JDBC supporta anche tipi definiti dall'utente con dimensioni maggiori di 64 kilobyte quando si specifica il formato UserDefined.  
  
 Non esiste alcuna modifica di comportamento per i tipi definiti dall'utente minori o uguali a 8.000 byte, ma sono supportati tipi definiti dall'utente di dimensioni maggiori, che vengono indicate come illimitate ("unlimited").  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sui tipi di dati del Driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  

