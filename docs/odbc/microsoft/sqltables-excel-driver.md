---
title: SQLTables (Driver per Excel) | Documenti Microsoft
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
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2921d9e047e03cae092e5c0e7d2fcd4e4f8f24c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32903616"
---
# <a name="sqltables-excel-driver"></a>SQLTables (Driver per Excel)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver Excel. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argomento|Commenti|  
|--------------|--------------|  
|*szTableOwner*|L'argomento valido solo per *szTableOwner* è NULL perché nessuno dei driver supporta i nomi dei proprietari. Con *szTableOwner* impostato su NULL, vengono restituite tutte le tabelle. Nella colonna TABLE_OWNER viene restituito NULL.|  
|*szTableQualifier*|Quando Microsoft Excel 3.0 o 4.0 driver viene usato, se si chiama **SQLTables** con un valore per *szTableQualifier* che non è il nome di una tabella esistente, il driver creerà una tabella con lo stesso nome.<br /><br /> Nella colonna TABLE_QUALIFIER **SQLTables** restituirà il percorso in una directory.|  
|*SzTableType*|Per Microsoft Excel 3.0 o 4.0, "TABLE" è l'unico tipo di tabella è supportato.<br /><br /> Per le versioni successive dei file di Microsoft Excel, viene restituita "Tabella di sistema" per i nomi dei fogli (le tabelle con "$" alla fine) e viene restituito "TABLE" per le tabelle all'interno di fogli di lavoro.|
