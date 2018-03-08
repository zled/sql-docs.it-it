---
title: Gestione degli errori nell'API di TOM (Analysis Services AMO-TOM) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ec44daa0-a90e-42ad-b70d-6a7a7a4e4b7b
caps.latest.revision: "4"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fe73f11bb44968e7091fe522f4905e3640c95282
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="handling-errors-in-the-tom-api-analysis-services-amo-tom"></a>Gestione degli errori nell'API di TOM (Analysis Services AMO-TOM)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Una pratica comune per le librerie gestite come modello di oggetto tabulare Analysis Services Management Objects (AMO) (TOM) consiste nell'utilizzare eccezioni come un meccanismo per la segnalazione di condizioni di errore all'utente.  

Quando viene rilevato un errore in AMO TOM, oltre alla generazione alcune eccezioni .NET standard come **ArgumentException** e **InvalidOperationException**, TOM può anche generare varie eccezioni specifiche TOM.  

TOM eccezioni sono derivate da [classe AmoException](http://msdn.microsoft.com/library/microsoft.analysisservices.amoexception.aspx), relativi a entrambe le eccezioni specifiche TOM e AMO. 

Per illustrare in TOM di gestione delle eccezioni, è opportuno esaminare una delle eccezioni più comuni, ovvero [OperationException classe](http://msdn.microsoft.com/library/microsoft.analysisservices.operationexception.aspx).

**OperationException** viene generata quando un utente avvia un'operazione nel server di Analysis Services e il server non riesce a eseguire un'operazione, perché l'azione non valido o a causa di un altro errore interno o esterno. 

Quando viene generata, * * OperationException * * oggetto conterrà un elenco di errori XMLA restituiti dal server. 

Si noti che il server non accetterà le modifiche che non sono validi. In questo caso, ripristinare il **modello** struttura ad albero nell'ultimo stato noto soddisfacente utilizzando il [UndoLocalChanges metodo](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.model.undolocalchanges.aspx), correggere il modello, quindi inviare di nuovo. 

## <a name="code-example-handle-exceptions"></a>Esempio di codice: la gestione delle eccezioni 
 
```
 try 
 { 
  // Change the Model, for example create a table. 
  // … 
   model.saveChanges(); 
 } 
  catch(operationException ex) 
 { 
  foreach(XmlaError err in ex.Results.OfType<XmlaError>().cast<XmlaError>()) 
  { 
   Console.WriteLine(“Error returned from the server:” + err.Messsage ); 
  } 
 } 
```

## <a name="next-steps"></a>Passaggi successivi

Altre eccezioni rilevanti, tra cui:

- [Classe TomInternalException](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.tominternalexception.aspx)
- [Classe TomValidationException](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.tomvalidationexception.aspx)
- [Classe JsonSerializationException](http://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_JsonSerializationException.htm)
