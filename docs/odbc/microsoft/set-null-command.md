---
title: Comando NULL SET | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- set nullSET NULL
ms.assetid: 410c5a6e-e957-4ecc-9e2d-e591cbc0bc4f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 14cade223de7014dd4a0c27295d3ff742d18af17
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="set-null-command"></a>Comando NULL SET
Determina come valori null sono supportati da SQL ALTER TABLE - SQL, CREATE TABLE - e INSERT - comandi SQL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>Argomenti  
 ON  
 (Impostazione predefinita per il driver; il valore predefinito di Visual FoxPro è impostata su OFF). Specifica che tutte le colonne in una tabella creata con l'istruzione ALTER TABLE e CREATE TABLE consentirà valori null. È possibile eseguire l'override di supporto di valori null per le colonne nella tabella includendo la clausola NOT NULL nelle definizioni delle colonne.  
  
 Specifica inoltre che INSERT - SQL verrà inserire valori null in tutte le colonne non incluse nell'istruzione INSERT - clausola VALUE SQL. INSERT - SQL inserirà valori null solo in colonne che ammettono valori null.  
  
 OFF  
 Specifica che tutte le colonne in una tabella creata con l'istruzione ALTER TABLE e CREATE TABLE non consente valori null. È possibile designare il supporto di valori null per le colonne nell'istruzione ALTER TABLE e CREATE TABLE, includendo la clausola NULL nelle definizioni delle colonne.  
  
 Specifica inoltre che INSERT - SQL verrà inserire valori vuoti in tutte le colonne non incluse nell'istruzione INSERT - clausola VALUE SQL.  
  
## <a name="remarks"></a>Osservazioni  
 SET NULL influisce solo come valori sono supportati da INSERT - SQL ALTER TABLE e CREATE TABLE. Altri comandi sono influenzati SET NULL.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE - comando SQL](../../odbc/microsoft/alter-table-sql-command.md)   
 [Crea tabella - comando SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT - comando SQL](../../odbc/microsoft/insert-sql-command.md)
