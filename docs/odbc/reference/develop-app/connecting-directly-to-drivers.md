---
title: Connettersi direttamente al driver | Documenti Microsoft
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
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f85b319ec264f9784953f12f93100660db614cbb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-directly-to-drivers"></a>Connettersi direttamente al driver
Come è stato illustrato in [scelta di un'origine dati o il Driver](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md), più indietro in questa sezione, alcune applicazioni non si desidera utilizzare un'origine dati in tutti. In alternativa, desiderano connettersi direttamente a un driver. **SQLDriverConnect** fornisce un modo per le applicazioni possono connettersi direttamente a un driver senza specificare un'origine dati. Concettualmente, un'origine dati temporaneo viene creata in fase di esecuzione.  
  
 Per connettersi direttamente a un driver, l'applicazione specifica di **DRIVER** parola chiave nella stringa di connessione anziché il **DSN** (parola chiave). Il valore di **DRIVER** (parola chiave) è la descrizione del driver restituito da **SQLDrivers**. Si supponga, ad esempio, un driver con la descrizione del Driver Paradox e richiede il nome di una directory contenente i file di dati. Per connettersi a questo driver, l'applicazione potrebbe utilizzare una delle stringhe di connessione seguenti:  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 Con la prima stringa, il driver non è necessario eventuali informazioni aggiuntive. Con la seconda stringa, il driver necessario richiedere il nome della directory contenente i file di dati.
