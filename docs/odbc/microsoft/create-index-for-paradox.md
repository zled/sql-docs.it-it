---
title: CREARE l'indice per Paradox | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE INDEX [ODBC]
- Paradox driver [ODBC], create index
ms.assetid: 6472bd69-b931-4bc2-a9bf-f1873ed4cdfe
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 058677892aa1a3266b1cd93a5ff015ed0a14bcb9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="create-index-for-paradox"></a>CREARE l'indice per Paradox
La sintassi dell'istruzione CREATE INDEX per il driver ODBC Paradox è:  
  
 **CREARE** [**UNIQUE**] **indice** *nome indice*  
  
 **ON** *-nome della tabella*  
  
 **(** *colonna identificatore* [**ASC**]  
  
 [**,** *colonna identificatore* [**ASC**]...] **)**  
  
 Il driver ODBC Paradox non supporta il **DESC** parola chiave nella grammatica SQL ODBC per l'istruzione CREATE INDEX. Il *-nome della tabella* argomento può specificare il percorso completo della tabella.  
  
 Se la parola chiave **UNIQUE** viene specificato, il driver ODBC Paradox verrà creato un indice univoco. Il primo indice univoco viene creato come indice primario. Si tratta di un file chiave primario Paradox denominato *-nome della tabella*. PX. Indici primari sono soggetti alle restrizioni seguenti:  
  
-   Prima di tutte le righe vengono aggiunte alla tabella, è necessario creare l'indice primario.  
  
-   Un indice primario deve essere definito al momento le prime colonne di "n" in una tabella.  
  
-   Per ogni tabella, è consentito un solo indice primario.  
  
-   Impossibile aggiornare una tabella dal driver Paradox se un indice primario non è definito nella tabella. Si noti che ciò non è possibile per una tabella vuota, che può essere aggiornata anche se non è definito un indice univoco nella tabella.  
  
-   Il *nome indice* argomento per un indice primario deve essere lo stesso nome base della tabella, come richiesto dal Paradox.  
  
 Se la parola chiave **UNIQUE** viene omesso, il driver ODBC Paradox verrà creato un indice non univoco. Si tratta di due file di indice secondario Paradox denominati *-nome della tabella*. X* nn * e *-nome della tabella*. Y*nn*, dove * nn * è il numero della colonna nella tabella. Gli indici non univoci sono soggetti alle restrizioni seguenti:  
  
-   Prima di poter creare un indice non univoco per una tabella, deve esistere un indice primario per la tabella.  
  
-   Per Paradox 3. *x*, *nome indice* argomento per un indice diverso da un indice primario (univoco o non univoco) deve essere identico al nome di colonna. Per Paradox 4. *x* e 5.* x*, il nome di tale indice è possibile, ma non deve essere identico al nome di colonna.  
  
-   Per un indice non univoco, è possibile specificare una sola colonna.  
  
 Impossibile aggiungere colonne di una volta definito un indice in una tabella. Se la prima colonna dell'elenco di argomenti di un'istruzione CREATE TABLE crea un indice, una seconda colonna non può essere inclusa nell'elenco di argomenti.  
  
 Ad esempio, per utilizzare il numero di ordine di vendita e le colonne di numeri di riga dell'indice univoco nella tabella SO_LINES, utilizzare l'istruzione:  
  
```  
CREATE UNIQUE INDEX SO_LINES  
 ON SO_LINES (SONum, LineNum)  
```  
  
 Per utilizzare la colonna dei numeri parte come un indice non univoco nella tabella SO_LINES, utilizzare l'istruzione:  
  
```  
CREATE INDEX PartNum  
 ON SO_LINES (PartNum)  
```  
  
 Si noti che quando vengono eseguite due istruzioni CREATE INDEX, la prima istruzione crea sempre un indice primario con lo stesso nome della tabella e la seconda istruzione crea sempre un indice non univoco con lo stesso nome della colonna. Questi indici verranno denominati in questo modo anche se i nomi diversi vengono immessi nelle istruzioni CREATE INDEX e anche se l'indice è univoco nella seconda istruzione CREATE INDEX.  
  
> [!NOTE]  
>  Quando si usa il driver Paradox senza implementare Borland motore di Database di sola lettura e aggiungere le istruzioni sono consentite.
