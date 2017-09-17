---
title: SQLDriverConnect (Driver per Excel) | Documenti Microsoft
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
- Excel driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Excel Driver
ms.assetid: 285cb1ea-f461-4596-97f2-fc57af05dede
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: eca660cf2c38539dbf4a0fa560bfc67a1b1be115
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (Driver per Excel)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver Excel. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** consente di connettersi a un driver senza creare un'origine dati (DSN).  
  
 Le parole chiave seguenti sono supportate nella stringa di connessione per tutti i driver: **DSN**, **DBQ**, e **FIL**.  
  
 Nella tabella seguente mostra le parole chiave minime necessarie per connettersi a tutti i driver e viene fornito un esempio di coppie parola chiave/valore utilizzate con **SQLDriverConnect**. Per un elenco completo dei valori DRIVERID, vedere [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).  
  
> [!NOTE]  
>  Se DBQ o DefaultDir per Microsoft Excel 3.0 o 4.0 driver non è specificato, il driver si connetterà alla directory corrente.  
  
|Driver|Parole chiave necessari|Esempi|  
|------------|-----------------------|--------------|  
|Microsoft Excel versione 3.0 o 4.0|Driver, DriverID|Driver = {Driver Microsoft Excel (xls)}; DBQ = c:\temp; DriverID = 278|  
|Microsoft Excel 5.0/7.0|Driver, DriverID, DBQ|Driver = {Driver Microsoft Excel (xls)}; DBQ=c:\Temp\sample.xls; DriverID = 22|  
|Microsoft Excel 97 e versioni successive|Driver, DriverID, DBQ|Driver = {Driver Microsoft Excel (xls)}; DBQ=c:\Temp\sample.xls; DriverID = 790|
