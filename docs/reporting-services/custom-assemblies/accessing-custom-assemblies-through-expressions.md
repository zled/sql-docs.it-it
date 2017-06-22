---
title: Accesso agli assembly personalizzati tramite espressioni | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
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
- expressions [Reporting Services], custom assemblies
- static member calls
- instance member calls [Reporting Services]
- calling class members
- custom assemblies [Reporting Services], expressions
ms.assetid: 917c4d47-1a95-4f54-98b1-e8cb2165d90f
caps.latest.revision: 32
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 70ff488827e5289d401bf62b67a82a08ecc25f70
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="accessing-custom-assemblies-through-expressions"></a>Accesso agli assembly personalizzati tramite espressioni
  Dopo aver creato un assembly personalizzato, averlo reso disponibile in Progettazione report o nel server di report, aver aggiunto i criteri di sicurezza appropriati e aver aggiunto un riferimento all'assembly personalizzato nella definizione del report, è possibile accedere ai membri delle classi nell'assembly utilizzando le espressioni di report. Per fare riferimento al codice personalizzato in un'espressione, è necessario chiamare il membro di una classe nell'assembly. La modalità di esecuzione di tale operazione dipende dal tipo di metodo, ovvero statico o basato su istanze.  
  
## <a name="calling-static-members-from-a-report-definition-file"></a>Chiamata a membri statici da un file di definizione del report  
 I membri statici appartengono alla classe o al tipo e non a un oggetto per il quale è stata creata un'istanza. È possibile accedere a questi membri chiamandoli direttamente dalla classe. È consigliabile utilizzare i membri statici per chiamare le funzioni personalizzate in un report ogni qualvolta è possibile, perché i membri statici offrono prestazioni migliori. Per chiamare un membro statico, è necessario farvi riferimento come un'espressione che assume il formato =*Spaziodeinomi*.  
  
#### <a name="to-call-static-members"></a>Per chiamare i membri statici  
  
-   Per chiamare un membro statico, impostare l'espressione in modo che corrisponda al nome completo del membro che include lo spazio dei nomi, il nome della classe e il nome del membro. L'esempio seguente chiama il **ToGBP** metodo, che converte il **StandardCost** campo valore da dollari a sterline e lo visualizza in un report:  
  
    ```  
    =CurrencyConversion.DollarCurrencyConversion.ToGBP(Fields!StandardCost.Value)  
    ```  
  
### <a name="important-information-regarding-static-fields-and-properties"></a>Informazioni importanti relative alle proprietà e ai campi statici  
 Attualmente, tutti i report vengono eseguiti nello stesso dominio dell'applicazione. Questo significa che i report con dati statici specifici dell'utente espongono questi dati alle altre istanze dello stesso report. In questo modo, i dati statici di un utente possono essere resi disponibili per tutti gli utenti che attualmente eseguono un report specifico. Per questo motivo, è consigliabile non utilizzare proprietà in assembly personalizzati o in o campi statici di **codice** elemento; utilizzare invece proprietà o campi di istanza nei report. I metodi statici possono comunque essere utilizzati, perché non comportano l'archiviazione dello stato o dei dati.  
  
## <a name="calling-instance-members-from-a-report-definition-file"></a>Chiamata a membri di istanza da un file di definizione del report  
 Se l'assembly personalizzato contiene membri di istanza a cui è necessario accedere in una definizione del report, è necessario aggiungere al report un nome di istanza per la classe. È possibile aggiungere un nome di istanza per una classe utilizzando il **codice** scheda della finestra di **proprietà Report** finestra di dialogo. Per ulteriori informazioni sull'aggiunta di istanze di classi a un report, vedere [codice personalizzato e riferimenti ad Assembly in espressioni in Progettazione Report &#40; SSRS &#41; ](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 Per chiamare un membro statico, è necessario farvi riferimento come un'espressione che assume il formato = Code*. NomeIstanza*.  
  
#### <a name="to-call-instance-members"></a>Per chiamare i membri dell'istanza  
  
-   Per chiamare un membro di istanza di un assembly personalizzato, è necessario fare riferimento il **codice** (parola chiave) seguito dal nome dell'istanza e il metodo. Nell'esempio seguente chiama un metodo di istanza **ToEUR** che consente di convertire il **StandardCost** campo valore da dollari a euro e lo visualizza in un report:  
  
    ```  
    =Code.m_myDollarCoversion.ToEUR(Fields!StandardCost.Value)  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di assembly personalizzati con i report](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
