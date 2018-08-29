---
title: Tipi definiti dall'utente | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 19a71b27-b788-43a3-a76d-fe3001a6f016
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 55db7c7c903f4b22a85f9762f13f845ea7ea17ba
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786285"
---
# <a name="user-defined-types"></a>Tipi definiti dall'utente

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

I tipi definiti dall'utente (UDT) sono stati introdotti in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] per consentire agli sviluppatori di estendere il sistema di tipo scalare del server archiviando oggetti Common Language Runtime (CLR) in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I tipi definiti dall'utente possono contenere più elementi e avere comportamenti che, a differenza dei tradizionali tipi di dati alias, sono costituiti da un solo tipo di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In precedenza, i tipi definiti dall'utente erano limitati a una dimensione massima di 8 kilobyte. In [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] è stato aggiunto il supporto per i tipi definiti dall'utente con dimensioni superiori a 64 kilobyte. A partire dalla versione 3.0, il driver JDBC supporta anche tipi definiti dall'utente con dimensioni maggiori di 64 kilobyte quando si specifica il formato UserDefined.

Non esiste alcuna modifica di comportamento per i tipi definiti dall'utente minori o uguali a 8.000 byte, ma sono supportati tipi definiti dall'utente di dimensioni maggiori, che vengono indicate come illimitate ("unlimited").

## <a name="see-also"></a>Vedere anche

[Informazioni sui tipi di dati del driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)
