---
title: "Specifica le proprietà di connessione | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
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
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80da1a4da2d2a04f6a73b05e57ab366d2cb40e97
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
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
