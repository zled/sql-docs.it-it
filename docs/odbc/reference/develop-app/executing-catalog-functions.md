---
title: L'esecuzione di funzioni di catalogo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], executing
- functions [ODBC], catalog functions
ms.assetid: c59cbda3-e214-4399-9edc-cfac86b378d7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: daf1ab2fc05b198e71b45cb02b4577eebee5c5b6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704289"
---
# <a name="executing-catalog-functions"></a>Esecuzione delle funzioni di catalogo
Poiché una funzione di catalogo crea un set di risultati, è equivalente all'esecuzione di qualsiasi istruzione SQL: generazione di set di risultati. In effetti, funzioni di catalogo vengono spesso implementate l'esecuzione di istruzioni SQL predefinite o chiamando le procedure predefinite che vengono fornite con il driver o DBMS. Quasi tutto ciò che si applica alle istruzioni SQL che creano set di risultati si applica anche alle funzioni di catalogo. Ad esempio, l'attributo di istruzione SQL_ATTR_MAX_ROWS limita il numero di righe restituite dalla funzione di catalogo, esattamente come limita il numero di righe restituite da una **seleziona** istruzione.  
  
 Per eseguire una funzione di catalogo, un'applicazione chiama semplicemente la funzione.  
  
 Per altre informazioni sulle funzioni di catalogo, vedere [funzioni di catalogo](../../../odbc/reference/develop-app/catalog-functions.md).
