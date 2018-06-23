---
title: Connessione di contesto | Documenti Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context connections [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- context [CLR integration]
ms.assetid: 67dd1925-d672-4986-a85f-bce4fe832ef7
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a95f4c4b190f37674290588714fc3e7b0c6582a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158003"
---
# <a name="context-connection"></a>Connessione di contesto
  Il problema dell'accesso ai dati interni rappresenta uno scenario comune. Si tratta della situazione in cui si desidera accedere allo stesso server su cui viene eseguita la funzione o la stored procedure CLR (Common Language Runtime). Una delle possibilità consiste nel creare una connessione utilizzando `System.Data.SqlClient.SqlConnection`, specificare una stringa di connessione che punta al server locale e aprire la connessione. Questa procedura richiede la specifica di credenziali per l'accesso. La connessione si trova in una sessione di database diversa dalla funzione o dalla stored procedure, può presentare opzioni `SET` diverse, si trova in una transazione separata, non vede le tabelle temporanee e così via. Se il codice di funzione o la stored procedure gestita sono in esecuzione nel processo di SQL Server, è perché qualcuno si è collegato a quel server e ha eseguito un'istruzione SQL per richiamarli. È probabile che si voglia eseguire la stored procedure o la funzione nel contesto di quella connessione, insieme alla rispettiva transazione, alle opzioni `SET` e così via. In questo caso si parla di connessione di contesto.  
  
 La connessione di contesto consente di eseguire istruzioni Transact-SQL nello stesso contesto nel quale è stato richiamato il codice. Per ottenere la connessione di contesto, è necessario utilizzare la parola chiave relativa alla stringa di connessione "context connection", come nell'esempio seguente:  
  
 [C#]  
  
```  
using(SqlConnection connection = new SqlConnection("context connection=true"))   
{  
    connection.Open();  
    // Use the connection  
}  
```  
  
 [Visual Basic]  
  
```  
Using connection as new SqlConnection("context connection=true")  
    connection.Open()  
    ' Use the connection  
End Using  
  
```  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Visual Studio regolare. Connessioni di contesto](context-connections-vs-regular-connections.md)  
 Vengono descritte le differenze tra le connessioni normali e di contesto.  
  
 [Restrizioni sulle normali e connessioni di contesto](context-connections-and-regular-connections-restrictions.md)  
 Vengono descritte le restrizioni relative alle connessioni normali e di contesto.  
  
  