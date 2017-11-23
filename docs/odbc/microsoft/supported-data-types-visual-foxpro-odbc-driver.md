---
title: Tipi di dati (Driver ODBC di Visual FoxPro) supportati | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], data types
- FoxPro ODBC driver [ODBC], data types
- data types [ODBC], Visual FoxPro ODBC driver
ms.assetid: ab529cc6-d157-4b35-b6f9-6ffd09af098c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2bb3bc1b6de38295af0028fb79d0526bb092b49b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="supported-data-types-visual-foxpro-odbc-driver"></a>Tipi di dati supportati (Driver ODBC di Visual FoxPro)
L'elenco di tipi di dati supportati dal driver sono presentati tramite l'API ODBC e nella Query di Microsoft.  
  
## <a name="data-types-in-c-applications"></a>Tipi di dati nelle applicazioni C  
 È possibile ottenere un elenco di tipi di dati supportati dal Driver ODBC Visual FoxPro utilizzando il [SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md) funzione nelle applicazioni C o C++.  
  
## <a name="data-types-in-applications-using-microsoft-query"></a>Tipi di dati nelle applicazioni che utilizzano Microsoft Query  
 Se l'applicazione utilizza Microsoft Query per creare una nuova tabella in un'origine dati di Visual FoxPro, Microsoft Query consente di visualizzare il **nuova definizione di tabella** la finestra di dialogo. In **campo Descrizione**, **tipo** casella elenchi [tipi di dati di campo di Visual FoxPro](../../odbc/microsoft/visual-foxpro-field-data-types.md), rappresentato dai singoli caratteri.
