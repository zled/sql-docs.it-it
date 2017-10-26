---
title: Tipi di dati di campo di Visual FoxPro | Documenti Microsoft
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
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7c1ae849d91962cb7d11ca8bac755665217fe1a2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="visual-foxpro-field-data-types"></a>Tipi di dati di campo di Visual FoxPro
Nella tabella seguente sono elencati i valori per il *FieldType* argomento nell'istruzione ALTER TABLE e CREATE TABLE e indica se *nFieldWidth* e *nPrecision* gli argomenti sono Obbligatorio.  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|Campo della larghezza di caratteri*n*|  
|D|-|-|Data|  
|F|N|d|A virgola mobile a un campo numerico della larghezza * n * con *d* posizioni decimali|  
|G|-|-|Generale|  
|I|-|-|Valore intero|  
|L|-|-|Logico|  
|M|-|-|Memo|  
|N|N|d|Campo numerico della larghezza * n * con *d* posizioni decimali|  
|T|-|-|DateTime|  
|S|-|-|Currency|

