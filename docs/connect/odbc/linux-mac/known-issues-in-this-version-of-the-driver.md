---
title: Problemi noti di questa versione del Driver per SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- known issues
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 25ebc4837eb37604a45e98112fa5fc24bdb3e69b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742999"
---
# <a name="known-issues-in-this-version-of-the-driver"></a>Problemi noti in questa versione del driver

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Questo articolo contiene un elenco di problemi noti con Microsoft ODBC Driver 13 13.1 e 17 for SQL Server in Linux e macOS.

Altri problemi verranno pubblicati nel [blog del team di Microsoft ODBC Driver](http://blogs.msdn.com/b/sqlnativeclient/).  

- Windows, Linux e macOS convertono i caratteri provenienti dall'Area uso privato (PUA) o i caratteri definiti dall'utente finale (EUDC) in modo diverso. Per le conversioni eseguite sul server all'interno di [!INCLUDE[tsql](../../../includes/tsql-md.md)] viene usata la libreria di conversione Windows. Le conversioni del driver di usano le librerie di conversione di Windows, Linux o macOS. Le conversioni eseguite con le due librerie possono produrre risultati diversi. Per altre informazioni, vedere [End-User-Defined and Private Use Area Characters](/windows/desktop/Intl/end-user-defined-characters) (Caratteri definiti dall'utente finale e caratteri di area uso privato).

- Se il client di codifica è UTF-8, Gestione driver non sempre correttamente conversione da UTF-8 a UTF-16. Attualmente, il danneggiamento dei dati si verifica quando uno o più caratteri nella stringa non sono caratteri UTF-8 validi. Caratteri ASCII verranno mappati correttamente. Gestione driver tenta questa conversione quando si chiamano le versioni SQLCHAR dell'API ODBC (ad esempio, SQLDriverConnectA). Gestione driver non tenterà questa conversione quando si chiamano le versioni SQLWCHAR dell'API ODBC (ad esempio, SQLDriverConnectW).  

- Il *ColumnSize* del parametro **SQLBindParameter** indica il numero di caratteri nel tipo SQL, mentre *BufferLength* è il numero di byte dell'applicazione buffer. Tuttavia, se il tipo di dati SQL è `varchar(n)` o `char(n)`, se l'applicazione associa il parametro come SQL_C_CHAR o SQL_C_VARCHAR e se la codifica dei caratteri del client è UTF-8, è possibile che si verifichi un errore "Troncamento a destra della stringa di dati" nel driver anche se il valore di *ColumnSize* è allineato con la dimensione del tipo di dati nel server. Questo errore si verifica perché le conversioni tra codifiche di caratteri possono cambiare la lunghezza dei dati. Ad esempio, di caratteri (2019 U +) un apostrofo destro codificato in CP-1252 come 0x92 byte singolo, ma in formato UTF-8 alla sequenza di 3 byte 0xe2 0x80 0x99.

Ad esempio, se la codifica è UTF-8 e si specifica 1 per entrambi *BufferLength* e *ColumnSize* nelle **SQLBindParameter** per un parametro out e quindi tentare di recuperare il carattere precedente archiviato in un `char(1)` colonna nel server (tramite CP-1252), il driver prova a convertirlo per la codifica UTF-8 3 byte, ma non è sufficiente il risultato in un buffer a 1 byte. In altra direzione, confronta *ColumnSize* con il *BufferLength* nelle **SQLBindParameter** prima di eseguire la conversione tra le diverse tabelle codici sul client e server. Poiché il valore 1 di *ColumnSize* è minore di un valore *BufferLength* di 3 (ad esempio), il driver genera un errore. Per evitare questo errore, verificare che la lunghezza dei dati dopo la conversione si integra con il buffer specificato o una colonna. Si noti che *ColumnSize* non può essere maggiore di 8000 per il `varchar(n)` tipo.

## <a name="see-also"></a>Vedere anche  
[Linee guida per la programmazione](../../../connect/odbc/linux-mac/programming-guidelines.md)  
[Note sulla versione](../../../connect/odbc/linux-mac/release-notes.md)  

