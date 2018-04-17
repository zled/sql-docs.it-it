---
title: Tipi di dati C in ODBC | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
ms.assetid: c91bef31-3794-4736-966a-d50997b2233c
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 05a8ce31caf23a29a51cd9329c2c85950e15580e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="c-data-types-in-odbc"></a>Tipi di dati C in ODBC
ODBC definisce i tipi di dati C utilizzati da variabili di applicazione e i relativi identificatori di tipo corrispondente. Questi vengono utilizzati dai buffer che sono associati a colonne del set di risultati e i parametri dell'istruzione. Si supponga, ad esempio, che un'applicazione deve recuperare dati da una colonna del set di risultati in formato carattere. Dichiara una variabile con il SQLCHAR * tipo di dati e viene associato a questa variabile per la colonna del set di risultati con un identificatore di tipo di SQL_C_CHAR. Per un elenco completo dei tipi di dati C e gli identificatori di tipo, vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 Anche ODBC definisce già un mapping predefinito di ogni tipo di dati SQL per un tipo di dati C. Ad esempio, un integer a 2 byte nell'origine dati viene eseguito il mapping a un intero di 2 byte nell'applicazione. Per utilizzare il mapping predefinito, un'applicazione specifica l'identificatore di tipo SQL_C_DEFAULT. Tuttavia, l'uso di questo identificatore è sconsigliato per motivi di interoperabilità.  
  
 Tutti i tipi di dati integer C definiti in ODBC 1*x* sono stati firmati. In ODBC 2.0 sono stati aggiunti tipi di dati C senza segno e i relativi identificatori di tipo corrispondente. Per questo motivo, applicazioni e driver necessario prestare particolare cautela quando si lavora con 1*x* versioni.  
  
## <a name="c-data-type-extensibility"></a>Estendibilità del tipo di dati C  
 In ODBC 3.8, è possibile specificare i tipi di dati C specifici del driver. Ciò consente di associare un tipo SQL come tipo nelle applicazioni ODBC C specifici del driver quando si chiama [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md), o [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md). Ciò può rivelarsi utile per il supporto di nuovi tipi di server, poiché i tipi di dati C esistenti potrebbero non rappresentare correttamente i nuovi tipi di dati di server. Utilizzo di tipi C specifici del driver, è possibile aumentare il numero di conversioni che è possono eseguire i driver.  
  
 Ad esempio, si supponga che un sistema di gestione di database (DBMS) introdotto un nuovo tipo SQL, **DATETIMEOFFSET**, per rappresentare la data e ora con informazioni sul fuso orario. Non vi sarà alcun tipo specifico di C in ODBC che corrisponde a **DATETIMEOFFSET**. Sarebbe necessario associare un'applicazione **DATETIMEOFFSET** come SQL_C_BINARY ed eseguire il cast a un di dati definito dall'utente digitare. A partire da ODBC 3.8 con estendibilità del tipo di dati C, un driver può definire un nuovo tipo C corrispondente. Ad esempio, per il nuovo tipo SQL DATETIMEOFFSET, il driver può definire un nuovo tipo C corrispondente, ad esempio SQL_C_DATETIMEOFFSET. Quindi, un'applicazione può associare il nuovo tipo di SQL come tipo C specifici del driver.  
  
 Viene definito un tipo di dati C nel driver come segue:  
  
-   Il livello di conformità per un'applicazione, il driver ODBC e di gestione Driver ODBC è 3.8 (o versione successiva).  
  
-   L'intervallo di dati di tipo C specifici del driver è tra 0x4000 e 0x7FFF.  
  
-   Il driver definisce la struttura dei dati corrispondente al tipo di C.  Questa operazione può essere eseguita in SDK specifici del driver.  
  
 Gestione driver non verrà convalidato un tipo C definito nell'intervallo di 0x4000 e 0x7FFF; il driver esegue la convalida e qualsiasi conversione di tipi di dati. Tuttavia, se l'intervallo di dati di tipo C passato al gestore di driver è compreso tra 0x0000 e 0x3FFF o tra 0x8000 e 0xFFFF, Gestione driver convaliderà il tipo di dati C.  
  
> [!NOTE]  
>  Nella documentazione del driver, è necessario descrivere i tipi di dati C specifici del driver.  
  
 Per specificare un livello di conformità ODBC di 3.8, un'applicazione chiama [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md) attributo impostato su con il SQL_ATTR_ODBC_VERSION **SQL_OV_ODBC3_80**. Per determinare la versione del driver, un'applicazione chiama **SQLGetInfo** con SQL_DRIVER_ODBC_VER.  
  
 Per ulteriori informazioni su ODBC 3.8, vedere [novità di ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md)
