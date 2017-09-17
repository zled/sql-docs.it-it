---
title: DLL di riferimento all'API del programma di installazione | Documenti Microsoft
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
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1bd84a225c94c4141cb9c7f6a897731926384ea6
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setup-dll-api-reference"></a>Riferimento API per l'installazione DLL
In questa sezione viene descritta la sintassi del programma di installazione di driver API DLL, che è costituito da due funzioni (**ConfigDriver** e **ConfigDSN**). **ConfigDriver** e **ConfigDSN** possibile di DLL del driver o in una funzione DLL di installazione.  
  
 Inoltre, in questa sezione viene descritta la sintassi dell'impostazione della funzione di conversione API DLL, che è costituito da una singola funzione (**ConfigTranslator del**). **ConfigTranslator del** può essere nella DLL la funzione di conversione o in una funzione DLL di installazione.  
  
 Ogni funzione è contrassegnata con la versione di ODBC in cui è stato introdotto.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Funzione ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [Funzione ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [Funzione ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)
