---
title: "Proprietà CacheSize (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::CacheSize
helpviewer_keywords:
- CacheSize property [ADO]
ms.assetid: 49dc9a49-af7b-433b-be36-7a14ca984fb7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 29d5a36905a4de936dcac630adf97688d2b40855
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="cachesize-property-ado"></a>Proprietà CacheSize (ADO)
Indica il numero di record da un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetti memorizzati nella cache in locale.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **lungo** valore che deve essere maggiore di 0. Valore predefinito è 1.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **CacheSize** proprietà per controllare il numero di record da recuperare contemporaneamente nella memoria locale dal provider. Ad esempio, se il **CacheSize** è 10, dopo avere aperto prima il **Recordset** dell'oggetto, il provider recupera i primi 10 record nella memoria locale. Quando si sposta attraverso i **Recordset** dell'oggetto, il provider restituisce i dati dal buffer di memoria locale. Non appena si sposta dopo l'ultimo record nella cache, il provider recupera i successivi 10 record dall'origine dati nella cache.  
  
> [!NOTE]
>  **CacheSize** si basa sul **numero massimo di righe aperto** proprietà specifiche del provider (nel **proprietà** insieme del **Recordset** oggetto). Non è possibile impostare **CacheSize** su un valore maggiore di **numero massimo di righe aperto**. Per modificare il numero di righe che può essere aperta dal provider, impostare **numero massimo di righe aperto**.  
  
 Il valore di **CacheSize** può essere modificata durante il ciclo di vita del **Recordset** oggetto, ma se si modifica questo valore interessa solo il numero di record nella cache dopo recuperi successivi dall'origine dati. La modifica solo il valore della proprietà non modificherà il contenuto corrente della cache.  
  
 Se sono presenti record di un numero inferiore rispetto al recupero **CacheSize** specifica, il provider restituisce i record rimanenti e si verifica alcun errore.  
  
 Oggetto **CacheSize** impostazione pari a zero non è consentito e viene restituito un errore.  
  
 I record recuperati dalla cache non riflettono le modifiche simultanee da altri utenti ai dati di origine. Per forzare un aggiornamento di tutti i dati memorizzati nella cache, utilizzare il [Resync](../../../ado/reference/ado-api/resync-method.md) metodo.  
  
 Se **CacheSize** è impostata su un valore maggiore di uno, i metodi di navigazione ([spostare](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst, MoveLast, MoveNext e MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) potrebbe causare il passaggio a un eliminare i record, se l'eliminazione si verifica dopo che sono stati recuperati i record. Dopo l'operazione di recupero iniziale, le successive operazioni di eliminazione non si rifletteranno nella cache di dati fino a quando non si tenta di accedere a un valore di dati da una riga eliminata. Tuttavia, l'impostazione **CacheSize** a uno Elimina questo problema, poiché non è possibile recuperare le righe eliminate.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà CacheSize (VB)](../../../ado/reference/ado-api/cachesize-property-example-vb.md)   
 [Esempio di proprietà CacheSize (VC + +)](../../../ado/reference/ado-api/cachesize-property-example-vc.md)   
 [Esempio di proprietà CacheSize (JScript)](../../../ado/reference/ado-api/cachesize-property-example-jscript.md)

