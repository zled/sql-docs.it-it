---
title: La gestione di colonne Text e Image | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1316f093ac0d1f79c5155ae1be88df98f091bd8f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168996"
---
# <a name="managing-text-and-image-columns"></a>Gestione di colonne di tipo text e image
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **testo**, **ntext**, e **immagine** dati (detto anche dati di tipo long) sono carattere o i tipi di dati stringa binari che possono contenere valori di dati troppo grande per **char**, **varchar**, **binario**, oppure **varbinary** colonne. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **testo** del tipo di dati esegue il mapping al tipo di dati ODBC SQL_LONGVARCHAR. **ntext** a SQL_WLONGVARCHAR e **immagine** a SQL_LONGVARBINARY. Alcuni elementi di dati, ad esempio i documenti lunghi o le bitmap di grandi dimensioni, potrebbero essere troppo grandi per essere archiviati correttamente in memoria. Da cui recuperare dati long [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in parti sequenziali, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client consente a un'applicazione di chiamare [SQLGetData](../native-client-odbc-api/sqlgetdata.md). Per inviare dati di tipo long in parti sequenziali, l'applicazione può chiamare [SQLPutData](../native-client-odbc-api/sqlputdata.md). I parametri per i quali i dati vengono inviati in fase di esecuzione sono noti come parametri data-at-execution.  
  
 Un'applicazione in realtà può scrivere o recuperare qualsiasi tipo di dati (non il tempo) con **SQLPutData** oppure **SQLGetData**, ma solo **carattere** e  **binario** dati possono essere inviati o recuperati in parti. Tuttavia, se i dati sono sufficientemente piccoli da rientrare in un unico buffer, non è in genere usare **SQLPutData** oppure **SQLGetData**. È molto più semplice associare il singolo buffer al parametro o alla colonna.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Colonne di tipo text e image associate e non associate](bound-vs-unbound-text-and-image-columns.md)  
  
-   [Modifiche registrate e non registrate](logged-vs-unlogged-modifications.md)  
  
-   [Colonne data-at-execution di tipo text, ntext o image](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  