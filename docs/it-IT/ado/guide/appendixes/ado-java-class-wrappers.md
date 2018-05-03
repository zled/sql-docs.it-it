---
title: Wrapper di classe Java ADO | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d1ac9d3421aac0847782766bfc30d15f045abc9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ado-java-class-wrappers"></a>Wrapper di classe Java ADO
Questo codice dichiara un'istanza di ADO [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) wrapper della classe e la inizializza, tutte nella stessa riga di codice. Inoltre, vengono dichiarate le variabili per ognuno degli argomenti nel [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) (metodo), in particolare per [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) e [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) (perché non supporta il linguaggio enumerato tipi). Apre e chiude il **Recordset** oggetto. L'impostazione di gruppi di risultati 1 su NULL semplicemente pianifica tale variabile deve essere rilasciato quando Java esegue il relativo rilascio sistematico e intermittente di oggetti inutilizzati.  
  
```  
public static void main( String args[])  
{  
   msado15._Recordset   Rs1 = new msado15.Recordset();  
   Variant Source     = new Variant( "SELECT * FROM Authors" );  
   Variant Connect    = new Variant( "DSN=AdoDemo;UID=admin;PWD=;" );  
   int     LockType   = msado15.CursorTypeEnum.adOpenForwardOnly;  
   int     CursorType = msado15.LockTypeEnum.adLockReadOnly;  
   int     Options    = -1;  
  
   Rs1.Open( Source, Connect, LockType,  CursorType, Options );  
   Rs1.Close();  
   Rs1 = null;  
  
   System.out.println( "Success!\n" );  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Microsoft SDK per Java](../../../ado/guide/appendixes/using-the-microsoft-sdk-for-java.md)
