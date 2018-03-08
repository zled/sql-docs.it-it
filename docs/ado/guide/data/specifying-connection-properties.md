---
title: "Specifica le proprietà di connessione | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6e07a16be9d12aa905abbad4b2007726b853d805
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="specifying-connection-properties"></a>Specifica le proprietà di connessione
È possibile fornire la maggior parte delle informazioni specificate da un [stringa di connessione](../../../ado/guide/data/creating-a-connection-string.md) impostando le proprietà del **connessione** oggetto prima dell'apertura della connessione. Ad esempio, è possibile ottenere lo stesso effetto come stringa di connessione illustrato in [la creazione di una stringa di connessione](../../../ado/guide/data/creating-a-connection-string.md) usando il codice seguente.  
  
```  
With objConn  
.Provider = "SQLOLEDB"  
.Properties("Data Source") = "MySqlServer"  
   .Properties("Integrated Security") = "SSPI"  
.Open  
.DefaultDatabase = "Northwind"  
End With  
```  
  
 DefaultDatabase è impostato solo dopo aver aperto la connessione.  
  
> [!NOTE]
>  In ADO non è necessario utilizzare una password contenente un punto e virgola (";"), a meno che la password è racchiuso tra virgolette singole.
