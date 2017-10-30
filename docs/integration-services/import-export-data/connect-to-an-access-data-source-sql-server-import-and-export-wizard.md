---
title: Connettersi a un'origine dati di accesso (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b44c159a-c33d-4f3c-bdb8-9832f35317c8
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 71bb3914e31259bc95a1116c2db03708c0442e8c
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---
# <a name="connect-to-an-access-data-source-sql-server-import-and-export-wizard"></a>Connettersi a un'origine dati di accesso (SQL Server importazione / esportazione guidata)
In questo argomento viene illustrato come connettersi a un **Microsoft Access** dell'origine dati dal **scegliere un'origine dati** o **scegliere una destinazione** pagina di SQL Server di importazione / esportazione guidata.

La schermata seguente mostra una connessione di esempio a un database Microsoft Access. In questo esempio, non è necessario immettere un nome utente e una password, perché il database di destinazione non utilizza un file di informazioni sul gruppo di lavoro.

![Connettersi a accesso](../../integration-services/import-export-data/media/connect-to-access.jpg)

## <a name="options-to-specify"></a>Opzioni per specificare

> [!NOTE]
> Le opzioni di connessione per il provider di dati sono gli stessi se l'accesso è l'origine o destinazione. Ovvero le opzioni disponibili sono gli stessi in entrambi i **scegliere un'origine dati** e **scegliere una destinazione** pagine della procedura guidata.

**Origine dati**  
L'elenco dei provider di dati può contenere diverse voci di Microsoft Access. Selezionare la versione più recente installata o la versione che corrisponde alla versione di accesso che ha creato il file di database.

|Origine dati|Versione di Office|
|-------|-------|
|Microsoft Access (Microsoft.ACE.OLEDB.16.0)|Office 2016|
|Microsoft Access (Microsoft.ACE.OLEDB.15.0)|Office 2013|
|Microsoft Access (motore di Database Microsoft Access)|Office 2010 e Office 2007|
|Microsoft Access (motore di Database Microsoft Jet)|Versioni precedenti di Office 2007 di Office|

> [!IMPORTANT]
> È possibile scaricare e installare i file aggiuntivi per la connessione al database di Access. Vedere [ottenere i file necessari per connettersi a accesso](#officeDownloads) in questa pagina per altre informazioni.

 **Nome file**  
Specificare il percorso e il nome per il file di Access. Ad esempio, **c:\\MyData.mdb** per un file nel computer locale, o  **\\ \\Sales\\Database\\mdb** per un file in una condivisione di rete. In alternativa, fare clic su **Sfoglia**. 

 >   [!NOTE] 
 > Se si fa clic **Sfoglia** per individuare il file di accesso, il **aprire** filtri casella finestra di dialogo per i file con il precedente. MDB formato file di estensione e per impostazione predefinita. Tuttavia, nel provider di dati è inoltre possibile aprire i file con la versione più recente. Estensione di file di formato e ACCDB.
  
 **Sfoglia**  
 Consente di individuare il file di database tramite la finestra di dialogo **Apri**.  
  
 **Nome utente**  
Se un file di informazioni sul gruppo di lavoro è associato al database, specificare un nome utente valido.  
  
 **Password**  
Se un file di informazioni sul gruppo di lavoro è associato al database, specificare la password dell'utente qui.
 
Se il database è protetta con una sola password per tutti gli utenti, vedere [è il file di database protetto da password?](#database_password).
  
 **Avanzate**  
Specificare le opzioni avanzate, ad esempio la password del database o un file di informazioni sul gruppo di lavoro non predefinito nel **proprietà di Data Link** la finestra di dialogo.  

## <a name="i-dont-see-access-in-the-list-of-data-sources"></a>Non ho accesso nell'elenco delle origini dati
Se l'accesso non viene visualizzato nell'elenco delle origini dati, si esegue la procedura guidata a 64 bit? I provider per Excel e Access sono in genere a 32 bit e non sono visibili nella procedura guidata a 64 bit. Eseguire la procedura guidata a 32 bit.

> [!NOTE]
> Per utilizzare la versione a 64 bit di SQL Server di importazione / esportazione guidata, è necessario installare SQL Server. SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS) sono applicazioni a 32 bit e installare solo i file a 32 bit, inclusa la versione a 32 bit della procedura guidata.

## <a name="officeDownloads"></a>Ottenere i file che necessari per connettersi a accesso  
È possibile scaricare i componenti di connettività per le origini dati di Microsoft Office, incluso Access ed Excel, se non è già non sono installati. Scaricare la versione più recente dei componenti di connettività per l'accesso ed Excel file: [Microsoft Access Database Engine 2016 Redistributable](https://www.microsoft.com/download/details.aspx?id=54920).
  
La versione più recente dei componenti è possibile aprire i file creati con versioni precedenti di Access.

Se il computer dispone di una versione a 32 bit di Office, quindi è necessario installare la versione a 32 bit dei componenti ed è inoltre necessario assicurarsi di eseguire il pacchetto in modalità a 32 bit.

Se si dispone di una sottoscrizione Office 365, assicurarsi di scaricare il pacchetto ridistribuibile di 2016 del motore di accesso Database e non Microsoft Access 2016 Runtime. Quando si esegue il programma di installazione, è possibile vedere un messaggio di errore che non è possibile installare il download side-by-side con componenti di Office a portata di clic. Per ignorare questo messaggio di errore, eseguire l'installazione in modalità non interattiva, aprendo una finestra del prompt dei comandi ed eseguire il. File EXE scaricato con il `/quiet` passare. Esempio:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="database_password"></a>È il file di database protetto da password?
In alcuni casi, un database di Access è protetto da password, ma non sta utilizzando un file di informazioni sul gruppo di lavoro. Tutti gli utenti, sono necessario fornire la stessa password, ma non sono necessario immettere un nome utente. Per fornire una password del database, eseguire le operazioni seguenti.

1.  Nel **scegliere un'origine dati** o **scegliere una destinazione** pagina, fare clic su di **avanzate** pulsante per aprire la **proprietà di Data Link** la finestra di dialogo.  
2.  Nel **proprietà di Data Link** la finestra di dialogo, seleziona il **tutti** scheda.  
3.  Nell'elenco di proprietà e valori, selezionare **Jet OLEDB: database Password**.   
    
    ![Specificare la password di accesso, schermata 1](../../integration-services/import-export-data/media/specify-access-password-screen-1.jpg) 
4.  Fare clic su **Modifica valore** per aprire la **Modifica valore proprietà** la finestra di dialogo.  
    
    ![Specificare la password di accesso, schermata 2](../../integration-services/import-export-data/media/specify-access-password-screen-2.jpg)
5.  Nel **Modifica valore proprietà** finestra di dialogo immettere la password del database.
6.  Fare clic su **OK** in ogni finestra di dialogo per ripristinare il **scegliere un'origine dati** o **scegliere una destinazione** pagina della procedura guidata e continuare.

## <a name="keep-your-autonumber-values-when-you-export-from-access"></a>Mantenere i valori di contatore quando si esporta dall'accesso
Per consentire i valori di identità esistenti nei dati di origine da inserire in una colonna identity nella tabella di destinazione, scegliere il **Consenti IDENTITY_INSERT** opzione il **i mapping delle colonne** la finestra di dialogo. Per impostazione predefinita, la colonna identity di destinazione in genere non è possibile inserire valori esistenti. Per visualizzare il **i mapping delle colonne** nella finestra di dialogo **modificare i mapping** quando si raggiunge il **Selezione origine tabelle e viste** pagina della procedura guidata. Per visualizzare queste pagine, vedere [Selezione origine tabelle e viste](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md) e [i mapping delle colonne](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).

Se le chiavi primarie esistenti si trovano in una colonna Identity, in una contatore o nell'equivalente, in genere è necessario selezionare questa opzione per mantenere i valori di chiave primaria esistenti. In caso contrario la colonna Identity di destinazione assegna in genere nuovi valori.

## <a name="see-also"></a>Vedere anche
[Scegliere un'origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Scegliere una destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


