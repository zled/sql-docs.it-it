---
title: Consentire agli utenti di servizi di SQL Server Machine Learning | Microsoft Docs
description: Come autorizzare gli utenti a servizi di SQL Server Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/05/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: ad5c3fa3bf94bb88041c9ec81773b2a26013e517
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100332"
---
# <a name="give-users-permission-to-sql-server-machine-learning-services"></a>Consentire agli utenti di SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo descrive come è possibile concedere agli utenti l'autorizzazione per eseguire gli script esterni in SQL Server Machine Learning Services e concedere le autorizzazioni di language (DDL) per database di dati, scrittura o lettura definizione.

Un account di accesso di SQL Server o account utente di Windows è necessario eseguire gli script esterni che usano dati di SQL Server o che vengono eseguite con SQL Server come contesto di calcolo.

Identifica l'account utente o account di accesso di *entità di sicurezza*, che potrebbe essere necessario più livelli di accesso, a seconda dei requisiti dello script esterno:

+ Autorizzazione per accedere al database in cui sono abilitati gli script esterni.
+ Autorizzazioni per leggere i dati da oggetti protetti, ad esempio le tabelle.
+ La possibilità di scrivere nuovi dati a una tabella, ad esempio un modello o i risultati di punteggio.
+ La possibilità di creare nuovi oggetti, ad esempio tabelle, stored procedure che utilizzano lo script esterno o personalizzato funzioni che usa R o il processo di Python.
+ Diritto di installare nuovi pacchetti nel computer SQL Server o usare i pacchetti disponibili a un gruppo di utenti.

Pertanto, ogni persona che esegue uno script esterno usando SQL Server come contesto di esecuzione deve essere mappato a un utente nel database. In sicurezza di SQL Server, è più semplice creare i ruoli per gestire i set di autorizzazioni e assegnare gli utenti a tali ruoli, anziché impostare separatamente le autorizzazioni utente.

Anche gli utenti che usano R o Python in uno strumento esterno devono essere mappati a un account di accesso o un account nel database se l'utente deve eseguire un script esterni nel database, o accedere agli oggetti di database e i dati. Le stesse autorizzazioni sono necessarie se lo script esterno viene inviato da un client di analisi scientifica dei dati remota o all'uso di una procedura T-SQL archiviate.

Si supponga, ad esempio, che è stato creato uno script esterno che viene eseguito nel computer locale e si desidera eseguire il codice in SQL Server. È necessario assicurarsi che siano soddisfatte le condizioni seguenti:

+ Il database consente le connessioni remote.
+ L'account di accesso SQL o l'account di Windows utilizzato per l'accesso al database è stato aggiunto a SQL Server a livello di istanza.
+ L'account di accesso SQL o un utente di Windows deve avere l'autorizzazione per eseguire gli script esterni. In genere, questa autorizzazione può essere aggiunta solo da un amministratore del database.
+ L'account di accesso SQL o un utente di Windows deve essere aggiunto come utente, con le autorizzazioni appropriate, in ogni database in cui lo script esterno esegue una qualsiasi di queste operazioni:
  + Il recupero dei dati.
  + La scrittura o aggiornamento dei dati.
  + Creazione di nuovi oggetti, ad esempio tabelle o le stored procedure.

Dopo che l'account di accesso o l'account utente di Windows è stato effettuato il provisioning e le autorizzazioni necessarie, è possibile eseguire uno script esterno in SQL Server usando un oggetto origine dati in R o la **revoscalepy** libreria in Python, o chiamando una stored procedure che contiene lo script esterno.

Ogni volta che uno script esterno viene avviato da SQL Server, la sicurezza del motore di database Ottiene il contesto di sicurezza dell'utente che ha avviato il processo e gestisce i mapping dell'utente o account di accesso agli oggetti a protezione diretta.

Pertanto, tutti gli script esterni che vengono avviati da un client remoto devono specificare le informazioni sull'account di accesso o utente come parte della stringa di connessione.

<a name="permissions-external-script"></a> 

## <a name="permission-to-run-scripts"></a>Autorizzazione per eseguire gli script

Se è stato installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] manualmente, mentre si eseguono gli script R o Python nella tua istanza di, è in genere eseguire gli script come amministratore. In questo modo, si dispone dell'autorizzazione implicita su varie operazioni e tutti i dati nel database.

La maggior parte degli utenti, tuttavia, si dispone di tali autorizzazioni con privilegi elevati. Ad esempio, gli utenti in un'organizzazione che usano account di accesso SQL per accedere al database in genere non è le autorizzazioni con privilegi elevate. Pertanto, per ogni utente che usa R o Python, è necessario concedere agli utenti di servizi di Machine Learning l'autorizzazione per eseguire gli script esterni in ogni database in cui viene utilizzata la lingua. Ecco come:

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> Autorizzazioni non sono specifiche del linguaggio di script supportato. In altre parole, non esistono livelli di autorizzazione separati per lo script R e lo script Python. Se è necessario mantenere separate le autorizzazioni per queste lingue, installare R e Python in istanze separate.

<a name="permissions-db"></a> 

## <a name="grant-databases-permissions"></a>Concedere le autorizzazioni di database

Mentre un utente è in esecuzione gli script, l'utente potrebbe essere necessario leggere i dati da altri database. L'utente potrebbe essere necessario anche creare nuove tabelle per archiviare i risultati e scrivere dati nelle tabelle.

Per ogni account utente di Windows o account di accesso SQL che esegue gli script R o Python, verificare che abbia le autorizzazioni appropriate sul database specifico: `db_datareader` per leggere i dati, `db_datawriter` per salvare gli oggetti nel database, o `db_ddladmin` per creare gli oggetti ad esempio le stored procedure o tabelle contenenti sottoposto a training e i dati serializzati.

Ad esempio, il seguente [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione offre l'accesso SQL *MySQLLogin* i diritti per eseguire query T-SQL *ML_Samples* database. Per eseguire questa istruzione, l'account di accesso SQL deve essere già presente nel contesto di sicurezza del server.

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulle autorizzazioni incluse in ogni ruolo, vedere [ruoli a livello di Database](../../relational-databases/security/authentication-access/database-level-roles.md).