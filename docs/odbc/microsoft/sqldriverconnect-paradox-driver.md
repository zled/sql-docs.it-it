---
title: SQLDriverConnect (Driver Paradox) | Documenti Microsoft
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
- SQLDriverConnect function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLDriverConnect
ms.assetid: c2ba486e-5e01-4e67-adb1-68511f5f0206
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f9265657327f71e41c124707ab66c8ad621bda55
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (Paradox Driver)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver Paradox. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** consente di connettersi a un driver senza creare un'origine dati (DSN).  
  
 Le parole chiave seguenti sono supportate nella stringa di connessione per tutti i driver: **DSN**, **DBQ**, e **FIL**.  
  
 Il **PWD** supportata anche la parola chiave. La parola chiave PWD non deve includere i caratteri speciali (vedere SQL_SPECIAL_CHARACTERS in **SQLGetInfo** restituiti valori).  
  
 Dopo aver aperto un file protetto da password da un utente, non è consentiti ad altri utenti apre lo stesso file.  
  
 Nella tabella seguente mostra le parole chiave minime necessarie per connettersi a tutti i driver e viene fornito un esempio di coppie parola chiave/valore utilizzate con **SQLDriverConnect**. Per un elenco completo dei valori DRIVERID, vedere [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).  
  
> [!NOTE]  
>  Se DBQ o DefaultDir non specificato per il driver Paradox, il driver si connetterà alla directory corrente.  
  
|Driver|Parole chiave necessari|Esempio|  
|------------|-----------------------|-------------|  
|Paradox|Driver, DriverID|Driver = {Microsoft Paradox Driver (*. DB)}; DBQ = c:\temp; DriverID = 26|

