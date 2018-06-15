---
title: Specifica le proprietà di connessione | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c198eb4c8118328d68b40deed4ab0e57ff561f9c
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272661"
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
