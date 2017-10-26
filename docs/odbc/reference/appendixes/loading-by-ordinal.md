---
title: Caricamento tramite l'ordinale | Documenti Microsoft
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
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ef22486a7cbd9932c90069f461b83358c2db8fd4
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="loading-by-ordinal"></a>Caricamento da ordinale
In ODBC 2. *x*, è possibile eseguire il caricamento da numero ordinale per migliorare le prestazioni del processo di connessione. Un database ODBC 2. *x* driver Esporta una funzione fittizia con l'ordinale 199; quando Gestione Driver rileva, risolve gli indirizzi delle funzioni ODBC per ordinale e non per nome. Questa funzionalità è ancora supportata per l'API ODBC 2. *x* driver ma non è supportata per ODBC 3*x* driver.

