---
title: Oggetto Parameter | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameter
helpviewer_keywords:
- Parameter object [ADO]
ms.assetid: e010e794-7f0f-4026-8b5b-37328e437d63
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb2eda53603a06ed73dce0962bea4ca18035714f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280710"
---
# <a name="parameter-object"></a>Oggetto Parameter
Rappresenta un parametro o un argomento associato a un [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto basato su una query con parametri o stored procedure.  
  
## <a name="remarks"></a>Remarks  
 Molti provider supportano i comandi con parametri. Questi sono i comandi in cui l'azione desiderata è definita una sola volta, ma le variabili (o parametri) vengono usati per modificare alcuni dettagli del comando. Un'istruzione SQL SELECT, ad esempio, utilizzare un parametro per definire i criteri di corrispondenza di una clausola WHERE e un altro per definire il nome di colonna per una clausola di ordinamento.  
  
 **Parametro** oggetti rappresentano i parametri associati alle query con parametri o gli argomenti in/out e i valori restituiti di stored procedure. A seconda della funzionalità del provider, alcuni insiemi, metodi o proprietà di un **parametro** oggetto potrebbe non essere disponibile.  
  
 Con le raccolte, i metodi e proprietà di un **parametro** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Impostare o restituire il nome di un parametro con il [nome](../../../ado/reference/ado-api/name-property-ado.md) proprietà.  
  
-   Impostare o restituire il valore di un parametro con il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà. **Valore** è la proprietà predefinita di **parametro** oggetto.  
  
-   Impostare o restituire le caratteristiche del parametro con il [attributi](../../../ado/reference/ado-api/attributes-property-ado.md), [direzione](../../../ado/reference/ado-api/direction-property.md), [precisione](../../../ado/reference/ado-api/precision-property-ado.md), [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md), [ Dimensioni](../../../ado/reference/ado-api/size-property-ado-parameter.md), e [tipo](../../../ado/reference/ado-api/type-property-ado.md) proprietà.  
  
-   Passare dati long binari o character a un parametro con il [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) metodo.  
  
-   Attributi specifici del provider di accesso tramite il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme.  
  
 Se si conoscono i nomi e le proprietà dei parametri associati con la stored procedure o query con parametri a cui si desidera chiamare, è possibile utilizzare il [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) metodo per creare **parametro** oggetti con le impostazioni di proprietà appropriato e l'utilizzo di [Append](../../../ado/reference/ado-api/append-method-ado.md) metodo per aggiungerli al [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) insieme. Consente di impostare e restituire i valori dei parametri senza necessità di chiamare il [aggiornamento](../../../ado/reference/ado-api/refresh-method-ado.md) metodo il **parametri** raccolta per recuperare le informazioni sui parametri dal provider, un potenzialmente operazione utilizza molte risorse.  
  
 Il **parametro** oggetto non è sicuro per lo scripting.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Le proprietà dell'oggetto parametro, metodi ed eventi](../../../ado/reference/ado-api/parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Metodo CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Raccolta di parametri (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
