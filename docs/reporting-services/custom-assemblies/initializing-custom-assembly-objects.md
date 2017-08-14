---
title: Inizializzazione di oggetti Assembly personalizzato | Documenti Microsoft
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
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: ab05efc7baba58a34180faa038cb58c7f57f4af2
ms.contentlocale: it-it
ms.lasthandoff: 08/12/2017

---
# <a name="initializing-custom-assembly-objects"></a>Inizializzazione di oggetti assembly personalizzati
  In alcuni casi, potrebbe essere necessario inizializzare valori di proprietà e campi nelle classi di assembly personalizzate quando si crea un'istanza di tali classi. In genere, è necessario inizializzare le classi personalizzate con i valori disponibili nelle raccolte di oggetti globali del report. A tale scopo, si esegue l'override di **OnInit** metodo il **codice** oggetto di un report. Per accedere a **OnInit**, utilizzare il **codice** elemento della definizione del report. Sono disponibili due tecniche per l'inizializzazione di valori di campo o proprietà delle classi in un assembly personalizzato che si intende utilizzare nel report: È possibile dichiarare e creare una nuova istanza della classe utilizzando **OnInit**, oppure è possibile chiamare un metodo disponibile pubblicamente utilizzando **OnInit**.  
  
## <a name="global-object-collections-and-initialization"></a>Raccolte di oggetti globali e inizializzazione  
 Per l'inizializzazione delle variabili delle classi personalizzate sono disponibili diverse raccolte. È possibile utilizzare il **Globals** e **utente** raccolte. Il **parametri**, **campi** e **ReportItems** le raccolte non sono disponibili nella fase del ciclo di vita del report quando il **OnInit** metodo viene richiamato. Per utilizzare le raccolte condivise, **Globals** o **utente**, è necessario includere il **Report** riferimento all'oggetto. Ad esempio, per inizializzare la classe personalizzata in base alla lingua corrente dell'utente che accede al report, il **codice** elemento potrebbe essere simile al seguente:  
  
```  
<Code>  
   Dim m_myClass As MyClass  
  
   Protected Overrides Sub OnInit()  
      m_myClass = new MyClass(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 Per inizializzare valori di proprietà e campi di una classe come illustrato in precedenza, è possibile dichiarare la classe e creare una nuova istanza chiamando un costruttore sottoposto a override.  
  
 Un altro modo per inizializzare i valori di proprietà e campi delle classi negli assembly personalizzati consiste nel chiamare un metodo disponibile pubblicamente definito dal **OnInit** metodo. È innanzitutto necessario aggiungere un nome di istanza per la classe nel file di definizione del report. Dopo avere aggiunto il nome di istanza e il riferimento all'assembly appropriati, è possibile chiamare il metodo di inizializzazione per inizializzare i valori di proprietà e campi per la classe. Il **OnInit** metodo potrebbe essere simile al seguente:  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 Per ulteriori informazioni sull'aggiunta di un nome di riferimento e l'istanza di assembly per la classe personalizzata, vedere [aggiungere un riferimento all'Assembly per un Report &#40; SSRS &#41; ](../../reporting-services/report-design/add-an-assembly-reference-to-a-report-ssrs.md).  
  
 Per ulteriori informazioni sulle raccolte di oggetti globali, vedere [raccolte predefinite nelle espressioni &#40; Generatore report e SSRS &#41; ](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di assembly personalizzati con i report](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
