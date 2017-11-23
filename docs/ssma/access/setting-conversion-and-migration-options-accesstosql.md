---
title: Impostazione di conversione e opzioni di migrazione (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- conversion, setting options
- migration options
- modes
- options, conversion settings
- project settings
- schemas
ms.assetid: 0a7304df-2f35-4453-96ef-7ac83dea1167
caps.latest.revision: "20"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5cea7c02271cdf7acabb585e4be51f404f658a62
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="setting-conversion-and-migration-options-accesstosql"></a>Impostazione di conversione e opzioni di migrazione (AccessToSQL)
Per ogni progetto SSMA, è possibile impostare le opzioni a livello di progetto. Queste opzioni specificano la modalità di conversione, migrazione dei dati e modalità di mapping dei tipi di dati di origine ai tipi di dati di destinazione. Prima di convertire oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure o la migrazione dei dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, verificare che le opzioni di configurazione siano appropriate per il progetto.  
  
## <a name="configuration-options-and-modes"></a>Modalità e le opzioni di configurazione  
SSMA è quattro set di impostazioni di configurazione e quattro modalità per la configurazione di queste impostazioni: predefinito, Optimistic, Full e personalizzato. La modalità predefinita è consigliata per la maggior parte degli utenti. Utilizzare la modalità ottimistica per le conversioni semplici. Se si desidera visualizzare tutti i messaggi, utilizzare la modalità completa. In modalità personalizzata, impostare le opzioni.  
  
Le impostazioni sono descritte nella sezione "Riferimenti all'interfaccia utente" di questa documentazione. Per ulteriori informazioni sulle impostazioni e come le impostazioni vengono applicate in ogni modalità, vedere gli argomenti seguenti:  
  
-   [Impostazioni progetto (conversione)](http://msdn.microsoft.com/en-us/bcebc635-c638-4ddb-924c-b9ccfef86388)  
  
-   [Impostazioni progetto (migrazione)](http://msdn.microsoft.com/en-us/4caebc9c-8680-4b99-a8fa-89c43161c95d)  
  
-   [Impostazioni progetto (GUI)](http://msdn.microsoft.com/en-us/cf06baf1-8714-48a3-95dc-781f6ca53693)  
  
-   [Impostazioni progetto (mapping dei tipi)](http://msdn.microsoft.com/en-us/b87b9683-abed-4677-8c50-18bdba704655)  
  
-   [Impostazioni del progetto (SQL Azure)](http://msdn.microsoft.com/en-us/bbb8a204-d0e4-4f0b-9709-271feb1f136e)  
  
## <a name="setting-project-options"></a>Impostazione delle opzioni di progetto  
In SSMA, è possibile configurare le impostazioni predefinite per tutti i progetti. Queste impostazioni vengono salvate nel file di configurazione di SSMA e applicate a qualsiasi nuovo progetto creato.  
  
**Per impostare opzioni di progetto predefinite**  
  
1.  Nel **strumenti** dal menu **impostazioni di progetto predefinite**.  
  
2.  Nel **impostazioni di progetto predefinite** la finestra di dialogo, effettuare una delle operazioni seguenti:  
  
    -   Selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **conversione o la migrazione o SQL Azure**.  
  
        > [!NOTE]  
        > Opzione di SQL Azure è disponibile nel **generale** scheda solo se il tipo di progetto creato è SQL Azure.  
  
    -   Per selezionare una modalità predefinita, selezionare **predefinito**, **Optimistic**, o **completo** nel **modalità** casella di riepilogo a discesa.  
  
    -   Per specificare una modalità personalizzata, selezionare **personalizzato** nel **modalità** casella, selezionare un'opzione nel riquadro a sinistra, fare clic sull'impostazione o un valore nel riquadro di destra, quindi selezionare o immettere la nuova impostazione o un valore.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
È anche possibile personalizzare le impostazioni per il progetto corrente. Queste impostazioni vengono salvate nel file di progetto corrente.  
  
**Per personalizzare le impostazioni per il progetto corrente**  
  
1.  Nel **strumenti** dal menu **impostazioni progetto**.  
  
2.  Nel **impostazioni progetto** la finestra di dialogo, effettuare una delle operazioni seguenti:  
  
    -   Per selezionare una modalità predefinita, selezionare **predefinito**, **Optimistic**, o **completo** nel **modalità** casella di riepilogo a discesa.  
  
    -   Per specificare una modalità personalizzata, selezionare **personalizzato** nel **modalità** casella, selezionare un'opzione nel riquadro a sinistra, fare clic sull'impostazione o un valore nel riquadro di destra, quindi selezionare o immettere la nuova impostazione o un valore.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
## <a name="next-steps"></a>Passaggi successivi  
Il passaggio successivo della migrazione dipende dalle esigenze del progetto:  
  
-   Per personalizzare il mapping dei tipi di dati di origine e di destinazione, vedere [Mapping tipi di origine e destinazione dati](http://msdn.microsoft.com/en-us/b362a075-16e7-423f-b63f-e1e9f02844a9)  
  
-   Per personalizzare il mapping del database di origine e destinazione, vedere [Mapping database di origine e destinazione](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4)  
  
-   In caso contrario, è possibile convertire le definizioni degli oggetti di database di Access in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o le definizioni degli oggetti di SQL Azure. Per ulteriori informazioni, vedere [la conversione di oggetti di Database di Access](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
