---
title: Tipi di dati Visual FoxPro campo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07aa06eae9f1e75a047bdd302754d884790436e1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806121"
---
# <a name="visual-foxpro-field-data-types"></a>Tipi di dati dei campi Visual FoxPro
Nella tabella seguente sono elencati i valori per il *FieldType* argomento nell'istruzione ALTER TABLE e CREATE TABLE indicando se *nFieldWidth* e *nPrecision* gli argomenti sono Obbligatorio.  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|c|N|-|Campo di caratteri della larghezza *n*|  
|D|-|-|date|  
|F|N|d|Mobile campo numerico della larghezza *n* con *1!d* posizioni decimali|  
|G|-|-|Generale|  
|I|-|-|Valore intero|  
|L|-|-|Logico|  
|M|-|-|Memo|  
|N|N|d|Campo numerico della larghezza *n* con *1!d* posizioni decimali|  
|T|-|-|DateTime|  
|Y|-|-|Currency|
