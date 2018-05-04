---
title: DOVE clausola limitazioni | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, WHERE clause limitations
- WHERE clause limitations [ODBC]
ms.assetid: 46b54f74-e4a3-4318-87cf-8a97c38a2718
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e1a9b9485004b46cd6563835e880f801d36dc0eb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="where-clause-limitations"></a>DOVE clausola limitazioni
Il numero massimo di clausole in una clausola WHERE è 40.  
  
 Colonne LONGVARBINARY e LONGVARCHAR possono essere confrontate con i valori letterali di fino a 255 caratteri, ma non possono essere confrontate con i parametri.
