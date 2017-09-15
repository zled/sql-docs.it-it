---
title: Panoramica dell'architettura driver | Documenti Microsoft
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
- Visual FoxPro ODBC driver [ODBC], architecture
- FoxPro ODBC driver [ODBC], architecture
ms.assetid: ef5a91cd-158e-40bf-b5a8-8ba535c4705e
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6755e4b04c0d56995fb83f64891e5fcd7d765a49
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="driver-architecture-overview"></a>Panoramica dell'architettura del driver
Il Driver ODBC Microsoft Visual FoxPro è un driver a 32 bit che consente di aprire ed eseguire query su un database di Microsoft Visual FoxPro o FoxPro tabelle tramite l'interfaccia aprire Database Connectivity (ODBC). È possibile accedere a dati FoxPro utilizzando i seguenti tipi di applicazioni:  
  
-   Un'applicazione di Microsoft Office, ad esempio Microsoft Excel o Microsoft Word, Microsoft Query che utilizza per comunicare con ODBC.  
  
-   Un'applicazione scritta in Microsoft Visual C++ o C, che usa l'API SDK di ODBC.  
  
-   Un'applicazione scritta in Microsoft Visual Basic o Microsoft Visual Basic for Applications.  
  
 In ogni caso, la richiesta di informazioni viene utilizzata l'API ODBC. Gestione Driver ODBC funziona con il Driver ODBC Visual FoxPro per aprire e recuperare dati dal database e le tabelle di FoxPro.  
  
 L'architettura è rappresentata nel diagramma seguente:  
  
 ![Architettura del Driver ODBC](../../odbc/microsoft/media/vfparch.gif "vfparch")  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Terminologia di Visual FoxPro](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [L'installazione e configurazione del Driver ODBC di Visual FoxPro](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Tramite il Driver ODBC di Visual FoxPro](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
