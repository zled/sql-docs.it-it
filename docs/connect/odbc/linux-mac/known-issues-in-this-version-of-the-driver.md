---
title: Problemi noti di questa versione del Driver | Documenti Microsoft
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
- known issues
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f4202004a556479779d4884fc42d04ae540ed56d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="known-issues-in-this-version-of-the-driver"></a>Problemi noti in questa versione del driver
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]In questo argomento contiene un elenco di problemi noti relativi a Microsoft ODBC Driver 13 for SQL Server in Linux e macOS.

Altri problemi verranno pubblicati nel [blog del team di Microsoft ODBC Driver](http://blogs.msdn.com/b/sqlnativeclient/).  

- Windows, Linux e macOS convertire caratteri dall'Area uso privato (PUA) o caratteri definiti dall'utente (EUDC) in modo diverso. Le conversioni eseguite sul server all'interno di [!INCLUDE[tsql](../../../includes/tsql_md.md)] utilizzare la libreria di conversione di Windows. Le conversioni del driver di utilizzano le librerie di conversione di Windows, Linux o Mac OS. Ogni libreria può produrre risultati diversi quando si eseguono queste conversioni. Per altre informazioni, vedere l'articolo relativo ai [caratteri definiti dall'utente finale e caratteri Area uso privato](http://msdn.microsoft.com/library/dd317802.aspx).

- Se il client la codifica UTF-8, Gestione driver non sempre esegue correttamente la conversione da UTF-8 a UTF-16. Attualmente, il danneggiamento dei dati verrà eseguita se 1 o più caratteri nella stringa sono caratteri non validi UTF-8. I caratteri ASCII verranno mappati correttamente. Gestione driver tenterà questa conversione quando si chiamano le versioni SQLCHAR dell'API ODBC (ad esempio, SQLDriverConnectA). Gestione driver non tenterà questa conversione quando si chiamano le versioni SQLWCHAR dell'API ODBC (ad esempio, SQLDriverConnectW).  

- Il *ColumnSize* parametro di **SQLBindParameter** indica il numero di caratteri nel tipo SQL, mentre *BufferLength* è il numero di byte dell'applicazione buffer. Tuttavia, se il tipo di dati SQL è `varchar(n)` o `char(n)`, l'applicazione associa il parametro come SQL_C_CHAR o SQL_C_VARCHAR e la codifica dei caratteri del client è UTF-8, potrebbe verificarsi un errore "dati di tipo stringa, troncamento a destra" da anche se il driver di valore di *ColumnSize* è allineato con la dimensione del tipo di dati nel server. Questo errore si verifica poiché le conversioni tra le codifiche di caratteri possono modificare la lunghezza dei dati. Ad esempio, un apostrofo destro carattere (U + 2019) viene codificato in CP-1252 come 0x92 byte singolo, ma in UTF-8 come sequenza di byte di 3 0xe2 0x80 0x99.

Ad esempio, se la codifica è UTF-8 e si specifica 1 per entrambi *BufferLength* e *ColumnSize* in **SQLBindParameter** per un parametro out e quindi si tenta di recuperare il carattere precedente archiviato in un `char(1)` colonna nel server (utilizzando CP-1252), il driver tenta di convertirlo nella codifica UTF-8 3 byte, ma non è sufficiente il risultato in un buffer di 1 byte. In altra direzione, confronta *ColumnSize* con il *BufferLength* in **SQLBindParameter** prima di eseguire la conversione tra le tabelle codici diverse nel client e server. Poiché il valore 1 di *ColumnSize* è minore di un valore *BufferLength* di 3 (ad esempio), il driver genera un errore. Per evitare questo errore, verificare che la lunghezza dei dati dopo la conversione si integra con il buffer specificato o di una colonna. Si noti che *ColumnSize* non può essere maggiore di 8000 per il `varchar(n)` tipo.

## <a name="see-also"></a>Vedere anche  
[Linee guida per la programmazione](../../../connect/odbc/linux-mac/programming-guidelines.md)  
[Note sulla versione](../../../connect/odbc/linux-mac/release-notes.md)  


