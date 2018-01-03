---
title: Connessione a un'origine dati (Driver ODBC per Oracle) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connecting to data source [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connecting to data sources
ms.assetid: f724a9c5-342a-4f4e-a030-ec34f7378eaf
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a2b087ef77a00947c4e270861fffd27108389839
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="connecting-to-a-data-source-odbc-driver-for-oracle"></a>Connessione a un'origine dati (Driver ODBC per Oracle)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Un'applicazione ODBC è possibile passare le informazioni di connessione in diversi modi. Ad esempio, l'applicazione potrebbe avere il driver Chiedi sempre conferma all'utente le informazioni di connessione. O l'applicazione potrebbe prevedere una stringa di connessione che specifica la connessione all'origine dati. La modalità di connessione a un'origine dati dipende dal metodo di connessione utilizzato dall'applicazione ODBC.  
  
 Un modo comune per connettersi a un'origine dati è tramite la finestra di dialogo origine dati. Se l'applicazione ODBC è configurato per utilizzare una finestra di dialogo, tale finestra di dialogo viene visualizzata e viene richiesto per le informazioni di connessione di origine di dati appropriato.  
  
 È inoltre possibile connettersi a un'origine dati usando il [stringa di connessione](../../odbc/microsoft/connection-string-format-and-attributes.md).  
  
### <a name="to-connect-to-a-data-source-using-a-dialog-box"></a>Per connettersi a un'origine dati tramite una finestra di dialogo  
  
1.  Quando viene visualizzata la finestra di dialogo origine dati, selezionare un'origine dati Oracle e quindi fare clic su OK. Verrà visualizzata la finestra di dialogo Connetti.  
  
2.  Compilare le informazioni appropriate per la finestra di dialogo di connessione e quindi fare clic su OK.  
  
 Dopo la connessione è verificare informazioni, l'applicazione può utilizzare il Driver ODBC per Oracle per accedere alle informazioni contenute nell'origine dati.
