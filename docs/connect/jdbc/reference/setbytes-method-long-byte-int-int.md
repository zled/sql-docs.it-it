---
title: setBytes (long, byte, int, int) (metodo) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerBlob.setBytes (long.byte[], int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7def226c-b211-459e-8c1a-08592d75d4a4
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5aa6587a6877143486aa5b053311694229f10a36
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setbytes-method-long-byte-int-int"></a>setBytes (long, byte, int, int) (metodo)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Scrive tutta o parte della matrice di byte specificata nell'oggetto BLOB a partire dalla posizione, dall'offset e dalla lunghezza specificati; quindi restituisce il numero di byte scritti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int setBytes(long pos,  
                    byte[] bytes,  
                    int offset,  
                    int len)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 Posizione (in base 1) nell'oggetto BLOB in corrispondenza della quale iniziare la scrittura dei dati.  
  
 *byte*  
  
 Matrice di byte da scrivere nell'oggetto BLOB.  
  
 *offset*  
  
 L'offset in byte della matrice in cui iniziare la lettura dei dati dal **byte** matrice.  
  
 *Len*  
  
 Numero di byte di cui tentare la lettura dalla matrice di byte nell'oggetto BLOB.  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** contenente il numero di byte scritti.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setBytes viene specificato dal metodo setBytes nell'interfaccia Java.SQL. BLOB.  
  
 I dati vengono sovrascritti a partire dalla posizione specificata e possono superare la lunghezza iniziale dell'oggetto BLOB. Se si specifica un valore posizione+1, verranno aggiunti byte. Se si passa un valore posizione+2 o superiore (o zero o inferiore) verrà generato un errore di posizione. Il passaggio di lunghezza zero **byte** matrice restituirà zero perché è stato scritto alcun byte.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setBytes &#40; SQLServerBlob &#41;](../../../connect/jdbc/reference/setbytes-method-sqlserverblob.md)   
 [Metodi di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Membri di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Classe SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
