---
title: La connessione a MySQL (MySQLToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 94099d01-ab19-4d58-a172-340c86b4a0f3
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: eb5ded86bf30a942aaece3f7d1404df781c24112
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="connect-to-mysql-mysqltosql"></a>La connessione a MySQL (MySQLToSQL)
Utilizzare il **connessione a MySQL** la finestra di dialogo per la connessione al database di MySQL che si desidera eseguire la migrazione.  
  
Per accedere a questa finestra di dialogo, scegliere il **File** dal menu **connessione a MySQL**. Se in precedenza si è connessi, il comando è **Riconnetti a MySQL**.  
  
## <a name="options"></a>Opzioni  
**Provider**  
  
Provider MySQL disponibile è MySQL 5.1 provider ODBC (attendibile).  
  
**Mode**  
  
La modalità predefinita è la modalità Standard. In modalità Standard immettere o selezionare i valori per MySQL, nome del server, porta del server, nome utente e password.  
  
**Nome server**  
  
Immettere il nome del server MySQL. Questa è un'opzione di modalità Standard.  
  
**Porta server**  
  
Immettere la porta del Server. La porta del server predefinita è 3306. Questa è un'opzione di modalità Standard.  
  
**Nome utente**  
  
Immettere il nome utente utilizzato per connettersi al database MySQL SSMA.  
  
**Password**  
  
Immettere la password associata al nome utente.  
  
**SSL**  
  
Se si desidera stabilire una connessione sicura a MySQL, avvalersi di Secure Socket Layer (SSL) controllando il **SSL** casella di controllo.  
  
**Configurare**  
  
Fornisce un'opzione per configurare la connessione a MySQL tramite Secure Socket Layer (SSL).  
  
> [!NOTE]  
> Per abilitare **configura**, SSL deve essere impostato su **True**.  
  
Se si sceglie il pulsante "Configura", viene visualizzata una finestra di dialogo. Utilizzare la crittografia durante la connessione al MySQL Database, percorso file tre certificato seguenti presente nella finestra di dialogo deve essere definito [Privacy avanzata posta certificati (PEM)]:  
  
-   **Autorità di certificazione SSL:** specifica il percorso di un file con un elenco di certificati Autorità di certificazione SSL.  
  
-   **Certificato SSL:** specifica il nome del file di certificato SSL da utilizzare per stabilire una connessione sicura.  
  
-   **La chiave SSL:** specifica il nome del file di chiave SSL da utilizzare per stabilire una connessione sicura.  
  
> [!NOTE]  
> -   Il **OK** pulsante viene abilitato quando sono state fornite le informazioni necessarie. Se non sono validi tutti i percorsi di file, il pulsante "OK" rimarrà disabilitato.  
> -   Il **Annulla** pulsante consente di chiudere la finestra di dialogo e **disattiva** all'opzione SSL dal modulo di connessione principale.  
  

