---
title: Istruzione SQL Create Table (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
caps.latest.revision: 67
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ad9b68e2a0ac4cd88917a7b45c7a8f12b14f3ab4
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a>Istruzione SQL CREATE TABLE (Importazione/Esportazione guidata SQL Server)
Se nella finestra di dialogo **Mapping colonne** si seleziona **Crea tabella di destinazione** e quindi **Modifica codice SQL** , l'Importazione/Esportazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] visualizza la finestra di dialogo **Istruzione SQL CREATE TABLE** . In questa pagina è necessario esaminare ed eventualmente personalizzare il comando **CREATE TABLE** che verrà eseguito dalla procedura guidata per creare la nuova tabella di destinazione.
  
> [!NOTE]
> Per maggiori informazioni sull'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TABLE e non sulla finestra di dialogo **Istruzione SQL CREATE TABLE** dell'Importazione/Esportazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md). 
  
## <a name="screen-shot-of-the-create-table-sql-statement-page"></a>Screenshot della pagina Istruzione SQL CREATE TABLE  
 L'immagine riportata di seguito illustra la finestra di dialogo **Istruzione SQL CREATE TABLE** della procedura guidata.
 
In questo esempio, la finestra di dialogo **Istruzione SQL** contiene l'istruzione **CREATE TABLE** predefinita generata dalla procedura guidata. Questa istruzione crea una nuova tabella di destinazione denominata **Person.AddressNew** che rappresenta una copia di **Person. Address** tabella di origine. 
  
 ![Pagina di creazione tabella dell'importazione / esportazione guidata](../../integration-services/import-export-data/media/create-table.png "pagina di creazione tabella dell'importazione / esportazione guidata")  
  
## <a name="review-or-regenerate-the-create-table-statement"></a>Rivedere o rigenerare l'istruzione CREATE TABLE  
 **Istruzione SQL**  
Consente di visualizzare l'istruzione SQL generata automaticamente ed eventualmente di personalizzarla.
 
Se si modifica il comando CREATE TABLE predefinita, potrebbe anche essere necessario apportare modifiche ai mapping delle colonne associate quando si torna al **i mapping delle colonne** la finestra di dialogo.  
  
Per includere un ritorno a capo nel testo dell'istruzione SQL, premere CTRL+INVIO. Premere solo INVIO per chiudere la finestra di dialogo.  
  
Per altre informazioni sull'istruzione CREATE TABLE e la relativa sintassi, vedere [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).   
  
 **Genera automaticamente**  
 Ripristinare l'istruzione SQL predefinita, se è stato modificato, fare clic su **genera automaticamente**.  
  
## <a name="create-a-table-that-includes-a-filestream-column"></a>Creare una tabella che include una colonna FILESTREAM  
 L'Importazione/Esportazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un'istruzione CREATE TABLE predefinita basata sull'origine dati connessa. Questa istruzione CREATE TABLE predefinita non include l'attributo FILESTREAM anche se la tabella di origine include una colonna FILESTREAM.
 1.  Prima di copiare una colonna FILESTREAM tramite la procedura guidata, implementare l'archiviazione di FILESTREAM nel database di destinazione.
 2.  Aggiungere quindi manualmente l'attributo FILESTREAM all'istruzione CREATE TABLE nella finestra di dialogo **Istruzione SQL CREATE TABLE** .  

Per ulteriori informazioni sulla sintassi, vedere [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md). Per altre informazioni su FILESTREAM, vedere [Dati BLOB &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
## <a name="whats-next"></a>Operazioni successive  
 Dopo aver rivisto e personalizzato il comando CREATE TABLE e fatto clic su **OK**, dalla finestra di dialogo **Istruzione SQL CREATE TABLE** si torna alla finestra di dialogo **Mapping colonne** . Per altre informazioni, vedere [Mapping colonne](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).
 
 ## <a name="see-also"></a>Vedere anche
[Iniziare con questo semplice esempio dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



