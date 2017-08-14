---
title: Utilizzo di assembly personalizzati con nome sicuro | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: cf8ee5462bd75ab82ea4296a5b71136cb2eb9ee9
ms.contentlocale: it-it
ms.lasthandoff: 08/12/2017

---
# <a name="using-strong-named-custom-assemblies"></a>Utilizzo di assembly personalizzati con nome sicuro
  Un nome sicuro identifica un assembly e include il nome di testo dell'assembly, il numero di versione in quattro parti, informazioni sulle impostazioni cultura (se disponibili), una chiave pubblica e una firma digitale archiviata nel manifesto dell'assembly. Un nome sicuro identifica in modo univoco un assembly in CLR (Common Language Runtime) e assicura l'integrità binaria.  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a>Utilizzo di AllowPartiallyTrustedCallersAttribute  
 Per utilizzare assembly con nome sicuro con i report, è necessario consentire l'assembly con nome sicuro di essere chiamato da codice parzialmente attendibile utilizzando l'assembly **AllowPartiallyTrustedCallers** attributo. È possibile utilizzare **AllowPartiallyTrustedCallersAttribute** per consentire assembly con nome sicuro di essere chiamato da Progettazione Report o il server di report nelle espressioni del report. Per consentire al codice parzialmente attendibile di chiamare gli assembly con nome sicuro, aggiungere l'attributo a livello di assembly seguente al file di attributo dell'assembly.  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 **AllowPartiallyTrustedCallersAttribute** è efficace solo quando si applica a un assembly con nome sicuro a livello di assembly. Per ulteriori informazioni sull'applicazione di attributi a livello di assembly, vedere "Applicazione di attributi" nel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] documentazione SDK.  
  
> [!CAUTION]  
>  Quando **AllowPartiallyTrustedCallersAttribute** è presente, il valore predefinito **FullTrustLinkDemand** controlli di sicurezza, rendendo possibile chiamare da qualsiasi altro assembly parzialmente attendibile di assembly. Tutti i controlli di sicurezza, inclusi gli attributi di sicurezza dichiarativi a livello di classe o di metodo, devono essere dichiarati in modo esplicito.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di assembly personalizzati con i report](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
