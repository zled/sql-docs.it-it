---
title: Pacchetti installati nelle librerie utente | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99ffd9b8-aa6d-4ac2-9840-4e66d0463978
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b4d5c7f3d1d0da5e1967140fcbdfcf60ba4571e7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="packages-installed-in-user-libraries"></a>Pacchetti installati nelle librerie utente

Se un utente necessita di un nuovo pacchetto R e non è un amministratore, i pacchetti non potranno essere installati nel percorso predefinito e saranno pertanto installati per impostazione predefinita in una libreria utente privata. 

In un ambiente di sviluppo R tipico, per fare riferimento al pacchetto nel codice, l'utente dovrebbe aggiungere il percorso alla variabile di ambiente R `libPath` o fare riferimento al percorso completo del pacchetto, come nell'esempio seguente:  
  
~~~~
library("c:/Users/<username>/R/win-library/packagename")  
~~~~

## <a name="problems-with-packages-in-user-libraries"></a>Problemi con i pacchetti nelle librerie utente

Tuttavia, in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] questa soluzione alternativa **non** è supportata; i pacchetti devono essere installati nella libreria predefinita. Se il pacchetto non è installato nella libreria predefinita, potrebbe essere visualizzato un errore analogo al seguente quando si tenta di chiamare il pacchetto:

*Errore nella libreria (xxx): nessun pacchetto denominato "xxx"*
 

Pertanto, quando si esegue la migrazione di soluzioni R per l'esecuzione in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], è importante eseguire le operazioni seguenti:
+ Installare tutti i pacchetti necessari per la libreria predefinita.
+ Modificare il codice per garantire che i pacchetti vengano caricati dalla libreria predefinita, anziché da librerie utente o directory ad hoc.
+ Controllare il codice per assicurarsi che non ci siano chiamate a pacchetti non installati.
+ Modificare qualsiasi codice che tenti di installare pacchetti in modo dinamico.
 
Se un pacchetto è installato nella libreria predefinita, il runtime R lo caricherà dalla libreria predefinita, anche se viene specificata un'altra libreria nel codice R.

## <a name="see-also"></a>Vedere anche
