---
title: Metodo GetRows (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::GetRows
- Recordset15::raw_GetRows
helpviewer_keywords:
- Getrows method [ADO]
ms.assetid: 14b92860-4171-47d9-a413-dd60dd6a8880
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1c76e506432e4aeeaae552ea67803bf4723c85fa
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getrows-method-ado"></a>Metodo GetRows (ADO)
Recupera i record multipli di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto in una matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array = recordset.GetRows(Rows, Start, Fields )  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **Variant** il cui valore è una matrice bidimensionale.  
  
#### <a name="parameters"></a>Parametri  
 *Righe*  
 Facoltativa. Oggetto [GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md) valore che indica il numero di record da recuperare. Il valore predefinito è **adGetRowsRest**.  
  
 *Inizio*  
 Facoltativa. Oggetto **stringa** valore o **Variant** che restituisce il segnalibro per il record da cui il **GetRows** deve iniziare l'operazione. È inoltre possibile utilizzare un [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md) valore.  
  
 *Campi*  
 Facoltativa. Oggetto **Variant** che rappresenta un nome di campo singolo o posizione ordinale o una matrice di nomi di campo o i numeri di posizione ordinale. ADO restituisce solo i dati in questi campi.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **GetRows** metodo per copiare i record da un **Recordset** in una matrice bidimensionale. Il primo indice identifica il campo e il secondo il numero di record. Il *matrice* variabile viene ridimensionata automaticamente per il corretto ridimensionamento quando il **GetRows** metodo restituisce i dati.  
  
 Se non si specifica un valore per il *righe* argomento, la **GetRows** che consente di recuperare automaticamente tutti i record di **Recordset** oggetto. Se vengono richiesti più record di quelli disponibili, **GetRows** restituisce solo il numero di record disponibili.  
  
 Se il **Recordset** oggetto supporta i segnalibri, è possibile specificare quali record di **GetRows** metodo deve iniziare il recupero dei dati passando il valore di tale record [segnalibro](../../../ado/reference/ado-api/bookmark-property-ado.md)proprietà il *avviare* argomento.  
  
 Se si desidera limitare i campi che il **GetRows** chiamata restituisce, è possibile passare un nome di campo singolo/numero o una matrice di nomi di campo i numeri nel *campi* argomento.  
  
 Dopo aver chiamato **GetRows**, il record successivo da leggere diventa il record corrente, o [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) è impostata su **True** se non sono presenti più record.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo GetRows (VB)](../../../ado/reference/ado-api/getrows-method-example-vb.md)   
 [Esempio di metodo GetRows (VC + +)](../../../ado/reference/ado-api/getrows-method-example-vc.md)   

