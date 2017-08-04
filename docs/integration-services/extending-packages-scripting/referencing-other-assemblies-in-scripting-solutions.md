---
title: Riferimento ad altri assembly nelle soluzioni di Scripting | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, .NET Framework
- Script task [Integration Services], adding references
- referencing custom assemblies
- SSIS Script task, VisualBasic namespace
- assemblies [Integration Services]
- VisualBasic namespace
- Script task [Integration Services], VisualBasic namespace
- Microsoft.VisualBasic namespace
- Script task [Integration Services], .NET Framework
- .NET Framework [Integration Services]
- referencing Web services
ms.assetid: 9b655bcd-19f6-43d8-9f89-1b4d299c6380
caps.latest.revision: 68
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3deb13c7e3aeb2e974ac6e6582555a617346a298
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="referencing-other-assemblies-in-scripting-solutions"></a>Riferimenti ad altri assembly nelle soluzioni di scripting
  Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] libreria di classi fornisce allo sviluppatore di script con un set di potenti strumenti per l'implementazione di funzionalità personalizzate in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pacchetti. L'attività Script e il componente script possono anche utilizzare assembly gestiti personalizzati.  
  
> [!NOTE]  
>  Per consentire ai pacchetti di utilizzare gli oggetti e metodi da un servizio Web, utilizzare il **Aggiungi riferimento Web** comando disponibile in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA). Nelle versioni precedenti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è necessario generare una classe proxy per utilizzare un servizio Web.  
  
## <a name="using-a-managed-assembly"></a>Utilizzo di un assembly gestito  
 Per [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per trovare un assembly gestito in fase di progettazione, è necessario eseguire i passaggi seguenti:  
  
1.  Archiviare l'assembly gestito in qualsiasi cartella del computer.  
  
    > [!NOTE]  
    >  Nelle versioni precedenti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è possibile aggiungere solo un riferimento a un assembly gestito archiviato nella cartella %windir%\Microsoft.NET\Framework\vx.x.xxxxx o nella cartella %Programmi%\Microsoft SQL Server\100\SDK\Assemblies.  
  
2.  Aggiungere un riferimento all'assembly gestito.  
  
     Per aggiungere il riferimento, in VSTA nel **Aggiungi riferimento** della finestra di dialogo di **Sfoglia** individuare e aggiungere l'assembly gestito.  
  
 Affinché [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] trovi l'assembly gestito in fase di esecuzione, è necessario effettuare i passaggi seguenti:  
  
1.  Firmare l'assembly gestito con un nome sicuro.  
  
2.  Installare l'assembly nella Global Assembly Cache nel computer in cui viene eseguito il pacchetto.  
  
     Per ulteriori informazioni, vedere [compilazione, distribuzione e debug di oggetti personalizzati](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).  
  
## <a name="using-the-microsoft-net-framework-class-library"></a>Utilizzo della libreria di classi Microsoft .NET Framework  
 L'attività Script e il componente script possono trarre vantaggio da tutti gli altri oggetti e funzionalità esposti dalla libreria di classi [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Ad esempio, tramite [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] è possibile recuperare informazioni sull'ambiente e interagire con il computer in cui viene eseguito il pacchetto.  
  
 In questo elenco vengono descritte alcune delle classi [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] utilizzate più di frequente:  
  
-   **System. Data** contiene l'architettura ADO.NET.  
  
-   **System.IO** fornisce un'interfaccia per il file system e i flussi.  
  
-   **Forms** fornisce la creazione dei moduli.  
  
-   **System.Text.RegularExpressions** fornisce classi per l'utilizzo di espressioni regolari.  
  
-   **System. Environment** restituisce informazioni sul computer locale, l'utente corrente e le impostazioni utente e computer.  
  
-   **System.Net** fornisce comunicazioni di rete.  
  
-   **System. DirectoryServices** espone Active Directory.  
  
-   **System. Drawing** fornisce librerie Modifica immagine completa.  
  
-   **System. Threading** consente la programmazione multithreading.  
  
 Per ulteriori informazioni su [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], consultare MSDN Library.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di pacchetti tramite Scripting](../../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
  
  
