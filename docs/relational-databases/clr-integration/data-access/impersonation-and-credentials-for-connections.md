---
title: Rappresentazione e credenziali per le connessioni | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0815ae6b182f371eb171cf577e89a50adb9cdac4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="impersonation-and-credentials-for-connections"></a>Rappresentazione e credenziali per le connessioni
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Nel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] integrazione common language runtime (CLR), utilizzando l'autenticazione di Windows è complesso, ma è più sicura dell'autenticazione di SQL Server. Utilizzando l'autenticazione di Windows, è necessario tenere conto di alcune considerazioni.  
  
 Per impostazione predefinita, un processo di SQL Server che si connette a Windows acquisisce il contesto di sicurezza dell'account di servizio Windows di SQL Server. È tuttavia possibile eseguire il mapping di una funzione CLR a un'identità del proxy, in modo che le connessioni in uscita dispongano di un contesto di sicurezza diverso da quello dell'account di servizio Windows.  
  
 In alcuni casi, si desidera rappresentare il chiamante utilizzando il **SqlContext.WindowsIdentity** proprietà anziché in esecuzione come account del servizio. Il **WindowsIdentity** istanza rappresenta l'identità del client che ha richiamato il codice chiamante ed è disponibile solo quando il client utilizza l'autenticazione di Windows. Dopo aver ottenuto il **WindowsIdentity** istanza, è possibile chiamare **Impersonate** per modificare il token di sicurezza del thread, quindi aprire connessioni ADO.NET per conto del client.  
  
 Dopo aver chiamato SQLContext.WindowsIdentity.Impersonate, non è possibile accedere a dati locali e non è possibile accedere ai dati di sistema. Per accedere ai dati, è necessario chiamare WindowsImpersonationContext.  
  
 Nell'esempio seguente viene illustrato come rappresentare il chiamante utilizzando il **SqlContext.WindowsIdentity** proprietà.  
  
 Visual C#  
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  Per informazioni sulle modifiche al comportamento della rappresentazione, vedere [modifiche di rilievo alle funzionalità del motore di Database in SQL Server 2016](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Inoltre, se è stata ottenuta l'istanza dell'identità di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, per impostazione predefinita non è possibile propagarla in un altro computer, in quanto la propagazione è limitata dall'infrastruttura di sicurezza di Windows. Esiste tuttavia un meccanismo noto come "delega" che abilita la propagazione delle identità di Windows in più computer attendibili. Altre informazioni sulla delega nell'articolo di TechNet, "[transizione del protocollo Kerberos e delega vincolata](http://go.microsoft.com/fwlink/?LinkId=50419)".  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto SqlContext](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
