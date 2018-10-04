---
title: Tipi di dati supportati | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], DBMS support
- interoperability [ODBC], data types
ms.assetid: a89d4bab-ef3c-45c2-aa72-2639b3e0f856
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2a8848bad9d27dfd9318b725b77203706d3dfd5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753259"
---
# <a name="supported-data-types"></a>Tipi di dati supportati
Tipi di dati supportati dai sistemi DBMS variano notevolmente. Un'applicazione può determinare i nomi e caratteristiche dei tipi di dati supportati chiamando **SQLGetTypeInfo**. A causa di ampia variazione nei nomi dei tipi di dati, l'applicazione deve utilizzare i nomi dei tipi di dati restituiti da **SQLGetTypeInfo** nelle **CREATE TABLE** istruzioni. Per altre informazioni, vedere [tipi di dati in ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).
