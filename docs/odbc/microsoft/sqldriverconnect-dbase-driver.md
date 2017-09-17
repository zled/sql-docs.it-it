---
title: SQLDriverConnect (dBASE Driver) | Documenti Microsoft
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
- DBase driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], dBASE Driver
ms.assetid: c837aa31-068e-4fa3-bc00-aae09bec21de
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e8548e95e4b7c0e34ba71f73698174d5c25b1c4b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqldriverconnect-dbase-driver"></a>SQLDriverConnect (dBASE Driver)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver dBASE. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** consente di connettersi a un driver senza creare un'origine dati (DSN).  
  
 Le parole chiave seguenti sono supportate nella stringa di connessione per tutti i driver: **DSN**, **DBQ**, e **FIL**.  
  
 Quando viene utilizzato il driver Paradox, dopo aver aperto un file protetto da password da un utente, altri utenti non sono consentiti per aprire il file stesso.  
  
 Nella tabella seguente mostra le parole chiave minime necessarie per connettersi a tutti i driver e viene fornito un esempio di coppie parola chiave/valore utilizzate con **SQLDriverConnect**. Per un elenco completo dei valori DRIVERID, vedere [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).  
  
> [!NOTE]  
>  Se DBQ o DefaultDir non è specificato per il dBASEdriver, il driver si connetterà alla directory corrente.  
  
|Driver|Parole chiave necessari|Esempi|  
|------------|-----------------------|--------------|  
|file dBASE|Driver, DriverID|Driver = {Microsoft dBASE Driver (*. dbf)}; DBQ = c:\temp; DriverID = 277|
