---
title: Associare i record del descrittore | Documenti Microsoft
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
- bound descriptor records [ODBC]
- descriptors [ODBC], bound descriptor records
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d1ecc435a6b62d75527292ab8dc098e8cb121627
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="bound-descriptor-records"></a>Record del descrittore di binding
Quando l'applicazione imposta il campo SQL_DESC_DATA_PTR di un record di descrittore in modo che non contiene un valore null, il record è detto *associato*.  
  
 Se il descrittore è un APD, ogni record associato costituisce un parametro associato. Per i parametri di input, l'applicazione deve associare un parametro per ogni marcatore di parametro dinamico nell'istruzione SQL prima di eseguire l'istruzione. Per i parametri di output, l'applicazione non è necessario associare il parametro.  
  
 Se il descrittore è un ARD, che descrive una riga di dati del database, ogni record associato costituisce una colonna associata.

