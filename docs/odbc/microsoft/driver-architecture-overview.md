---
title: Panoramica dell'architettura driver | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], architecture
- FoxPro ODBC driver [ODBC], architecture
ms.assetid: ef5a91cd-158e-40bf-b5a8-8ba535c4705e
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f9c5d4720e126c6d496754201889b862b508e90
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
-   [Installazione e configurazione del Driver ODBC di Visual FoxPro](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Uso del driver ODBC Visual FoxPro](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
