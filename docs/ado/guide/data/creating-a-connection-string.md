---
title: Creazione di una stringa di connessione | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
- connection strings [ADO]
ms.assetid: 14eae122-2d1e-40c8-b88e-b7cb8dfbc93b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 41732b25c7b2c02f5b6b8a319e057d204a3a3384
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611387"
---
# <a name="creating-a-connection-string"></a>Creazione di una stringa di connessione
Una stringa di connessione è costituita da un elenco di coppie valore/argomento (vale a dire, parametri), separato da punti e virgola. Esempio:  
  
```  
"arg1=val1; arg2=val2; ... argN=valN;"  
```  
  
 Tutti i parametri devono essere riconosciuti da ADO o il provider specificato.  
  
 ADO riconosce i seguenti cinque argomenti in una stringa di connessione.  
  
|Argomento|Description|  
|--------------|-----------------|  
|*Provider*|Specifica il nome di un provider da utilizzare per la connessione.|  
|*Nome file*|Specifica il nome di un file specifico del provider (ad esempio, un oggetto origine dati persistenti) che contiene informazioni di connessione predefinite.|  
|*URL*|Specifica la stringa di connessione come un URL assoluto che identifica una risorsa, ad esempio un file o directory.|  
|*Provider remoto*|Specifica il nome di un provider da utilizzare quando si apre una connessione client-side. (Solo servizio dati remoto).|  
|*Server remoto*|Specifica il nome del percorso del server da usare quando si apre una connessione client-side. (Solo servizio dati remoto).|  
  
 Altri argomenti vengono passati al provider denominato nel *Provider* argomento, senza alcuna elaborazione da parte di ADO.  
  
 L'applicazione di HelloData nelle [HelloData: una semplice applicazione ADO](../../../ado/guide/data/hellodata-a-simple-ado-application.md) usata la stringa di connessione seguente:  
  
```  
m_sConnStr = "Provider=SQLOLEDB;Data Source=MySqlServer;" & _  
             "Initial Catalog=Northwind;Integrated Security='SSPI';"  
```  
  
 In questa stringa di connessione ADO riconosce solo il `"Provider=SQLOLEDB"` parametro che specifica il Provider Microsoft OLE DB per SQL Server come origine dati ADO. Il resto delle coppie di valore dell'argomento /, `"Data Source=MySqlServer; Initial Catalog=Northwind;Integrated Security='SSPI';"`, vengono passati verbatim per questo provider. Il tipo e la validità di tali parametri sono specifici del provider. Per informazioni sui parametri validi che può essere passato nella stringa di connessione, consultare la documentazione del provider singoli.  
  
 Secondo il Provider OLE DB per la documentazione di SQL Server, è possibile sostituire "Server" per il *Zdroj dat* parametro e "Database" per il *Initial Catalog* parametro. Di conseguenza, la stringa di connessione seguente produrrà risultati identici a quello riportato sopra:  
  
```  
m_sConnStr = "Provider=SQLOLEDB;Server=MySqlServer;" & _  
             "Database=Northwind;Integrated Security='SSPI';"  
```
