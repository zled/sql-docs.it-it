---
title: Schermata della procedura guidata 2, il Driver ODBC per SQL Server, dell'origine dati | Documenti Microsoft
ms.custom: 
ms.date: 09/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: e861bc52621e520a27e930dd22f1a1eb9613cc76
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="data-source-wizard-screen-2"></a>Creazione guidata origine dati - Schermata 2

Specificare il metodo di autenticazione e configurare le voci client avanzato Microsoft SQL Server e l'account e la password, che il driver ODBC per SQL Server utilizzerà per connettersi a SQL Server durante la configurazione dell'origine dati.

## <a name="options"></a>Opzioni

### <a name="with-integrated-windows-authentication"></a>Con l'autenticazione integrata di Windows

Specifica che il driver è richiesta una connessione protetta (o trusted) a SQL Server. Se si seleziona questa opzione, in SQL Server verrà utilizzata la sicurezza degli accessi integrata per stabilire connessioni con questa origine dati, indipendentemente dalla modalità di sicurezza degli accessi corrente del server. Qualsiasi password o ID di accesso specificato viene ignorato. L'amministratore di sistema di SQL Server deve essere associati l'account di accesso di Windows con un ID di accesso di SQL Server (ad esempio, utilizzando SQL Server Management Studio).

È inoltre possibile specificare un nome SPN per il server.

### <a name="with-active-directory-integrated-authentication"></a>Con l'autenticazione integrata di Active Directory

Specifica che il driver si autenticano a SQL Server con Azure Active Directory. Se selezionata, SQL Server utilizza la sicurezza degli accessi integrata in Azure Active Directory per stabilire una connessione con questa origine dati, indipendentemente dalla modalità di sicurezza corrente di account di accesso nel server.

### <a name="with-sql-server-authentication"></a>Con l'autenticazione di SQL Server

Specifica che il driver si autenticano a SQL Server utilizzando un ID di accesso e una password.

### <a name="with-active-directory-password-authentication"></a>Con l'autenticazione di Password di Active Directory

Specifica che il driver si autenticano a SQL Server utilizzando un ID di accesso di Azure Active Directory e una password.

### <a name="login-id"></a>ID accesso

Specifica l'ID di accesso, il driver utilizza per la connessione a SQL Server se **con autenticazione di SQL Server tramite un ID di accesso e password immessi dall'utente** o **l'autenticazione con Password di Active Directory utilizzando un ID di accesso e la password immessi dall'utente** è selezionata. Si applica solo alla connessione effettuata per determinare le impostazioni predefinite del server. Non si applica invece alle connessioni successive effettuate utilizzando l'origine dati dopo la relativa creazione.

### <a name="password"></a>Password

Specifica la password, il driver utilizza per la connessione a SQL Server se **con autenticazione di SQL Server tramite un ID di accesso e password immessi dall'utente** o **l'autenticazione con Password di Active Directory utilizzando un ID di accesso e la password immessi dall'utente** è selezionata. Si applica solo alla connessione effettuata per determinare le impostazioni predefinite del server. Non si applica invece alle connessioni successive effettuate utilizzando la nuova origine dati.

Entrambi i **ID di accesso** e **Password** caselle sono disabilitate se **autenticazione integrata di Windows** o **con integrata in Active Directory autenticazione** è selezionata.

### <a name="next"></a>Avanti

Passare alla schermata successiva della procedura guidata.

### <a name="back"></a>Indietro

Consente di tornare alla schermata precedente della procedura guidata.

## <a name="next-steps"></a>Passaggi successivi

[Schermata di creazione guidata origine dati 1](../../../connect/odbc/windows/dsn-wizard-1.md)

[Schermata di creazione guidata origine dati 3](../../../connect/odbc/windows/dsn-wizard-3.md)


