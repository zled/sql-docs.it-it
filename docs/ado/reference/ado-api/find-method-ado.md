---
title: Find (metodo) (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Find
- Recordset15::Find
helpviewer_keywords:
- Find method [ADO]
ms.assetid: 55c9810a-d8ca-46c2-a9dc-80e7ee7aa188
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d1e46954ec7a0983927b1d375615fe6e6cbf10ee
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="find-method-ado"></a>Find (metodo) (ADO)
Cerca un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) per la riga che soddisfa i criteri specificati. Facoltativamente, la direzione della ricerca, la riga iniziale e offset dalla riga iniziale può essere specificata. Se vengono soddisfatti i criteri, la posizione della riga corrente è impostata su record trovato. in caso contrario, la posizione viene impostata per la fine o inizio del **Recordset**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Find (Criteria, SkipRows, SearchDirection, Start)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Criteri*  
 Oggetto **stringa** valore contenente un'istruzione che specifica il nome della colonna, l'operatore di confronto e valore da utilizzare nella ricerca.  
  
 *SkipRows*  
 Parametro facoltativo*.* Oggetto **lungo** valore, il cui valore predefinito è zero, che specifica l'offset di riga dalla riga corrente o *avviare* segnalibro per iniziare la ricerca. Per impostazione predefinita, verrà avviata la ricerca nella riga corrente.  
  
 *SearchDirection*  
 Parametro facoltativo*.* Oggetto [SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md) valore che specifica se la ricerca deve iniziare sulla riga corrente o la successiva riga disponibile nella direzione della ricerca. Arresta una ricerca alla fine del **Recordset** se il valore è **adSearchForward**. Arresta una ricerca all'inizio del **Recordset** se il valore è **adSearchBackward**.  
  
 *Start*  
 Facoltativa. Oggetto **Variant** segnalibro che funziona come la posizione iniziale per la ricerca.  
  
## <a name="remarks"></a>Osservazioni  
 Può essere specificato solo un nome di colonna singola *criteri*. Questo metodo non supporta le ricerche a più colonne.  
  
 L'operatore di confronto in *criteri* potrebbe essere "**>**"(maggiore di),"**\<**" (minore di), "=" (uguale), "> =" (maggiore o uguale a), "< =" (minore o uguale a), "<>" (non uguale), o "like" (criteri di ricerca).  
  
 Il valore in *criteri* può essere una stringa, un numero a virgola mobile o una data. I valori stringa sono delimitati da virgolette singole o virgolette "#" (simbolo di cancelletto) (ad esempio, "stato = 'WA'" o "stato = WA # #"). I valori di data vengono delimitati da virgolette "#" (simbolo di cancelletto) (ad esempio, "start_date > # #7/22/97"). Questi valori possono contenere ore, minuti e secondi per indicare i timestamp, ma non devono contenere millisecondi o si verificheranno errori.  
  
 Se l'operatore di confronto è "mi piace", il valore di stringa può contenere un asterisco (*) per trovare una o più occorrenze di qualsiasi carattere o una sottostringa. Ad esempio, "stato come sto\*'" corrisponde a Milano e Massachusetts. È anche possibile utilizzare asterischi iniziali e finali per trovare una sottostringa contenuta all'interno dei valori. Ad esempio, "stato ad esempio '\*come\*'" corrisponde Alaska, Arkansas e Massachusetts.  
  
 Asterischi possono essere utilizzati solo alla fine di una stringa di criteri o all'inizio e fine di una stringa di criteri, come illustrato in precedenza. È possibile usare l'asterisco come carattere jolly iniziale ('* str'), o come un carattere jolly incorporati di s\*r'). Ciò genererà un errore.  
  
> [!NOTE]
>  Si verifica un errore se non è una posizione di riga corrente prima di chiamare **trovare**. Qualsiasi metodo che imposta la posizione di riga, ad esempio [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), deve essere chiamato prima di chiamare **trovare**.  
  
> [!NOTE]
>  Se si chiama il **trovare** metodo su un oggetto recordset e la posizione corrente del recordset all'ultimo record o alla fine del file (EOF), non sarà possibile trovare alcun elemento. È necessario chiamare il **MoveFirst** per impostare il cursore/posizione corrente all'inizio del recordset.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio del metodo Find (VB)](../../../ado/reference/ado-api/find-method-example-vb.md)   
 [Proprietà index](../../../ado/reference/ado-api/index-property.md)   
 [Ottimizzare la proprietà dinamica (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)   
 [Metodo Seek](../../../ado/reference/ado-api/seek-method.md)
