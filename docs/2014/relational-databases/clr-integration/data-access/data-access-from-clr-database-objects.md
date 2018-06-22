---
title: Accesso ai dati da oggetti di Database CLR | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], data access
- routines [CLR integration]
- data access [CLR integration]
- ADO.NET [CLR integration]
- internal data access [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], data access
- managed code [SQL Server], database objects
- .NET Data Access Provider for SQL Server [CLR integration]
- managed code [SQL Server], data access
- SqlClient provider
- in-process data access providers [CLR integration]
ms.assetid: 9a0f4dee-71c1-42e9-a85e-52382807010f
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ab43297c592258075e9c80ec9808b10c7bd267df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068537"
---
# <a name="data-access-from-clr-database-objects"></a>Accesso ai dati da oggetti di database CLR
  Una routine di common language runtime (CLR) può accedere facilmente ai dati archiviati nell'istanza di [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] in cui è in esecuzione, nonché ai dati archiviati in istanze remote. I dati specifici cui può accedere la routine sono determinati dal contesto utente in cui viene eseguito il codice. Accedere ai dati da un oggetto di database CLR utilizzando il Provider di dati .NET Framework per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dati provenienti da client gestiti e le applicazioni di livello intermedio. Per questo motivo, è possibile sfruttare la propria esperienza in ADO.NET e `SqlClient` in applicazioni client e di livello intermedio.  
  
> [!NOTE]  
>  Per impostazione predefinita, ai metodi con tipo definito dall'utente e alle funzioni definite dall'utente non è consentito eseguire accesso ai dati. È necessario impostare la proprietà `DataAccess` di `SqlMethodAttribute` o `SqlFunctionAttribute` su `DataAccessKind.Read` per consentire l'accesso ai dati di sola lettura da metodi con tipo definito dall'utente o funzioni definite dall'utente. Le operazioni di modifica dei dati non sono consentite da tipi definiti dall'utente o funzioni definite dall'utente e, in caso di un tentativo a tale scopo, vengono generate eccezioni in fase di esecuzione.  
  
 In questa sezione vengono illustrate solo le specifiche differenze funzionali e di comportamento durante l'accesso ai dati da un oggetto di database CLR. Per ulteriori informazioni su caratteristiche e funzionalità di ADO.NET, vedere la documentazione di ADO.NET inclusa in .NET Framework SDK.  
  
 Nella tabella seguente vengono elencati gli argomenti disponibili in questa sezione.  
  
 [Connessione di contesto](context-connection.md)  
 Viene descritta la connessione di contesto a SQL Server.  
  
 [Rappresentazione e credenziali per le connessioni](impersonation-and-credentials-for-connections.md)  
 Viene descritta la rappresentazione di connessioni e credenziali di connessione.  
  
 [Estensioni specifiche In-Process di SQL Server ad ADO.NET](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 Vengono descritti gli oggetti `SqlPipe`, `SqlContext`, `SqlTriggerContext` e `SqlDataRecord` specifici in-process.  
  
 [Integrazione con CLR e transazioni](../../native-client-ole-db-transactions/transactions.md)  
 Viene descritta l'integrazione del nuovo framework di transazioni fornito nello spazio dei nomi System.Transactions con ADO.NET e l'integrazione CLR di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Serializzazione XML da oggetti di Database CLR](../../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)  
 Viene illustrato come consentire scenari di serializzazione XML di oggetti di database CLR all'interno di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
  