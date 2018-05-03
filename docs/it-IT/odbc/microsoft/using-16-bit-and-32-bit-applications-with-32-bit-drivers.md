---
title: Utilizzare le applicazioni a 16 Bit e a 32 Bit con driver a 32 Bit | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 16-bit applications
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
- 16-bit applications with 32-bit drivers [ODBC]
ms.assetid: fc65c988-b31f-4cc9-851f-30d2119604fd
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 076284b2a7aa4d5ef0cb49154ee8597a2e35c6d7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-16-bit-and-32-bit-applications-with-32-bit-drivers"></a>Utilizzare le applicazioni a 16 Bit e a 32 Bit con driver a 32 Bit
> [!IMPORTANT]  
>  supporto di applicazioni a 16 bit verrà rimosso in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Sviluppare invece le applicazioni a 32 bit o 64 bit.  
  
 Con il componente di accesso ai dati ODBC, è possibile utilizzare le applicazioni a 16 bit e a 32 bit con driver a 32 bit. Sistemi operativi Microsoft® Windows® 95/98 e Microsoft Windows e Windows 2000 supportano le seguenti combinazioni di applicazioni e driver:  
  
-   applicazioni a 16 bit con driver a 32 bit  
  
-   applicazioni a 32 bit con driver a 32 bit  
  
 Non è supportato l'utilizzo di un'applicazione a 32 bit con driver a 16 bit.  
  
> [!NOTE]  
>  A partire dalla versione di ODBC versione 3.0, Windows NT 4.0 è supportata.  
  
 ODBC include i componenti ODBC necessari per supportare le configurazioni precedenti "thunk" librerie a collegamento dinamico (DLL) per convertire gli indirizzi di 16 bit in indirizzi a 32 bit e viceversa. Il programma di installazione determina il sistema operativo, si utilizza e installa i componenti ODBC richiesti da tale sistema. È anche possibile scegliere di installare i componenti ODBC utilizzati da tutti i sistemi.  
  
 Nella maggior parte dei casi, il porting di un'applicazione o il driver a 16 bit a 32 bit prevede cinque tipi di modifiche:  
  
-   Modifiche al codice di gestione dei messaggi  
  
-   Modifica perché sono numeri interi e gli handle a 32 bit  
  
-   Modifiche nelle chiamate a application programming interface (API) Windows  
  
-   Modifiche per rendere il driver thread-safe  
  
-   Modifiche ai componenti ODBC  
  
 Da un'applicazione o il driver programmazione punto di vista, la differenza principale tra i componenti ODBC a 16 bit e a 32 bit è che hanno nomi di file diversi. Dal punto di vista di sistema, l'architettura di ogni connessione di applicazione o il driver è diversa e gli strumenti utilizzati per gestire le origini dati sono diversi.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Uso delle applicazioni a 16 bit con driver a 32 bit](../../odbc/microsoft/using-16-bit-applications-with-32-bit-drivers.md)  
  
-   [Uso delle applicazioni a 32 bit con driver a 32 bit](../../odbc/microsoft/using-32-bit-applications-with-32-bit-drivers.md)
