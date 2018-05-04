---
title: Bloccare i cursori, i cursori scorrevoli e compatibilità con le versioni precedenti | Documenti Microsoft
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
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: d9d271f6-d2d9-49b9-a365-4909ca06caae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c22ef4ebf761b647f4b0e6bb8c65ccd3457fe694
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Cursori a blocchi, i cursori scorrevoli e compatibilità con le versioni precedenti
L'esistenza di entrambi **SQLFetchScroll** e **SQLExtendedFetch** rappresenta il primo clear suddiviso in ODBC tra l'interfaccia API (Application Programming), ovvero il set di funzioni di le chiamate dell'applicazione e il servizio Provider interfaccia SPI (), ovvero il set di funzioni il driver implementa. La divisione è necessaria in modo che ODBC 3. *x*, che usa **SQLFetchScroll**, bealigned con gli standard e anche essere compatibile con ODBC 2. *x*, che usa **SQLExtendedFetch**.  
  
 ODBC 3*x* API, ovvero il set di funzioni l'applicazione chiama, include **SQLFetchScroll** e relativi attributi di istruzione. ODBC 3*x* SPI, ovvero il set di funzioni implementa il driver, include **SQLFetchScroll**, **SQLExtendedFetch**e i relativi attributi di istruzione. Poiché ODBC non impone formalmente la divisione tra l'API e l'indice, è possibile per ODBC 3*x* alle applicazioni di chiamare **SQLExtendedFetch** e relativi attributi di istruzione. Tuttavia, non è necessario per ODBC 3*x* applicazione per eseguire questa operazione. Per ulteriori informazioni sulle API e SPI, vedere l'introduzione a [architettura ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Per informazioni su quali funzioni e l'istruzione gli attributi di un'applicazione ODBC 3. *x* applicazione deve utilizzare con i cursori scorrevoli e di blocco, vedere [cursori a blocchi, i cursori scorrevoli e la compatibilità con le applicazioni ODBC 3. x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Come funziona Gestione driver](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [Come funziona il driver](../../../odbc/reference/appendixes/what-the-driver-does.md)
