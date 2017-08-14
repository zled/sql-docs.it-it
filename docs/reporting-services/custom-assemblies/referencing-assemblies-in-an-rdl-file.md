---
title: Riferimento ad assembly in un File RDL | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
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
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 9fd80c818f13972434b72a72ce306e2f494cf56f
ms.contentlocale: it-it
ms.lasthandoff: 08/12/2017

---
# <a name="referencing-assemblies-in-an-rdl-file"></a>Impostazione di un riferimento agli assembly in un file RDL
  Per supportare l'uso degli assembly di codice personalizzato nel file di definizione del report, i due elementi di linguaggio RDL (Report Definition) sono inclusi nella specifica RDL: il **CodeModules** elemento e **classi** elemento.  
  
 Il **CodeModules** elemento consente di fare riferimento agli assembly di codice gestito nelle espressioni del report. **CodeModules** è un elemento di primo livello che contiene il riferimento all'assembly da utilizzare nel file di definizione del report per chiamare funzioni specializzate. Una voce in una definizione del report che supporta l'utilizzo di un assembly personalizzato può essere simile alla seguente:  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 Anziché chiamare <xref:System.Reflection.Assembly.Load%2A> dal codice personalizzato, registrare gli assembly personalizzati aggiungendo manualmente **CodeModule** elementi nel file RDL o utilizzando il **riferimenti** scheda della finestra di **proprietà Report** finestra di dialogo. Per altre informazioni, vedere [Riferimenti a codice personalizzato e ad assembly in espressioni in Progettazione report &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 Il **classi** elemento supporta l'utilizzo di membri di istanza in una definizione del report. **Classi** è un elemento di primo livello che contiene un riferimento al nome della classe e un nome di istanza. Una voce in una definizione del report che supporta l'utilizzo di membri dell'istanza può essere simile alla seguente:  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 Per ulteriori informazioni, vedere [l'accesso a Custom Assemblies Through Expressions](../../reporting-services/custom-assemblies/accessing-custom-assemblies-through-expressions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di assembly personalizzati con i report](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
