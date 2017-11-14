---
title: Metodo CompareBookmarks (ADO) | Documenti Microsoft
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
- CompareBookmarks
- Recordset20::CompareBookmarks
- Recordset20::raw_CompareBookmarks
helpviewer_keywords:
- CompareBookmarks method [ADO]
ms.assetid: d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f1e19f4800505e3ed481455bc349d65855c6b538
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="comparebookmarks-method-ado"></a>Metodo CompareBookmarks (ADO)
Confronta due segnalibri e restituisce un'indicazione dei relativi valori.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = recordset.CompareBookmarks(Bookmark1, Bookmark2)  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un [CompareEnum](../../../ado/reference/ado-api/compareenum.md) valore che indica la posizione di riga relativo di due record rappresentati dai relativi segnalibri.  
  
#### <a name="parameters"></a>Parametri  
 *Bookmark1*  
 Il segnalibro della prima riga.  
  
 *Bookmark2*  
 Il segnalibro della seconda riga.  
  
## <a name="remarks"></a>Osservazioni  
 I segnalibri devono applicare allo stesso [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto, o un **Recordset** oggetto e il relativo [clone](../../../ado/reference/ado-api/clone-method-ado.md). Non è possibile confrontare in modo affidabile segnalibri da diversi **Recordset** oggetti, anche se sono stati creati dall'origine o comando stesso. Né è possibile confrontare i segnalibri per una **Recordset** oggetto il cui provider sottostante non supporta i confronti.  
  
 Un segnalibro che identifica in modo univoco una riga in un **Recordset** oggetto. Utilizzare il [segnalibro](../../../ado/reference/ado-api/bookmark-property-ado.md) proprietà della riga corrente per ottenere il segnalibro.  
  
 Poiché il tipo di dati di un segnalibro è specifico di ogni provider, ADO espone come un **Variant**. Ad esempio, i segnalibri di SQL Server sono di tipo DBTYPE_R8 (**doppie**). ADO consente di esporre questo tipo come un **Variant** con un sottotipo di **Double**.  
  
 Quando si confrontano i segnalibri, ADO non tenta di qualsiasi tipo di coercizione. I valori vengono semplicemente passati al provider in cui si verifica il confronto. Se i segnalibri passato per il **CompareBookmarks** metodo sono archiviate in variabili di tipi diversi, è possibile generare il seguente errore di mancata corrispondenza di tipo: "argomenti sono di tipo errato, sono comprese nell'intervallo accettabile o sono in conflitto con l'altro."  
  
 Un segnalibro a cui non è valido o non corretto verrà generato un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo CompareBookmarks (VB)](../../../ado/reference/ado-api/comparebookmarks-method-example-vb.md)   
 [Esempio di metodo CompareBookmarks (VC + +)](../../../ado/reference/ado-api/comparebookmarks-method-example-vc.md)   
 [Proprietà Bookmark (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md)

