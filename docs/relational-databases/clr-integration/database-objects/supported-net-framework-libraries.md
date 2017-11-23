---
title: Librerie di .NET Framework supportati | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
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
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b6153914ef43333ad2feefb1dd428974c15eb83b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="supported-net-framework-libraries"></a>Librerie .NET Framework supportate
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Con common language runtime (CLR) ospitati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], è possibile creare stored procedure, trigger, funzioni definite dall'utente, tipi definiti dall'utente e aggregati definiti dall'utente nel codice gestito. Con le librerie di classi .NET Framework è possibile accedere alle classi preesistenti che offrono funzionalità per manipolazione delle stringhe, operazioni matematiche avanzate, accesso ai file, crittografia e così via. A queste classi è possibile accedere da stored procedure gestite, tipi definiti dall'utente, trigger, funzioni definite dall'utente o funzioni di aggregazione definite dall'utente.  
  
> [!NOTE]  
>  Se si gestiscono o aggiornano assembly non supportati nella Global Assembly Cache (GAC), è possibile che si arresti il funzionamento dell'applicazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ciò si verifica in quanto le operazioni di gestione o aggiornamento delle librerie presenti nella GAC non determinano l'aggiornamento degli assembly che si trovano in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se un assembly è presente sia in un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sia nella GAC, le due copie relative devono corrispondere esattamente. Se non corrispondono, si verificherà un errore quando l'assembly verrà usato dalla funzionalità di integrazione con CLR di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se si gestiscono o aggiornano assembly nella GAC che vengono registrati anche nel database, inclusi gli assembly di .NET Framework non supportati, assicurarsi anche gestiscono o aggiornano la copia dell'assembly all'interno del [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database con il  **Istruzione ALTER ASSEMBLY** istruzione. Per ulteriori informazioni, vedere [articolo 949080 della Knowledge Base](http://support.microsoft.com/kb/949080).  
  
## <a name="supported-libraries"></a>Librerie supportate  
 A partire da [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è disponibile un elenco di librerie .NET Framework supportate, che sono state testate per verificare che rispettino gli standard di sicurezza e di affidabilità per l'interazione con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le librerie supportate non devono essere registrate in modo esplicito nel server prima che possano essere utilizzate nel codice. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consente di caricarle direttamente dalla Global Assembly Cache (GAC).  
  
 Le librerie e gli spazi dei nomi supportati dall'integrazione con CLR in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono:  
  
-   CustomMarshalers  
  
-   Microsoft.VisualBasic  
  
-   Microsoft.VisualC  
  
-   mscorlib  
  
-   Sistema  
  
-   System.Configuration  
  
-   System.Data  
  
-   System.Data.OracleClient  
  
-   System.Data.SqlXml  
  
-   System.Deployment  
  
-   System.Security  
  
-   System.Transactions  
  
-   System.Web.Services  
  
-   System.Xml  
  
-   System.Core.dll  
  
-   System.Xml.Linq.dll  
  
## <a name="unsupported-libraries"></a>Librerie non supportate  
 Le librerie non supportate possono essere comunque chiamate da stored procedure gestite, trigger, funzioni definite dall'utente, tipi definiti dall'utente e funzioni di aggregazione definite dall'utente. La libreria non supportata deve prima essere registrata nel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, utilizzando il **CREATE ASSEMBLY** istruzione, prima di poter essere utilizzato nel codice. È necessario verificare e testare la sicurezza e l'affidabilità delle librerie non supportate registrate ed eseguite nel server.  
  
 Ad esempio, il **System. DirectoryServices** dello spazio dei nomi non è supportata. È necessario registrare l'assembly System.DirectoryServices.dll con **UNSAFE** autorizzazioni prima di poter chiamare dal codice. Il **UNSAFE** autorizzazione è necessaria perché le classi nel **System. DirectoryServices** dello spazio dei nomi non soddisfano i requisiti per **provvisoria** o  **EXTERNAL_ACCESS**. Per ulteriori informazioni, vedere [restrizioni del modello di programmazione integrazione CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md) e [sicurezza dall'accesso di codice CLR Integration](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [Sicurezza di accesso di codice dell'integrazione CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Restrizioni relative al modello di programmazione dell'integrazione con CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)  
  
  
