---
title: La gestione di colonne Text e Image | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0768825a8c73b5da5325c15b1f04231ffe544e12
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35697702"
---
# <a name="managing-text-and-image-columns"></a>Gestione di colonne di tipo text e image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **testo**, **ntext**, e **immagine** dati (detto anche dati di tipo long) sono carattere o i tipi di dati stringa binari che possono contenere valori di dati troppo grande per **char**, **varchar**, **binario**, oppure **varbinary** colonne. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **testo** del tipo di dati esegue il mapping al tipo di dati ODBC SQL_LONGVARCHAR. **ntext** a SQL_WLONGVARCHAR e **immagine** a SQL_LONGVARBINARY. Alcuni elementi di dati, ad esempio i documenti lunghi o le bitmap di grandi dimensioni, potrebbero essere troppo grandi per essere archiviati correttamente in memoria. Da cui recuperare dati long [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in parti sequenziali, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client consente a un'applicazione di chiamare [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). Per inviare dati di tipo long in parti sequenziali, l'applicazione può chiamare [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md). I parametri per i quali i dati vengono inviati in fase di esecuzione sono noti come parametri data-at-execution.  
  
 Un'applicazione in realtà può scrivere o recuperare qualsiasi tipo di dati (non il tempo) con **SQLPutData** oppure **SQLGetData**, ma solo **carattere** e  **binario** dati possono essere inviati o recuperati in parti. Tuttavia, se i dati sono sufficientemente piccoli da rientrare in un unico buffer, non è in genere usare **SQLPutData** oppure **SQLGetData**. È molto più semplice associare il singolo buffer al parametro o alla colonna.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Colonne di tipo text e image associate e non associate](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [Modifiche registrate e non registrate](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [Colonne data-at-execution di tipo text, ntext o image](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
