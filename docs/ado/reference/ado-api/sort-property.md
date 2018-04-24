---
title: Proprietà Sort | Documenti Microsoft
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
- Recordset15::get_Sort
- Recordset15::put_Sort
- Recordset15::PutSort
- Recordset15::GetSort
- Recordset15::Sort
helpviewer_keywords:
- DESC [ADO]
- ASC [ADO]
- Sort property [ADO]
ms.assetid: 3683ffa0-6f93-4906-9533-ef6942f24f39
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5a6f1652861f7b057105a198b36ab7bb0e4d98eb
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="sort-property"></a>Proprietà di ordinamento
Indica uno o più nomi di campo in cui il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) è ordinato, e se ogni campo viene ordinato in ordine crescente o decrescente.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **stringa** i nomi di valore che indica il campo nel **Recordset** di ordinamento. Ogni nome è separato da una virgola e, facoltativamente, è seguito da uno spazio vuoto e la parola chiave, **ASC**, che consente di ordinare il campo in ordine crescente o **DESC**, che consente di ordinare il campo in ordine decrescente. Per impostazione predefinita, se è specificata alcuna parola chiave, il campo viene ordinato in ordine crescente.  
  
## <a name="remarks"></a>Osservazioni  
 Questa proprietà richiede la [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà da impostare **adUseClient**. Verrà creato un indice temporaneo per ogni campo specificato nella **ordinamento** proprietà se non ne esiste già.  
  
 L'operazione di ordinamento è efficiente poiché i dati non è fisicamente ordinati, ma semplicemente avviene nell'ordine specificato dall'indice.  
  
 Quando il valore della **ordinamento** proprietà è diverso da una stringa vuota, il **ordinamento** ordine della proprietà ha la precedenza sull'ordine specificato in un **ORDER BY** clausola incluse nell'istruzione SQL utilizzata per aprire la **Recordset**.  
  
 Il **Recordset** non devono essere aperte prima di accedere il **ordinamento** proprietà; può essere impostato in qualsiasi momento dopo il **Recordset** viene creata un'istanza di oggetto.  
  
 L'impostazione di **ordinamento** proprietà in una stringa vuota verrà reimpostato le righe in base all'ordine originale e verranno eliminati gli indici temporanei. Gli indici esistenti non verranno eliminati.  
  
 Si supponga che un **Recordset** contiene tre campi denominati *firstName*, *middleInitial*, e *lastName*. Impostare il **ordinamento** proprietà alla stringa di "`lastName DESC, firstName ASC`", che verranno ordinate il **Recordset** in base al cognome in ordine decrescente, quindi in base al nome in ordine crescente. Il secondo nome viene ignorato.  
  
 Non può essere nome campo "ASC" o "DESC" poiché tali nomi siano in conflitto con le parole chiave **ASC** e **DESC**. È possibile creare un alias per un campo con un nome in conflitto con il **AS** (parola chiave) nella query che restituisce il **Recordset**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Sort (VB)](../../../ado/reference/ado-api/sort-property-example-vb.md)   
 [Esempio di proprietà Sort (VC + +)](../../../ado/reference/ado-api/sort-property-example-vc.md)   
 [Ottimizzare la proprietà dinamica (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)   
 [Proprietà SortColumn (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [Proprietà SortDirection (Servizi Desktop remoto)](../../../ado/reference/rds-api/sortdirection-property-rds.md)
