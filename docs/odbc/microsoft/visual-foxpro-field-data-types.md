---
title: Tipi di dati di campo di Visual FoxPro | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2b4dbb88985b114e0e2f89c4a3f57d8dae4c9210
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="visual-foxpro-field-data-types"></a>Tipi di dati di campo di Visual FoxPro
Nella tabella seguente sono elencati i valori per il *FieldType* argomento nell'istruzione ALTER TABLE e CREATE TABLE e indica se *nFieldWidth* e *nPrecision* gli argomenti sono Obbligatorio.  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|Campo della larghezza di caratteri*n*|  
|D|-|-|Data|  
|F|N|d|A virgola mobile a un campo numerico della larghezza  *n*  con *d* posizioni decimali|  
|G|-|-|Generale|  
|I|-|-|Valore intero|  
|L|-|-|Logico|  
|M|-|-|Memo|  
|N|N|d|Campo numerico della larghezza  *n*  con *d* posizioni decimali|  
|T|-|-|DateTime|  
|S|-|-|Currency|
