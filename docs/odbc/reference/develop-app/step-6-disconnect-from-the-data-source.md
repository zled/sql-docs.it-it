---
title: 'Passaggio 6: Disconnettersi dall''origine dati | Documenti Microsoft'
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
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ce3ea03a637e8edce89c83f196e4fcafd97dfdc8
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="step-6-disconnect-from-the-data-source"></a>Passaggio 6: Disconnettersi dall'origine dati
Il passaggio finale consiste nel disconnettere dall'origine dati, come illustrato nella figura seguente. In primo luogo, l'applicazione rilascia tutti gli handle di istruzione chiamando **SQLFreeHandle**. Per ulteriori informazioni, vedere [liberare l'Handle di istruzione](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Mostra la disconnessione da un'origine dati](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Successivamente, l'applicazione si disconnette dall'origine dati con **SQLDisconnect** e rilascia l'handle di connessione con **SQLFreeHandle**. Per ulteriori informazioni, vedere [disconnessione da un'origine dati o il Driver](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Infine, l'applicazione rilascia l'handle di ambiente con **SQLFreeHandle** e scaricato da Gestione Driver. Per ulteriori informazioni, vedere [allocare l'Handle di ambiente](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).

