---
title: Oggetto Error | Documenti Microsoft
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
- Error
helpviewer_keywords:
- error object [ADO]
ms.assetid: a175d453-fa55-4f49-9ede-a26d83177919
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 71609e69fa31adcaf1f336d9529ea8bd5fa62434
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="error-object"></a>Oggetto Error
Contiene informazioni sugli errori di accesso ai dati relativi a una singola operazione che include il provider.  
  
## <a name="remarks"></a>Osservazioni  
 Qualsiasi operazione relativa agli oggetti ADO può generare una o più errori del provider. Quando si verifica ogni errore, uno o più **errore** gli oggetti vengono inseriti nel [errori](../../../ado/reference/ado-api/errors-collection-ado.md) insieme del [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto. Quando un'altra operazione ADO genera un errore, il **errori** insieme è deselezionata e il nuovo set di **errore** oggetti viene inserito nella **errori** insieme.  
  
> [!NOTE]
>  Ogni **errore** oggetto rappresenta un errore del provider specifico, non un errore di ADO. Gli errori ADO vengono esposti al meccanismo di gestione delle eccezioni in fase di esecuzione. Ad esempio, in Microsoft Visual Basic, l'occorrenza di un errore specifico ADO verrà generato un **in caso di errore** eventi e vengono visualizzate nel **errore** oggetto. Per un elenco completo degli errori ADO, vedere il [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) argomento.  
  
 È possibile leggere un **errore** proprietà dell'oggetto per ottenere informazioni dettagliate su ogni errore, inclusi i seguenti:  
  
-   Il [descrizione](../../../ado/reference/ado-api/description-property.md) proprietà, che contiene il testo dell'errore. Questa è la proprietà predefinita.  
  
-   Il [numero](../../../ado/reference/ado-api/number-property-ado.md) proprietà che contiene il **lungo** valore intero della costante di errore.  
  
-   Il [origine](../../../ado/reference/ado-api/source-property-ado-error.md) proprietà, che identifica l'oggetto che ha generato l'errore. Questo è particolarmente utile quando si dispone più **errore** gli oggetti di **errori** insieme a seguito di una richiesta a un'origine dati.  
  
-   Il [SQLState](../../../ado/reference/ado-api/sqlstate-property.md) e [NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md) le proprietà che forniscono informazioni dalle origini dati SQL.  
  
 Quando si verifica un errore del provider, viene inserito nella **errori** insieme il **connessione** oggetto. ADO supporta la restituzione di più errori da una singola operazione di ADO per la gestione delle informazioni di errore specifico del provider. Per ottenere questa informazioni complete sugli errori in un gestore degli errori, utilizzare le funzionalità di intercettazione degli errori appropriate della lingua o l'ambiente in uso, quindi utilizzare cicli annidati di enumerare le proprietà di ogni **errore** oggetto di **Errori** insieme.  
  
> [!NOTE]
>  **Microsoft Visual Basic e gli utenti di VBScript** se non è non valida **connessione** dell'oggetto, sarà necessario recuperare le informazioni sull'errore dal **errore** oggetto.  
  
 Provider come tale, ADO Cancella il **OLE Error Info** dell'oggetto prima di effettuare una chiamata che potrebbe potenzialmente generare un nuovo errore del provider. Tuttavia, il **errori** insieme nel **connessione** oggetto viene deselezionato e viene popolato solo quando il provider genera un errore di nuovo, o quando il [deselezionare](../../../ado/reference/ado-api/clear-method-ado.md) metodo viene chiamato.  
  
 Alcune proprietà e metodi restituiscono avvisi che vengono visualizzati come **errore** gli oggetti di **errori** raccolta ma non arrestano l'esecuzione del programma. Prima di chiamare il [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), o [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) metodi su un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto; il [aprire](../../../ado/reference/ado-api/open-method-ado-connection.md) metodo su un **connessione** ; dell'oggetto o impostare il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà in un **Recordset** dell'oggetto, chiamare il **deselezionare**metodo il **errori** insieme. In questo modo, è possibile leggere il [conteggio](../../../ado/reference/ado-api/count-property-ado.md) proprietà del **errori** raccolta da testare per avvisi restituiti.  
  
 Il **errore** oggetto non è sicuro per lo scripting.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto Error](../../../ado/reference/ado-api/error-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà SQLState (VB), HelpContext, HelpFile, NativeError, numero, origine e descrizione](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Esempio di proprietà SQLState (VC + +), HelpContext, HelpFile, NativeError, numero, origine e descrizione](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Raccolta di errori (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Appendice A: Provider](../../../ado/guide/appendixes/appendix-a-providers.md)
