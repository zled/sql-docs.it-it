---
title: Creazione di una libreria di estensioni di recapito | Documenti Microsoft
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
- delivery extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 63b32f93-4bab-4b07-bd72-39a47aca1cda
caps.latest.revision: 36
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b893c0702a2a84c1bb354e9bc7859a05e8312ce4
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="creating-a-delivery-extension-library"></a>Creazione di una libreria di estensioni per il recapito
  A ogni estensione per il recapito di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] creata deve essere assegnato uno spazio dei nomi univoco e ogni estensione deve essere inclusa in una libreria o in un file di assembly. Il nome esatto dello spazio dei nomi non è importante, ma è necessario che sia univoco e non condiviso con altre estensioni. È necessario creare spazi dei nomi univoci personalizzati per le estensioni per il recapito della società.  
  
 Nell'esempio seguente viene illustrato il codice per iniziare a creare un'estensione per il recapito di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] che utilizza gli spazi dei nomi contenenti le interfacce per il recapito e le classi di utilità.  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 Quando si compila un'estensione per il recapito di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], è necessario fornire al compilatore un riferimento a Microsoft.ReportingServices.Interfaces.dll, in quanto le classi e le interfacce dell'estensione per il recapito sono incluse in tale elemento. Lo spazio dei nomi <xref:Microsoft.ReportingServices.Interfaces> è necessario per implementare l'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IExtension>, l'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> e altro ancora. Ad esempio, se tutti i file che contiene il codice per implementare un [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] sono stati scritto in c# estensione per il recapito in una singola directory con estensione cs, verrebbe inviato il comando seguente dalla directory per compilare i file archiviati in CompanyName.ExtensionName.dll.  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 Esempio di codice seguente viene illustrato il comando che verrebbe utilizzato per [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] i file con estensione. vb.  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  È inoltre possibile progettare, sviluppare e compilare un'estensione per il recapito utilizzando [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Per ulteriori informazioni sullo sviluppo di assembly in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vedere la documentazione di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementazione di un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
