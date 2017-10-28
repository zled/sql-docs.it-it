---
title: Impostazioni (sincronizzazione) (SybaseToSQL) del progetto | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2cd6bc01-b8e5-4312-83a4-eac66dc1d460
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b6533ce1774dec4967c9d43ea27902281d5bf756
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="project-settings-synchronization-sybasetosql"></a>Impostazioni del progetto (sincronizzazione) (SybaseToSQL)
La pagina di sincronizzazione del **impostazioni progetto** la finestra di dialogo contiene le impostazioni che consentono di personalizzare la modalità SSMA carica gli oggetti di database, ad esempio tabelle e stored procedure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
È possibile accedere a due diverse pagine di sincronizzazione che contengono le stesse impostazioni:  
  
-   Se si desidera specificare impostazioni per tutti i progetti futuri di SSMA, il **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa e quindi selezionare **sincronizzazione** nella parte inferiore del riquadro a sinistra.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** dal menu **impostazioni progetto**e quindi selezionare **sincronizzazione** nella parte inferiore del riquadro a sinistra.  
  
## <a name="options"></a>Opzioni  
**Tentativi**  
Specifica il numero di tentativi di SSMA è necessario apportare durante il caricamento di oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Gli oggetti che non vengono caricati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nel tentativo corrente verrà ritentata finché SSMA raggiunge il numero massimo di tentativi durante il processo di sincronizzazione corrente.  
  
## <a name="synchronization-for-sql-server"></a>Sincronizzazione per SQL Server  
**Aggiornare un oggetto locale nella modifica di oggetti locali e remoti**  
Specifica se SSMA deve sostituire i metadati dell'oggetto locale con i metadati dell'oggetto remoto se modificare gli oggetti locali e remoti.  
Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
Se si seleziona **scrivere nel Database**, SSMA aggiornerà gli oggetti del database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.   
Set di opzioni predefinito è **scrivere nel Database.**  
  
**Aggiornare un oggetto locale su Modifica oggetto locale**  
Specifica se SSMA deve sostituire i metadati dell'oggetto locale con i metadati dell'oggetto remoto se viene modificato l'oggetto remoto.  
Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
Se si seleziona **scrivere nel Database**, SSMA aggiornerà l'oggetto nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.   
Set di opzioni predefinito è **scrivere nel Database**.  
  
**Aggiornare un oggetto locale su Modifica oggetto remoto**  
Specifica se SSMA deve sostituire i metadati dell'oggetto locale con i metadati dell'oggetto remoto se viene modificato l'oggetto remoto.  
Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
Se si seleziona **scrivere nel Database**, SSMA aggiornerà l'oggetto nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.   
Set di opzioni predefinito è **aggiornamento dal Database**.  
  
**Aggiornamento quando i metadati dell'oggetto locale sono mancanti**  
Specifica se SSMA deve creare i metadati locali se esiste un oggetto nel database di destinazione, ma non in locale.  
Se si seleziona **aggiornamento dal Database**, SSMA consente di selezionare l'aggiornamento dall'opzione di Database quando viene soddisfatta la condizione.  
Se si seleziona **scrivere nel Database**, SSMA eliminerà l'oggetto dal database quando viene soddisfatta la condizione.  
Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.   
Set di opzioni predefinito è **aggiornamento dal Database**.  
  

