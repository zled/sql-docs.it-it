---
title: Riferimento agli assembly in un file RDL| Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: custom-assemblies
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 4b40e251558b622d4b301b3cae3148b963eda9ee
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33014708"
---
# <a name="referencing-assemblies-in-an-rdl-file"></a>Impostazione di un riferimento agli assembly in un file RDL
  Per supportare l'uso di assembly di codice personalizzati nei file di definizione report, nella specifica RDL (Report Definition Language) sono inclusi due elementi RDL, ovvero l'elemento **CodeModules** e l'elemento **Classes**.  
  
 L'elemento **CodeModules** consente di fare riferimento agli assembly di codice gestito nelle espressioni di report. **CodeModules** è un elemento di livello principale che contiene il riferimento all'assembly usato nei file di definizione report per chiamare funzioni specializzate. Una voce in una definizione del report che supporta l'utilizzo di un assembly personalizzato può essere simile alla seguente:  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 Anziché chiamare <xref:System.Reflection.Assembly.Load%2A> dal codice personalizzato, registrare gli assembly personalizzati aggiungendo manualmente elementi **CodeModule** al file RDL o usando la scheda **Riferimenti** della finestra di dialogo **Proprietà report**. Per altre informazioni, vedere [Riferimenti a codice personalizzato e ad assembly in espressioni in Progettazione report &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)sottostante.  
  
 L'elemento **Classes** supporta l'uso di membri di istanza in una definizione del report. **Classes** è un elemento di livello principale che contiene un riferimento al nome della classe e un nome dell'istanza. Una voce in una definizione del report che supporta l'utilizzo di membri dell'istanza può essere simile alla seguente:  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 Per altre informazioni, vedere [Accesso agli assembly personalizzati tramite espressioni](../../reporting-services/custom-assemblies/accessing-custom-assemblies-through-expressions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di assembly personalizzati con i report](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
