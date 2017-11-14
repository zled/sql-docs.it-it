---
title: Metodo di aggiornamento | Documenti Microsoft
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
- Recordset15::Update
helpviewer_keywords:
- Update method [ADO]
ms.assetid: 6b2a9c31-1a7e-40db-8a53-30720d0f6cc1
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 287fb5bf8b87a8371ee84d89ba4e5efee6b3587f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="update-method"></a>Update (metodo)
Salva le modifiche apportate alla riga corrente di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto, o [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta di un [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.Update Fields, Values  
record.Fields.Update  
```  
  
#### <a name="parameters"></a>Parametri  
 *Campi*  
 Facoltativa. Oggetto **Variant** che rappresenta un singolo nome o un **Variant** matrice che rappresenta i nomi o posizione ordinale del campo o campi che si desidera modificare.  
  
 *Valori*  
 Facoltativa. Oggetto **Variant** che rappresenta un singolo valore o un **Variant** matrice che rappresenta i valori per i campi nel nuovo record.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="recordset"></a>recordset  
 Utilizzare il **aggiornamento** per salvare le modifiche apportate al record corrente di un **Recordset** oggetto dopo la chiamata di [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) (metodo) o dopo la modifica dei valori di campo in un record esistente. Il **Recordset** oggetto deve supportare gli aggiornamenti.  
  
 Per impostare i valori di campo, effettuare una delle operazioni seguenti:  
  
-   Assegnare valori a un [campo](../../../ado/reference/ado-api/field-object.md) dell'oggetto [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà e chiamare il **aggiornamento** metodo.  
  
-   Passare come argomenti con un nome di campo e un valore di **aggiornamento** chiamare.  
  
-   Passare una matrice di nomi di campo e una matrice di valori con il **aggiornamento** chiamare.  
  
 Quando si utilizzano matrici di campi e valori, è necessario un numero uguale di elementi in entrambe le matrici. Inoltre, l'ordine dei nomi di campo deve corrispondere all'ordine dei valori dei campi. Se il numero e ordine dei campi e valori non corrispondono, si verifica un errore.  
  
 Se il **Recordset** oggetto supporta l'aggiornamento in batch, è possibile memorizzare nella cache più modifiche a uno o più record localmente finché non si chiama il [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) metodo. Se si modifica il record corrente o aggiungendo un nuovo record quando si chiama il **UpdateBatch** (metodo), ADO chiamerà automaticamente il **aggiornamento** per salvare le modifiche in sospeso per il record corrente prima di trasmettere le modifiche in blocco al provider.  
  
 Se si sposta dal record si aggiunge o modifica prima di chiamare il **aggiornamento** metodo, verrà automaticamente chiamato **aggiornamento** per salvare le modifiche. È necessario chiamare il [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) metodo se si desidera annullare le modifiche apportate al record corrente oppure eliminare il record appena aggiunto.  
  
 Il record corrente rimane invariato dopo la chiamata di **aggiornamento** metodo.  
  
## <a name="record"></a>Record  
 Il **aggiornamento** metodo completa aggiunte, eliminazioni e aggiornamenti ai campi di [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta di un **Record** oggetto.  
  
 Ad esempio, i campi eliminati con la **eliminare** metodo sono contrassegnati per l'eliminazione immediatamente ma rimangono nella raccolta. Il **aggiornamento** metodo deve essere chiamato per eliminare effettivamente questi campi dalla raccolta del provider.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Raccolta di campi (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodi CancelUpdate (VB) e di aggiornamento](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Esempio di metodi CancelUpdate (VC + +) e di aggiornamento](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [AddNew (metodo) (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Metodo CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Proprietà EditMode](../../../ado/reference/ado-api/editmode-property.md)   
 [Metodo UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)

