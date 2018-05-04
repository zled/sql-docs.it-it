---
title: L'esecuzione di funzioni di catalogo | Documenti Microsoft
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
- catalog functions [ODBC], executing
- functions [ODBC], catalog functions
ms.assetid: c59cbda3-e214-4399-9edc-cfac86b378d7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 854a7e7fe347bb02c59fe1608afd74bf87be6b7b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="executing-catalog-functions"></a>L'esecuzione di funzioni di catalogo
Poiché una funzione di catalogo crea un set di risultati, è equivalente all'esecuzione di qualsiasi istruzione SQL: generazione di set di risultati. In effetti, le funzioni di catalogo spesso vengono implementate mediante l'esecuzione di istruzioni SQL predefinite o chiamata di routine predefiniti forniti con il driver o DBMS. Quasi tutto ciò che si applica a SQL per la creazione di set di risultati si applica anche alle funzioni di catalogo. Ad esempio, l'attributo di istruzione SQL_ATTR_MAX_ROWS limita il numero di righe restituite dalla funzione di catalogo, esattamente come limita il numero di righe restituite da una **selezionare** istruzione.  
  
 Per eseguire una funzione di catalogo, un'applicazione chiama semplicemente la funzione.  
  
 Per ulteriori informazioni sulle funzioni di catalogo, vedere [funzioni di catalogo](../../../odbc/reference/develop-app/catalog-functions.md).
