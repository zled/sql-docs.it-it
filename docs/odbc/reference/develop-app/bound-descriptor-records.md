---
title: Associare i record del descrittore | Documenti Microsoft
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
- bound descriptor records [ODBC]
- descriptors [ODBC], bound descriptor records
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: acb8d22cc7d2af1efca121c70e99137df88f282b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="bound-descriptor-records"></a>Record del descrittore di binding
Quando l'applicazione imposta il campo SQL_DESC_DATA_PTR di un record di descrittore in modo che non contiene un valore null, il record è detto *associato*.  
  
 Se il descrittore è un APD, ogni record associato costituisce un parametro associato. Per i parametri di input, l'applicazione deve associare un parametro per ogni marcatore di parametro dinamico nell'istruzione SQL prima di eseguire l'istruzione. Per i parametri di output, l'applicazione non è necessario associare il parametro.  
  
 Se il descrittore è un ARD, che descrive una riga di dati del database, ogni record associato costituisce una colonna associata.
