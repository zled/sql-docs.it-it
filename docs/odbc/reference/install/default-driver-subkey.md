---
title: Predefinito sottochiave Driver | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- default subkey [ODBC]
- registry entries for components [ODBC], default subkey
- subkeys [ODBC], default subkey
- drivers subkey [ODBC]
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 64edd0f2a796c36b9c8a6efad971c7841b61a7ec
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="default-driver-subkey"></a>Sottochiave Driver predefinito
La sottochiave predefinito contiene un valore singolo che descrive il driver utilizzato dall'origine dati predefinito. Nella tabella seguente è illustrato il formato di questo valore.  
  
|Nome|Tipo di dati|data|  
|----------|---------------|----------|  
|**Driver**|REG_SZ|*descrizione predefinita-driver*|  
  
 Il *driver-predefinito-description* nome è identico al nome del valore della sottochiave driver ODBC che descrive il driver.  
  
 Ad esempio, se l'origine di dati predefinito utilizza il driver SQL Server, il valore della sottochiave predefinito può essere:  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  Il driver predefinito contenuto nella sottochiave predefinito può fare riferimento a un DSN dell'utente predefinito o un DSN di sistema predefinito. Se un DSN dell'utente predefinito sia il sistema DSN sono state create, il driver predefinito è determinato dal DSN che è stato creato per ultimo, in modo che non sia una voce valida per il DSN che è stata creata per prima.
