---
title: Non consentito di tipi e membri in Data. dll | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c222c10fe13a422e5195970057fbb623cc960a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066101"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>Tipi e membri non consentiti in System.Data.dll
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programmazione dell'integrazione con (CLR) linguaggio comuni non consente l'utilizzo di un tipo o membro che dispone di un `HostProtectionAttribute` che specifica un `System.Security.Permissions.HostProtectionResource` con un valore di enumerazione `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **SharedState**, `Synchronization`, o `UI`. Nella tabella seguente sono elencati i membri e i tipi dell'assembly System.Data.dll i cui valori degli attributi di protezione host non sono consentiti.  
  
> [!NOTE]  
>  Questo elenco è stato generato dagli assembly supportati. Per altre informazioni, vedere [librerie di .NET Framework supportata](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
|Tipo o membro|Valori dell'attributo di protezione host|  
|--------------------|--------------------|  
|System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteReader()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency..ctor()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Start()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Stop()|ExternalThreading|  
|System.Data.TypedDataSetGenerator|SharedState, Synchronization|  
|System.Xml.XmlDataDocument|Synchronization|  
  
## <a name="see-also"></a>Vedere anche  
 [Attributi di protezione host e programmazione dell'integrazione con CLR](host-protection-attributes-and-clr-integration-programming.md)   
 [Tipi non consentiti e i membri in VisualBasic](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Tipi non consentiti e i membri in mscorlib. dll](disallowed-types-and-members-in-mscorlib-dll.md)   
 [Tipi non consentiti e i membri in System. dll](disallowed-types-and-members-in-system-dll.md)   
 [Tipi e membri non consentiti in System.Core.dll](disallowed-types-and-members-in-system-core-dll.md)  
  
  