---
title: Tipi di dati di campo di Visual FoxPro | Documenti Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf6df134c5a4ad54e574e42e57d7a68e10b4e077
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="visual-foxpro-field-data-types"></a>Tipi di dati di campo di Visual FoxPro
Nella tabella seguente sono elencati i valori per il *FieldType* argomento nell'istruzione ALTER TABLE e CREATE TABLE e indica se *nFieldWidth* e *nPrecision* gli argomenti sono Obbligatorio.  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|Campo di caratteri della larghezza *n*|  
|D|-|-|Data|  
|F|N|d|Mobile campo numerico della larghezza *n* con *1!d* posizioni decimali|  
|G|-|-|Generale|  
|I|-|-|Integer|  
|L|-|-|Logico|  
|M|-|-|Memo|  
|N|N|d|Campo numerico della larghezza *n* con *1!d* posizioni decimali|  
|T|-|-|DateTime|  
|S|-|-|Currency|
