---
title: Mapping colonne (Importazione/Esportazione guidata SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.columnmapandtransform.f1
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b4afba941b06e073f2dddffdb96a2dd95ffda5b3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063386"
---
# <a name="column-mappings-sql-server-import-and-export-wizard"></a>Mapping colonne (Importazione/Esportazione guidata SQL Server)
  Usare la **mapping delle colonne** finestra di dialogo per modificare i parametri di trasformazione.  
  
> [!NOTE]  
>  Non è necessario copiare tutte le colonne in una tabella quando si seleziona l'opzione Copia tabella. Selezionare  **\<ignorare >** nel **destinazione** colonna questa finestra di dialogo per le colonne che si desidera ignorare.  
  
 Per ulteriori informazioni su questa procedura guidata, vedere [SQL Server di importazione / esportazione guidata](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Per ulteriori informazioni sulle opzioni per avviare la procedura guidata, nonché le autorizzazioni necessarie per eseguire correttamente la procedura guidata, vedere [eseguire il Server importazione / esportazione guidata SQL](start-the-sql-server-import-and-export-wizard.md).  
  
 Lo scopo di Importazione/Esportazione guidata SQL Server è la copia di dati da un'origine a una destinazione. La procedura guidata può inoltre creare automaticamente un database di destinazione e le tabelle di destinazione. Se tuttavia è necessario copiare più database o tabelle, o altri tipi di oggetti di database, è preferibile utilizzare Copia guidata database. Per altre informazioni, vedere [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Opzioni  
 **Origine**  
 Identifica la tabella, la visualizzazione o la query di origine selezionata.  
  
 **Destinazione**  
 Identifica la tabella, la visualizzazione o la query di destinazione selezionata.  
  
 **Crea tabella di destinazione/file**  
 Consente di specificare se creare la tabella di destinazione qualora non esista già.  
  
 **Elimina righe nella tabella di destinazione/file**  
 Consente di specificare se cancellare i dati da una tabella esistente prima di caricare nuovi dati.  
  
 **Aggiungi righe alla tabella di destinazione/file**  
 Consente di specificare se aggiungere nuovi dati a quelli già presenti in una tabella esistente.  
  
 **Modifica codice SQL**  
 Utilizzare l'istruzione predefinita nella **istruzione SQL Create Table** dialogo casella o modificarla in base alle esigenze. Se si modifica questa istruzione, è necessario inoltre eseguire modifiche collegate al mapping della tabella.  
  
 **Elimina e ricrea tabella di destinazione**  
 Selezionare questa opzione per sovrascrivere la tabella di destinazione. Questa opzione è disponibile solo quando si utilizza la procedura guidata per creare la tabella di destinazione. La tabella di destinazione viene eliminata e ricreata solo se si salva il pacchetto creato dalla procedura guidata e quindi lo si esegue nuovamente.  
  
 **Consenti IDENTITY_INSERT**  
 Selezionare questa opzione per consentire l'inserimento dei valori di identità esistenti nei dati di origine all'interno di una colonna Identity della tabella di destinazione. Per impostazione predefinita, non è possibile applicare questa opzione alla colonna Identity di destinazione.  
  
 **Mapping**  
 Consente di visualizzare la modalità di mapping tra ogni colonna nell'origine dati e una colonna nella destinazione.  
  
 L'elenco contiene le colonne seguenti:  
  
 **Origine**  
 Consente di visualizzare ogni colonna di origine da cui è possibile impostare parametri di trasformazione.  
  
 **Destinazione**  
 Consente di specificare se ignorare una colonna durante l'operazione di copia. È possibile copiare solo un subset di colonne selezionando  **\<ignorare >** in questa colonna per le colonne che si desidera ignorare. Prima di eseguire il mapping delle colonne, è necessario ignorare tutte le colonne di cui non verrà eseguito il mapping.  
  
 **Tipo**  
 Consente di selezionare un tipo di dati per la colonna.  
  
 **Ammette i valori Null**  
 Consente di specificare se una colonna può supportare un valore Null.  
  
 **Dimensione**  
 Consente di specificare il numero di caratteri nella colonna.  
  
 **Precisione**  
 Consente di specificare la precisione dei dati visualizzati, indicando il numero di cifre.  
  
 **Scala**  
 Consente di specificare la scala dei dati visualizzati, indicando il numero di posizioni decimali.  
  
  