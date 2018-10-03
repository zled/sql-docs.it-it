---
title: Riferimento all'API DLL di installazione | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d81bb9f5ec54f3d66089205f5b5941119d365501
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622209"
---
# <a name="setup-dll-api-reference"></a>Informazioni di riferimento sull'API per l'installazione DLL
In questa sezione viene descritta la sintassi del programma di installazione di driver API DLL, che è costituito da due funzioni (**ConfigDriver** e **ConfigDSN**). **ConfigDriver** e **ConfigDSN** può essere rappresentato nella DLL del driver o in una DLL di configurazione.  
  
 Inoltre, in questa sezione viene descritta la sintassi della configurazione di Microsoft translator, API DLL, che è costituito da una singola funzione (**ConfigTranslator**). **ConfigTranslator** può essere translator DLL o in una DLL di configurazione.  
  
 Ogni funzione viene etichettata con la versione di ODBC in cui è stato introdotto in.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Funzione ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [Funzione ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [Funzione ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)
