---
title: I messaggi di errore, Driver ODBC di Visual FoxPro | Documenti Microsoft
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
- error messages [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], error messages
- SQLSTATE [ODBC]
- FoxPro ODBC driver [ODBC], error messages
ms.assetid: 58ea9734-4edf-44da-ba80-938aa7b340e4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e561aab3359acb1f236aea38e76da33289e630ef
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="error-messages-visual-foxpro-odbc-driver"></a>Messaggi di errore (Driver ODBC di Visual FoxPro)
Quando si verifica un errore, il driver di Visual FoxPro restituisce le informazioni seguenti:  
  
-   Il numero di errore nativo e il testo del messaggio di errore  
  
-   Il valore SQLSTATE (un codice di errore ODBC) e testo messaggio di errore  
  
 Accedere a queste informazioni di errore chiamando [SQLError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md).  
  
## <a name="native-errors"></a>Errori nativi  
 Per gli errori che si verificano nell'origine dati, il driver di Visual FoxPro restituisce il numero di errore nativo e il testo del messaggio di errore. Per un elenco di numeri di errore nativo, vedere [Visual FoxPro ODBC Driver Native messaggi di errore](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md).  
  
## <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (codici di errore ODBC)  
 Per gli errori che vengono rilevati e restituiti dal driver Visual FoxPro, il driver esegue il mapping il numero di errore nativo restituito al codice SQLSTATE appropriato. Se un numero di errore nativo non dispone di un codice di errore ODBC per eseguire il mapping, il driver di Visual FoxPro restituisce SQLSTATE S1000 (errore generale).  
  
 Per un elenco di valori SQLSTATE generati dal Driver ODBC di Visual FoxPro per errori di Visual FoxPro corrispondenti, vedere [codici di errore ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).  
  
## <a name="syntax"></a>Sintassi  
 Messaggi di errore presentano il formato seguente:  
  
 **[** *fornitore* **] [** *ODBC_component* **]** *error_message*  
  
 I prefissi tra parentesi quadre ([]) identificano l'origine dell'errore, come definito nella tabella seguente.  
  
|Origine dati|Prefisso|Valore|  
|-----------------|------------|-----------|  
|Gestione driver|[fornitore]<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[Gestione Driver ODBC]<br />N/D|  
|Driver Visual FoxPro|fornitore]<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[Driver ODBC Visual FoxPro]<br />N/D|  
  
 Ad esempio, se il Driver ODBC di Visual FoxPro non è riuscito a trovare il file Employee. dbf, potrebbe restituire il messaggio di errore seguente:  
  
 "[*Microsoft*] [*Driver ODBC Visual FoxPro*] File 'Employee. dbf' non esiste"
