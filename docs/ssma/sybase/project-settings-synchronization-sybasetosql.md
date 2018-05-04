---
title: Impostazioni (sincronizzazione) (SybaseToSQL) del progetto | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2cd6bc01-b8e5-4312-83a4-eac66dc1d460
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0bbbe5982ced12fddabe3fd0a6ce629e0cc10c03
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
Set di opzioni predefinito è **scrittura al Database.**  
  
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
  
