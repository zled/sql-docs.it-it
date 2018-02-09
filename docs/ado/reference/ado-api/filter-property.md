---
title: "Proprietà Filter | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- Recordset15::Filter
helpviewer_keywords:
- Filter property
ms.assetid: 80263a7a-5d21-45d1-84fc-34b7a9be4c22
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8e0a74efdc9eeef18eac76e582355653d6677139
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="filter-property"></a>Proprietà filtro
Indica un filtro per i dati in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **Variant** valore, che può contenere uno dei seguenti:  
  
-   **Stringa di criteri** ??? una stringa costituita da uno o più clausole singoli concatenate con **AND** o **OR** operatori.  
  
-   **Matrice di segnalibri** ??? Matrice di segnalibro univoco valori che puntano ai record di **Recordset** oggetto.  
  
-   Oggetto [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) valore.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **filtro** proprietà selettivo i record in un **Recordset** oggetto. Filtrati **Recordset** diventa il cursore corrente. Altre proprietà che restituiscono valori basati sull'oggetto corrente **cursore** interessati, ad esempio [proprietà AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md), [proprietà AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md), [ Proprietà RecordCount (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md), e [proprietà PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md). Questo è l'impostazione di **filtro** proprietà su un valore specifico sposterà il record corrente al primo record che soddisfa il nuovo valore.  
  
 La stringa di criteri è costituita da clausole nel formato *nomecampo-operatore-valore* (ad esempio, `"LastName = 'Smith'"`). È possibile creare clausole composte concatenando clausole singole con **AND** (ad esempio, `"LastName = 'Smith' AND FirstName = 'John'"`) o **OR** (ad esempio, `"LastName = 'Smith' OR LastName = 'Jones'"`). Utilizzare le seguenti linee guida per le stringhe di criteri:  
  
-   *FieldName* deve essere un nome di campo valido di **Recordset**. Se il nome del campo contiene spazi, è necessario racchiudere il nome tra parentesi quadre.  
  
-   Operatore deve essere uno dei seguenti: \<, >, \<=, > =, <>, =, o **come**.  
  
-   Il valore è il valore con cui si confronteranno i valori dei campi (ad esempio, 'Smith', 24/8/&#95;, 12.345 o $50,00). Utilizzare le virgolette singole con le stringhe e i segni di cancelletto (#) con le date. Per i numeri, è possibile utilizzare la notazione scientifica, segni di dollaro e decimali. Se l'operatore è **come**, il valore può utilizzare i caratteri jolly. Sono consentiti solo l'asterisco (*) e i caratteri jolly il simbolo di percentuale (%) e devono essere l'ultimo carattere nella stringa. Valore non può essere null.  
  
> [!NOTE]
>  Per includere le virgolette singole (') nel valore del filtro, utilizzare due virgolette singole per rappresentare uno. Ad esempio, per filtrare in base, la stringa di criteri deve essere "col1 = ' O ' Malley'". Per includere virgolette all'inizio e alla fine del valore del filtro, racchiudere la stringa con segni di cancelletto (#). Ad esempio, per filtrare '1', la stringa di criteri deve essere "col1 = '1' # #".  
  
-   Non vi è alcun precedenza tra e e o. Le clausole possono essere raggruppate all'interno delle parentesi. Tuttavia, non è possibile raggruppare le clausole unite tramite l'operatore OR e quindi aggiungere il gruppo a un'altra clausola con l'operatore AND, simile al seguente:`(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'`  
  
-   In alternativa, è possibile creare il filtro seguente:`(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')`  
  
-   In un **come** clausola, è possibile utilizzare un carattere jolly all'inizio e alla fine del criterio (ad esempio, LastName Like ' * mit\*'), o solo alla fine del criterio (ad esempio, LastName Like ' Smit\*').  
  
 Le costanti del filtro rendono più semplice risolvere i singoli record conflitti durante la modalità di aggiornamento batch in quanto consente di visualizzare, ad esempio, solo i record che sono stati interessati durante l'ultima [metodo UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) chiamata al metodo.  
  
 Impostazione della proprietà Filter stessa potrebbe non riuscire a causa di un conflitto con i dati sottostanti (ad esempio, un record è già stato eliminato da un altro utente). In tal caso, il provider restituisce avvisi per il [la raccolta di errori (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md) raccolta ma non interrompe l'esecuzione del programma. Errore di run-time si verifica solo se sono presenti conflitti in tutti i record richiesti. Utilizzare il [proprietà Status (Recordset ADO)](../../../ado/reference/ado-api/status-property-ado-recordset.md) proprietà per individuare i record con conflitti.  
  
 L'impostazione di **filtro** proprietà in una stringa di lunghezza zero ("") ha lo stesso effetto dell'utilizzo di **adFilterNone** costante.  
  
 Ogni volta che il **filtro** è impostata, la posizione corrente si sposta al primo record nel subset filtrato di record di **Recordset**. Analogamente, quando il **filtro** proprietà è deselezionata, la posizione del record corrente viene spostato al primo record nel **Recordset**.  
  
 Quando un **Recordset** è filtrato in base a un campo di tipo variant (ad esempio, sql_variant), un errore (DISP_E_TYPEMISMATCH o 80020005) determinerà se i sottotipi dei valori di campo e filtro utilizzati nella stringa di criteri non corrispondono. Ad esempio, se un **Recordset** oggetto (rs) contiene una colonna (C) di tipo sql_variant e un campo di questa colonna è stato assegnato un valore pari a 1 del tipo I4, impostando la stringa di criteri di Reporting Services. Filtro = "C = 'A'" il campo verrà generato l'errore in fase di esecuzione. Tuttavia, Reporting Services. Filtro = "C = 2" applicato sullo stesso campo non produrrà un errore anche se il campo verrà possibile escludere dai set di record corrente.  
  
 Vedere il [proprietà segnalibro (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md) proprietà per una spiegazione dei valori di segnalibro da cui è possibile compilare una matrice da utilizzare con la proprietà di filtro.  
  
 Filtra solo in forma di stringhe di criteri (ad esempio DataOrdine > ' 12/31/1999 ') influiscono sul contenuto di un persistente **Recordset**. I filtri creati con una matrice di segnalibri o utilizzando un valore FilterGroupEnum non influirà il contenuto di persistente **Recordset**. Queste regole si applicano a Recordset creati con cursori sul lato client o sul lato server.  
  
> [!NOTE]
>  Quando si applica il contrassegno adFilterPendingRecords a un filtrato e modificato **Recordset** in modalità di aggiornamento batch, i risultanti **Recordset** è vuoto se il filtro è basato sul campo chiave di un chiave singola tabella e la modifica apportata ai valori del campo chiave. I risultanti **Recordset** sarà non vuoto se viene soddisfatta una delle operazioni seguenti:  
  
-   Il filtro è basato sui campi non chiave in una tabella di chiave singola.  
  
-   Il filtro è basato su tutti i campi in una tabella con più chiavi.  
  
-   Sono state apportate modifiche nei campi non chiave in una tabella di chiave singola.  
  
-   Sono state apportate modifiche in tutti i campi in una tabella con più chiavi.  
  
 Nella tabella seguente sono riepilogati gli effetti di **adFilterPendingRecords** in diverse combinazioni di filtri e le modifiche. La colonna a sinistra mostra le possibili modifiche; è possibile apportare modifiche in uno qualsiasi dei campi non chiave, nel campo chiave in una tabella di chiave singola o in uno qualsiasi dei campi chiave in una tabella con più chiavi. La riga superiore viene illustrato il criterio di filtro; filtro può essere basato su uno dei campi non chiave, il campo chiave in una tabella di chiave singola, o uno dei campi chiavi in una tabella con più chiavi. Le celle che si intersecano mostrano i risultati: il segno + indica che l'applicazione **adFilterPendingRecords** comporterà una non vuota **Recordset**; - significa che un oggetto vuoto **Recordset**.  
  
||Chiavi non|Singola chiave|Più chiavi|  
|-|--------------|----------------|-------------------|  
|**Chiavi non**|+|+|+|  
|**Singola chiave**|+|-|N/D|  
|**Più chiavi**|+|N/D|+|  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà RecordCount (VB) e di filtro](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)   
 [Esempio di proprietà RecordCount (VC + +) e di filtro](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)   
 [Clear (metodo) (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Proprietà dinamica Optimize (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)
