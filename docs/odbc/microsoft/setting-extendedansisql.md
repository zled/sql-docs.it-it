---
title: Impostazione ExtendedAnsiSQL | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extendedANSISQL [ODBC], setting
ms.assetid: 37b775d1-65ac-45ac-8572-454bc4e3c1a2
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8ba6688643c16eef8b6f20ef8f7bb469941b6edb
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setting-extendedansisql"></a>Impostazione ExtendedAnsiSQL
L'attributo può essere controllato nella stringa di connessione, aggiungere l'attributo ExtendedAnsiSQL:  
  
|Valore|Description|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 (impostazione predefinita)|Questa impostazione non abilita le nuove funzionalità.|  
|ExtendedAnsiSQL = 1|Questa impostazione abilita le nuove funzionalità.|  
  
 L'attributo può essere impostato anche in un DSN tramite il **opzioni avanzate** la finestra di dialogo quando si configura un DSN tramite il pannello di controllo.  
  
 Impostare l'attributo su 0 disabilita le funzionalità nuove. impostarla su 1 abilita le nuove funzionalità.  
  
 L'attributo può essere impostato anche tramite SQLSetConnectAttr(). Il valore dell'attributo è 65501 e viene impostato su un valore SQLINTEGER 1 o 0, come illustrato nella tabella precedente. Può essere chiamato prima o dopo la connessione, ma è preferibile chiamata dopo la connessione a causa dell'ordine in cui i processi di driver memorizzati nella cache gli attributi di connessione e le stringhe di connessione.
