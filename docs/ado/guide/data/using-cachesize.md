---
title: "Utilizzo della proprietà CacheSize | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locks [ADO], CacheSize property
- CacheSize property [ADO]
ms.assetid: ca1c3422-b6a4-4ba6-af55-54f975b698b1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 74ec85c5907485edc5ad8dbcb6c24826fc21ccf3
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-cachesize"></a>Utilizzo della proprietà CacheSize
Utilizzare il **CacheSize** proprietà per controllare il numero di record da recuperare contemporaneamente nella memoria locale dal provider. Ad esempio, se il **CacheSize** è 10, dopo avere aperto prima il **Recordset** dell'oggetto, il provider recupera i primi 10 record nella memoria locale. Quando si sposta attraverso i **Recordset** dell'oggetto, il provider restituisce i dati dal buffer di memoria locale. Non appena si sposta dopo l'ultimo record nella cache, il provider recupera i successivi 10 record dall'origine dati nella cache.  
  
> [!NOTE]
>  **CacheSize** si basa sul **numero massimo di righe aperto** proprietà specifiche del provider (nel **proprietà** insieme del **Recordset** oggetto). Non è possibile impostare **CacheSize** su un valore maggiore di **numero massimo di righe aperto.** Per modificare il numero di righe che può essere aperto dal provider, impostare **numero massimo di righe aperto**.  
  
 Il valore di **CacheSize** può essere modificata durante il ciclo di vita del **Recordset** oggetto, ma se si modifica questo valore interessa solo il numero di record nella cache dopo recuperi successivi dall'origine dati. La modifica solo il valore della proprietà non modificherà il contenuto corrente della cache.  
  
 Se sono presenti record di un numero inferiore rispetto al recupero **CacheSize** specifica, il provider restituisce i record rimanenti e si verifica alcun errore.  
  
 Oggetto **CacheSize** impostazione pari a zero non è consentito e viene restituito un errore.  
  
 Record recuperati dalla cache non riflettono le modifiche simultanee da altri utenti ai dati di origine. Per forzare un aggiornamento di tutti i dati memorizzati nella cache, utilizzare il [Resync](../../../ado/reference/ado-api/resync-method.md) metodo.  
  
 Se **CacheSize** è impostata su un valore maggiore di 1, i metodi di navigazione ([spostare](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst, MoveLast, MoveNext e MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) potrebbe causare il passaggio a un elemento eliminato record, l'eliminazione si verifica dopo che sono stati recuperati i record. Dopo l'operazione di recupero iniziale, le successive operazioni di eliminazione non si rifletteranno nella cache di dati fino a quando non si tenta di accedere a un valore di dati da una riga eliminata. Tuttavia, l'impostazione **CacheSize** a 1 consente di eliminare questo problema perché non è possibile recuperare le righe eliminate.
