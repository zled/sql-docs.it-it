---
title: Registrazione di Visual Studio. Le modifiche registrate | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-text-image-columns
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 39c969e390c3490ef6584f868a440d0b25c0053f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="logged-vs-unlogged-modifications"></a>Registrazione di Visual Studio. Modifiche registrate
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Un'applicazione può richiedere che il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client non registri **testo**, **ntext**, e **immagine** modifiche. Questa opzione deve essere utilizzata con una certa cautela e Deve essere utilizzato solo per i casi in cui il **testo**, **ntext**, o **immagine** dati non critici e i proprietari sono disposti a rinunciare alla possibilità di ripristinare i dati per prestazioni più elevate.  
  
 La registrazione di **testo**, **ntext**, e **immagine** le modifiche vengono controllate chiamando [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) con il  *Attributo* parametro impostato su sql_sopt_ss TEXTPTR_LOGGING apportate e *ValuePtr* impostato su SQL_TL_ON o SQL_TL_OFF.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di colonne di tipo text e image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
