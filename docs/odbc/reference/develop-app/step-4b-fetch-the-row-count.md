---
title: 'Passaggio 4b: recuperare il conteggio delle righe | Documenti Microsoft'
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
- fetches [ODBC], fetching row count
- row count [ODBC]
- application process [ODBC], fetching row count
ms.assetid: 3af481b1-d694-446e-948d-e3a5edcad050
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 797920b512d117394c92fcc9c47006fbb84a22d5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="step-4b-fetch-the-row-count"></a>Passaggio 4b: recuperare il conteggio delle righe
Il passaggio successivo è recuperare il conteggio delle righe, come illustrato nella figura seguente.  
  
 ![Illustra il recupero del conteggio delle righe](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Se l'istruzione eseguita nel passaggio 3 è un **aggiornamento**, **eliminare**, o **inserire** istruzione, l'applicazione recupera il conteggio delle righe interessate con  **SQLRowCount**. Per ulteriori informazioni, vedere [determinare il numero di righe interessate](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 A questo punto, l'applicazione restituisce al passaggio 3 per l'esecuzione di un'altra istruzione nella stessa transazione o procede al passaggio 5 per eseguire il commit o il rollback della transazione.
