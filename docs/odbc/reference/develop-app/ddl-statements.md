---
title: Istruzioni DDL | Documenti Microsoft
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
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], DDL statements
- DDL statements [ODBC]
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d077c86fb7a87658bc62d9530e9019e9f25da987
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909176"
---
# <a name="ddl-statements"></a>Istruzioni DDL
Istruzioni di Data Definition Language (DDL) variano notevolmente tra DBMS. SQL ODBC definisce le istruzioni per le operazioni più comuni di definizione dati: creazione ed eliminazione di tabelle, indici e viste. modifica di tabelle. e concedere e revocare i privilegi. Tutte le altre istruzioni DDL sono specifici dell'origine dati. Pertanto, applicazioni interoperative non è possibile eseguire alcune operazioni di definizione dati. In generale, non si tratta di un problema, perché tali operazioni tendono a essere elevata DBMS specifici e più a sinistra per il software di amministrazione di database proprietario fornito con la maggior parte dei DBMS o il programma di installazione fornita con il driver.  
  
 Un altro problema nella definizione dei dati è di quel tipo di dati i nomi di variano notevolmente tra DBMS. Anziché la definizione di nomi di tipi di dati standard e utilizzo forzato del driver per convertirli in nomi specifici del DBMS, **SQLGetTypeInfo** consente alle applicazioni di individuare i nomi di tipi di dati specifici del DBMS. Applicazioni interoperative devono utilizzare questi nomi nelle istruzioni SQL per creare e modificare tabelle. i nomi elencati nella [grammatica SQL di appendice c:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), e [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md), sono riportati solo alcuni esempi.
