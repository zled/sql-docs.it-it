---
title: Recupero di dati Long | Documenti Microsoft
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
- long data [ODBC]
- fetches [ODBC], long data
- result sets [ODBC], fetching
- SQLGetData function [ODBC], getting long data
- retrieving long data [ODBC]
ms.assetid: 6ccb44bc-8695-4bad-91af-363ef22bdb85
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0ea30c211e3cfd66acf1588ef9ca2a45fd1037d1
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getting-long-data"></a>Recupero di dati Long
Definiscono DBMS *dati long* come qualsiasi carattere o dati binari in una determinata dimensione, ad esempio i 255 caratteri. Tali dati possono essere sufficientemente ridotto da archiviare in un unico buffer, ad esempio una descrizione di parte di diverse migliaia di caratteri. Tuttavia, potrebbe essere troppo lungo per archiviare in memoria, ad esempio documenti di testo lungo o bitmap. Poiché tali dati non possono essere archiviati in un unico buffer, viene recuperato dal driver in parti con **SQLGetData** dopo gli altri dati nella riga sono stati recuperati.  
  
> [!NOTE]  
>  Un'applicazione può recuperare qualsiasi tipo di dati con **SQLGetData**, long non solo i dati, anche se solo i caratteri e i dati binari possono essere recuperati in parti. Tuttavia, se i dati sono sufficientemente piccoli da rientrare in un unico buffer, non è in genere utilizzare **SQLGetData**. È molto più semplice associare un buffer per la colonna e consentire il driver di restituire i dati nel buffer.  
  
 Per recuperare dati long da una colonna, un'applicazione chiama innanzitutto **SQLFetchScroll** o **SQLFetch** per spostare una riga e recuperare i dati per le colonne associate. L'applicazione chiama quindi **SQLGetData**. **SQLGetData** ha gli stessi argomenti **SQLBindCol**: un handle di istruzione; un numero di colonna; il C byte, l'indirizzo e tipo lunghezza dei dati di una variabile di applicazione e l'indirizzo di un buffer di lunghezza/indicatore. Entrambe le funzioni hanno gli stessi argomenti poiché eseguono essenzialmente la stessa attività: descrivono una variabile di applicazione per il driver e specificare che devono essere restituiti i dati per una determinata colonna in tale variabile. Le principali differenze sono che **SQLGetData** viene chiamato dopo che viene recuperata una riga (e talvolta come *ad associazione tardiva* per questo motivo) e che l'associazione specificata da **SQLGetData ** dura solo per la durata della chiamata.  
  
 Per quanto riguarda una singola colonna, **SQLGetData** si comporta come **SQLFetch**: recupera i dati per la colonna, lo converte il tipo della variabile di applicazione e restituisce tale variabile. Restituisce anche la lunghezza in byte dei dati nel buffer di lunghezza/indicatore. Per ulteriori informazioni su come **SQLFetch** restituisce dati, vedere [il recupero di una riga di dati](../../../odbc/reference/develop-app/fetching-a-row-of-data.md).  
  
 **SQLGetData** è diverso da **SQLFetch** per un aspetto importante. Se viene chiamato più volte in successione per la stessa colonna, ogni chiamata restituisce una parte successiva dei dati. Ogni chiamata tranne l'ultima chiamata restituisce SQL_SUCCESS_WITH_INFO e SQLSTATE 01004 (dati String, destra troncati); l'ultima chiamata restituisce SQL_SUCCESS. Si tratta come **SQLGetData** viene utilizzato per recuperare dati long in parti. Quando non sono presenti ulteriori dati da restituire, **SQLGetData** restituisce SQL_NO_DATA. L'applicazione è responsabile della combinazione di dati long, che potrebbe indicare la concatenazione di parti dei dati. Ogni parte è con terminazione null; l'applicazione è necessario rimuovere il carattere di terminazione null se le parti di concatenazione. Il recupero dei dati in parti può essere eseguita per segnalibri a lunghezza variabile anche per altri dati di tipo long. Il valore restituito in diminuisce il buffer di lunghezza/indicatore in ogni chiamata per il numero di byte restituiti nella chiamata precedente, anche se è comune per il driver a non essere in grado di individuare la quantità di dati disponibili e restituire una lunghezza in byte del SQL_NO_TOTAL. Esempio:  
  
```  
// Declare a binary buffer to retrieve 5000 bytes of data at a time.  
SQLCHAR       BinaryPtr[5000];  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd, BinaryLenOrInd, NumBytes;  
SQLRETURN     rc;   
SQLHSTMT      hstmt;  
  
// Create a result set containing the ID and picture of each part.  
SQLExecDirect(hstmt, "SELECT PartID, Picture FROM Pictures", SQL_NTS);  
  
// Bind PartID to the PartID column.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, &PartID, 0, &PartIDInd);  
  
// Retrieve and display each row of data.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   // Display the part ID and initialize the picture.  
   DisplayID(PartID, PartIDInd);  
   InitPicture();  
  
   // Retrieve the picture data in parts. Send each part and the number   
   // of bytes in each part to a function that displays it. The number   
   // of bytes is always 5000 if there were more than 5000 bytes   
   // available to return (cbBinaryBuffer > 5000). Code to check if   
   // rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
   while ((rc = SQLGetData(hstmt, 2, SQL_C_BINARY, BinaryPtr, sizeof(BinaryPtr),  
                           &BinaryLenOrInd)) != SQL_NO_DATA) {  
      NumBytes = (BinaryLenOrInd > 5000) || (BinaryLenOrInd == SQL_NO_TOTAL) ?  
                  5000 : BinaryLenOrInd;  
      DisplayNextPictPart(BinaryPtr, NumBytes);  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```  
  
 Esistono diverse restrizioni sull'utilizzo di **SQLGetData**. In genere, accedere alle colonne con **SQLGetData**:  
  
-   Deve essere accessibile in ordine crescente di numero di colonna (a causa del modo con che le colonne di un set di risultati vengono letti dall'origine dati). Ad esempio, è possibile chiamare **SQLGetData** per colonna 5 e lo chiama per la colonna 4.  
  
-   Non può essere associata.  
  
-   Deve avere un numero di colonne superiore rispetto l'ultima colonna associata. Ad esempio, se l'ultima colonna associata colonna 3, è consentito chiamare **SQLGetData** per la colonna 2. Per questo motivo, le applicazioni devono assicurarsi di inserire le colonne di dati long alla fine dell'elenco di selezione.  
  
-   Non può essere utilizzato se **SQLFetch** o **SQLFetchScroll** è stata chiamata per recuperare più righe. Per ulteriori informazioni, vedere [cursori a blocchi usando](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Alcuni driver non applicano queste restrizioni. Applicazioni interoperative devono supporre esiste o determinare le restrizioni non vengono applicate chiamando **SQLGetInfo** con l'opzione SQL_GETDATA_EXTENSIONS.  
  
 Se l'applicazione non necessita di tutti i dati in un carattere o una colonna di dati binari, è possibile ridurre il traffico di rete di driver basati su DBMS impostando l'attributo di istruzione SQL_ATTR_MAX_LENGTH prima di eseguire l'istruzione. Il che limita il numero di byte di dati che verranno restituiti per qualsiasi colonna di tipo binario o carattere. Si supponga, ad esempio, che una colonna contiene documenti di testo lungo. Un'applicazione che esamina la tabella contenente questa colonna potrebbe essere necessario visualizzare solo la prima pagina di ogni documento. Anche se questo attributo dell'istruzione può essere simulato nel driver, non è necessario eseguire questa operazione. In particolare, se un'applicazione desidera troncare i dati carattere o binario, deve essere associato un buffer di piccole dimensioni e la colonna con **SQLBindCol** e lasciare che il driver di troncare i dati.
