---
title: DLL di riferimento all'API del programma di installazione | Documenti Microsoft
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
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa09dad7423a56db064ade504f3b6598f3daf4ff
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916506"
---
# <a name="setup-dll-api-reference"></a>Riferimento API per l'installazione DLL
In questa sezione viene descritta la sintassi del programma di installazione di driver API DLL, che è costituito da due funzioni (**ConfigDriver** e **ConfigDSN**). **ConfigDriver** e **ConfigDSN** può essere rappresentato nella DLL del driver o in una DLL di installazione.  
  
 Inoltre, in questa sezione viene descritta la sintassi dell'impostazione della funzione di conversione API DLL, che è costituito da una singola funzione (**ConfigTranslator del**). **ConfigTranslator del** può essere nella DLL la funzione di conversione o in una DLL di installazione.  
  
 Ogni funzione è contrassegnata con la versione di ODBC in cui è stato introdotto.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Funzione ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [Funzione ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [Funzione ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)
