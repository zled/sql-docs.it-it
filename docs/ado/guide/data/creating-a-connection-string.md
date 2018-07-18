---
title: Creazione di una stringa di connessione | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
- connection strings [ADO]
ms.assetid: 14eae122-2d1e-40c8-b88e-b7cb8dfbc93b
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc700bdc0006a4591e61e15f2796b73c194dc5a1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-connection-string"></a>Creazione di una stringa di connessione
Una stringa di connessione è costituita da un elenco di coppie valore/argomento (ovvero, i parametri), separato da punti e virgola. Esempio:  
  
```  
"arg1=val1; arg2=val2; ... argN=valN;"  
```  
  
 Tutti i parametri devono essere riconosciuti da ADO o il provider specificato.  
  
 ADO riconosce i seguenti cinque argomenti in una stringa di connessione.  
  
|Argomento|Description|  
|--------------|-----------------|  
|*Provider*|Specifica il nome di un provider da utilizzare per la connessione.|  
|*Nome file*|Specifica il nome di un file specifico del provider (ad esempio, un oggetto origine dati persistenti) contenente informazioni di connessione predefinite.|  
|*URL*|Specifica la stringa di connessione come un URL assoluto che identifica una risorsa, ad esempio un file o directory.|  
|*Provider remoto*|Specifica il nome di un provider da utilizzare quando si apre una connessione sul lato client. (Solo servizio dati remota).|  
|*Server remoto*|Specifica il nome del percorso del server da utilizzare quando si apre una connessione sul lato client. (Solo servizio dati remota).|  
  
 Altri argomenti vengono passati al provider denominato nel *Provider* argomento, senza alcuna elaborazione da parte di ADO.  
  
 L'applicazione HelloData nel [HelloData: una semplice applicazione ADO](../../../ado/guide/data/hellodata-a-simple-ado-application.md) utilizzata la stringa di connessione seguente:  
  
```  
m_sConnStr = "Provider=SQLOLEDB;Data Source=MySqlServer;" & _  
             "Initial Catalog=Northwind;Integrated Security='SSPI';"  
```  
  
 In questa stringa di connessione ADO riconosce solo il `"Provider=SQLOLEDB"` parametro che specifica il Provider Microsoft OLE DB per SQL Server come origine dati ADO. Il resto delle coppie, argomento o valore `"Data Source=MySqlServer; Initial Catalog=Northwind;Integrated Security='SSPI';"`, verbatim vengono passati al provider. Il tipo e la validità di tali parametri sono specifici del provider. Per informazioni sui parametri validi che può essere passato nella stringa di connessione, consultare la documentazione del provider singoli.  
  
 Secondo il Provider OLE DB per la documentazione di SQL Server, è possibile sostituire "Server" per il *origine dati* parametro e "Database" per il *Initial Catalog* parametro. Di conseguenza, la stringa di connessione seguente produca risultati identici a quello riportato sopra:  
  
```  
m_sConnStr = "Provider=SQLOLEDB;Server=MySqlServer;" & _  
             "Database=Northwind;Integrated Security='SSPI';"  
```
