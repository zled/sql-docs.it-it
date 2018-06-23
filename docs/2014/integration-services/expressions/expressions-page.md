---
title: Pagina Espressioni | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a266929860877c960c656033c41715154b6e2736
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156248"
---
# <a name="expressions-page"></a>Pagina Espressioni
  Usare la pagina **Espressioni** per modificare le espressioni di proprietà e accedere alle finestre di dialogo **Editor espressioni di proprietà** e **Property Expression Builder** (Generatore di espressioni di proprietà).  
  
 Le espressioni di proprietà aggiornano i valori delle proprietà durante l'esecuzione del pacchetto. È possibile utilizzare queste espressioni con le proprietà di pacchetti, attività, contenitori, gestioni connessioni e alcuni componenti del flusso di dati. Le espressioni vengono valutate e i risultati vengono utilizzati in sostituzione dei valori che sono stati impostati per le proprietà alla configurazione del pacchetto e dei relativi oggetti. Nelle espressioni possono essere presenti variabili e le funzioni e gli operatori forniti dal linguaggio delle espressioni. È possibile, ad esempio, generare la riga Oggetto di un'attività Invia messaggi concatenando il valore di una variabile contenente la stringa "Previsioni del tempo per:" e i risultati restituiti dalla funzione GETDATE() per ottenere la stringa "Previsioni del tempo per: 4/5/2006".  
  
 Per altre informazioni sulla scrittura di espressioni e sull'utilizzo di espressioni di proprietà, vedere [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) e [Utilizzo delle espressioni di proprietà nei pacchetti](use-property-expressions-in-packages.md).  
  
## <a name="options"></a>Opzioni  
 **Espressioni (...)**  
 Fare clic sui puntini di sospensione per aprire la finestra di dialogo **Editor espressioni di proprietà** . Per altre informazioni, vedere [Editor espressioni di proprietà](property-expressions-editor.md).  
  
 **\<property name>**  
 Fare clic sui puntini di sospensione per aprire la finestra di dialogo **Generatore di espressioni** . Per altre informazioni, vedere [Generatore di espressioni](expression-builder.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi di integrazione &#40;SSIS&#41; variabili](../integration-services-ssis-variables.md)   
 [Variabili di sistema](../system-variables.md)   
 [Espressioni di Integration Services &#40;SSIS&#41;](integration-services-ssis-expressions.md)  
  
  