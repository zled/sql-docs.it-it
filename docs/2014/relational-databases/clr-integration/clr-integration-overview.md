---
title: Panoramica dell'integrazione con CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], about CLR integration
- extended stored procedures [SQL Server], vs. managed code
- objects [CLR integration]
- Transact-SQL vs. managed code
- managed code [SQL Server], vs. Transact-SQL
- managed code [SQL Server], vs. extended stored procedures
- execution at client vs. execution at server [CLR integration]
ms.assetid: 5aa176da-3652-4afa-a742-4c40c77ce5c3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 762c644690cb556ba316705f1e22e3673e811bf1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077711"
---
# <a name="overview-of-clr-integration"></a>Panoramica dell'integrazione con CLR
  Common Language Runtime (CLR) rappresenta il fulcro di Microsoft .NET Framework e fornisce l'ambiente di esecuzione per tutto il codice .NET Framework. Il codice eseguito in CLR viene chiamato codice gestito. CLR fornisce varie funzioni e servizi necessari per l'esecuzione del programma, incluse le funzioni di compilazione JIT (Just-In-Time), di allocazione e gestione della memoria, di imposizione dell'indipendenza dai tipi, di gestione delle eccezioni, di gestione dei thread e di sicurezza.  Per ulteriori informazioni, vedere .NET Framework SDK.  
  
 Grazie all'integrazione di CLR in Microsoft SQL Server, è possibile creare stored procedure, trigger, funzioni definite dall'utente, tipi definiti dall'utente e aggregazioni definite dall'utente nel codice gestito. Poiché il codice gestito viene compilato nel codice nativo prima dell'esecuzione, è possibile ottenere notevoli miglioramenti delle prestazioni in alcuni scenari.  
  
 Nel codice gestito viene utilizzata la sicurezza dall'accesso di codice (CAS) per gli assembly eseguano determinate operazioni. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizza CAS per aiutare a proteggere il codice gestito e impedire che il sistema operativo o il server di database vengano compromessi.  
  
## <a name="advantages-of-clr-integration"></a>Vantaggi dell'integrazione con CLR  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] è progettato in maniera specifica per consentire di accedere ai dati e modificarli direttamente nel database. Sebbene [!INCLUDE[tsql](../../../includes/tsql-md.md)] risulti particolarmente vantaggioso per l'accesso ai dati e la loro gestione, non è un linguaggio di programmazione completo. [!INCLUDE[tsql](../../../includes/tsql-md.md)] non supporta, ad esempio, matrici, raccolte, cicli Foreach, scorrimento bit o classi. Il codice gestito dispone di supporto integrato per questi costrutti, sebbene sia possibile simularne alcuni in [!INCLUDE[tsql](../../../includes/tsql-md.md)]. A seconda dello scenario, l'implementazione di determinate caratteristiche del database nel codice gestito può risultare particolarmente vantaggiosa.  
  
 Microsoft Visual Basic .NET e Microsoft Visual C# offrono funzionalità orientate a oggetti quali incapsulamento, ereditarietà e polimorfismo. Il codice correlato può ora essere organizzato facilmente in classi e spazi dei nomi. In questo modo è possibile organizzare e gestire il codice più facilmente quando si utilizzano grandi quantità di codice server.  
  
 Il codice gestito risulta più appropriato di [!INCLUDE[tsql](../../../includes/tsql-md.md)] per i calcoli e la logica di esecuzione complicata e dispone inoltre di un supporto esteso per numerose attività complesse, ad esempio la gestione delle stringhe e le espressioni regolari. Grazie alle funzionalità della libreria .NET Framework, è possibile accedere facilmente a migliaia di classi e routine preesistenti da qualsiasi stored procedure, trigger o funzione definita dall'utente. La libreria di classi di base (BCL, Base Class Library) include classi che forniscono funzionalità per la modifica delle stringhe, operazioni matematiche avanzate, accesso ai file, crittografia e altro ancora.  
  
> [!NOTE]  
>  Sebbene molte di queste classi siano disponibili nel codice CLR in SQL Server, quelle che non sono appropriate per l'utilizzo sul lato server, ad esempio le classi di windowing, non risultano disponibili. Per altre informazioni, vedere [librerie di .NET Framework supportate](database-objects/supported-net-framework-libraries.md).  
  
 Uno dei vantaggi del codice gestito è l'indipendenza dai tipi o la garanzia che il codice acceda ai tipi solo con modalità consentite e ben definite. Prima che venga eseguito il codice gestito, CLR verifica che il codice sia sicuro. Viene ad esempio eseguito un controllo del codice per verificare che non venga letta memoria che non sia stata scritta in precedenza. CLR è inoltre in grado di garantire che il codice non modifichi la memoria non gestita.  
  
 L'integrazione con CLR offre un potenziale miglioramento delle prestazioni. Per informazioni, vedere [sulle prestazioni dell'integrazione con CLR](clr-integration-architecture-performance.md).  
  
## <a name="choosing-between-transact-sql-and-managed-code"></a>Scelta tra Transact-SQL e codice gestito  
 Quando si scrivono stored procedure, trigger e funzioni definite dall'utente, è necessario decidere se utilizzare il linguaggio [!INCLUDE[tsql](../../../includes/tsql-md.md)] tradizionale o un linguaggio .NET Framework, quale Visual Basic .NET o Visual C#. Utilizzare [!INCLUDE[tsql](../../../includes/tsql-md.md)] quando tramite il codice verrà eseguito soprattutto l'accesso ai dati, con una logica procedurale ridotta o nulla. Utilizzare codice gestito per le procedure e le funzioni che richiedono un utilizzo elevato della CPU e sono caratterizzate da una logica complessa o quando si desidera utilizzare la libreria di classi di base di .NET Framework.  
  
### <a name="choosing-between-execution-in-the-server-and-execution-in-the-client"></a>Scelta tra l'esecuzione nel server e nel client  
 Un altro aspetto che incide sulla decisione di utilizzare [!INCLUDE[tsql](../../../includes/tsql-md.md)] o il codice gestito è la posizione in cui si desidera che risieda il codice, ovvero il computer server o il computer client. Sia [!INCLUDE[tsql](../../../includes/tsql-md.md)] che il codice gestito possono essere eseguiti nel server. In questo modo, il codice e i dati si troveranno vicini e sarà possibile usufruire delle capacità di elaborazione del server. D'altra parte, è possibile che si desideri evitare di collocare le attività che richiedono un utilizzo elevato del processore sul server di database. La maggior parte dei moderni computer client è piuttosto potente ed è possibile che si desideri usufruire di queste capacità di elaborazione posizionando la quantità maggiore possibile di codice sul client. Diversamente da [!INCLUDE[tsql](../../../includes/tsql-md.md)], il codice gestito può essere eseguito in un computer client.  
  
## <a name="choosing-between-extended-stored-procedures-and-managed-code"></a>Scelta tra stored procedure estese e codice gestito  
 Le stored procedure estese consentono di ottenere funzionalità altrimenti non disponibili con le stored procedure [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Diversamente dal codice gestito indipendente dai tipi, tuttavia, le stored procedure estese possono compromettere l'integrità del processo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La gestione della memoria, la pianificazione di thread e fiber e i servizi di sincronizzazione sono, inoltre, notevolmente più integrati tra il codice gestito di CLR e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Grazie all'integrazione con CLR, è possibile scrivere le stored procedure necessarie per eseguire attività non consentite in [!INCLUDE[tsql](../../../includes/tsql-md.md)] in modo più sicuro rispetto alle stored procedure estese. Per altre informazioni sull'integrazione con CLR e stored procedure estese, vedere [sulle prestazioni dell'integrazione con CLR](clr-integration-architecture-performance.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di .NET Framework](http://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx)   
 [Architettura dell'integrazione con CLR](../../database-engine/dev-guide/architecture-of-clr-integration.md)   
 [Accesso ai dati da oggetti di Database CLR](data-access/data-access-from-clr-database-objects.md)   
 [Introduzione all'integrazione con CLR](database-objects/getting-started-with-clr-integration.md)  
  
  
