---
title: Impostando le opzioni di migrazione (AccessToSQL) e conversione | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
caps.latest.revision: 20
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: bf73284de3f23aa861c446e4a2ed67278f4a5ce5
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979703"
---
# <a name="setting-conversion-and-migration-options-accesstosql"></a>Impostando le opzioni di migrazione (AccessToSQL) e conversione
Per ogni progetto SSMA, è possibile impostare le opzioni a livello di progetto. Queste opzioni specificano come gli oggetti vengono convertiti, migrazione dei dati e come eseguire il mapping tipi di dati di origine ai tipi di dati di destinazione. Prima di convertire gli oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure o eseguire la migrazione dei dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, verificare che le opzioni di configurazione siano appropriate per il progetto.  
  
## <a name="configuration-options-and-modes"></a>Le modalità e le opzioni di configurazione  
SSMA è quattro set di impostazioni di configurazione e quattro modalità per la configurazione di queste impostazioni: Default, Optimistic, Full e personalizzato. La modalità predefinita è consigliata per la maggior parte degli utenti. Utilizzare la modalità ottimistica per le conversioni semplici. Se si desidera vedere tutti i messaggi, usare la modalità completa. Nella modalità personalizzata, impostare le opzioni.  
  
Le impostazioni sono descritte nella sezione "Riferimenti dell'interfaccia utente" di questa documentazione. Per altre informazioni sulle impostazioni e come vengono applicate le impostazioni in ciascuna modalità, vedere gli argomenti seguenti:  
  
-   [Impostazioni progetto (conversione)](http://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388)  
  
-   [Impostazioni progetto (migrazione)](http://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d)  
  
-   [Impostazioni progetto (GUI)](http://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693)  
  
-   [Impostazioni progetto (mapping dei tipi)](http://msdn.microsoft.com/b87b9683-abed-4677-8c50-18bdba704655)  
  
-   [Impostazioni progetto (SQL Azure)](http://msdn.microsoft.com/bbb8a204-d0e4-4f0b-9709-271feb1f136e)  
  
## <a name="setting-project-options"></a>Impostazione delle opzioni progetto  
In SSMA, è possibile configurare le impostazioni predefinite per tutti i progetti. Queste impostazioni vengono salvate nel file di configurazione di SSMA e applicate a ogni nuovo progetto creato.  
  
**Per impostare le opzioni del progetto predefinito**  
  
1.  Nel **degli strumenti** dal menu **impostazioni di progetto predefinite**.  
  
2.  Nel **impostazioni di progetto predefinite** nella finestra di dialogo, effettuare una delle operazioni seguenti:  
  
    -   Seleziona tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati / modificato da **versione di destinazione della migrazione** elenco a discesa, fare clic su **generali** nella parte inferiore del riquadro a sinistra e quindi selezionare **Conversione o la migrazione o di SQL Azure**.  
  
        > [!NOTE]  
        > Opzione di SQL Azure è disponibile nel **generale** scheda solo se il tipo di progetto creato è SQL Azure.  
  
    -   Per selezionare una modalità predefinita, selezionare **predefinite**, **Optimistic**, o **completo** nel **modalità** casella di riepilogo a discesa.  
  
    -   Per specificare una modalità personalizzata, selezionare **personalizzati** nel **modalità** casella, selezionare un'opzione nel riquadro sinistro, fare clic sull'impostazione o un valore nel riquadro di destra e quindi selezionare o immettere il valore o la nuova impostazione.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
È anche possibile personalizzare le impostazioni per il progetto corrente. Queste impostazioni vengono salvate nel file di progetto corrente.  
  
**Per personalizzare le impostazioni per il progetto corrente**  
  
1.  Nel **degli strumenti** dal menu **le impostazioni del progetto**.  
  
2.  Nel **impostazioni del progetto** nella finestra di dialogo, effettuare una delle operazioni seguenti:  
  
    -   Per selezionare una modalità predefinita, selezionare **predefinite**, **Optimistic**, o **completo** nel **modalità** casella di riepilogo a discesa.  
  
    -   Per specificare una modalità personalizzata, selezionare **personalizzati** nel **modalità** casella, selezionare un'opzione nel riquadro sinistro, fare clic sull'impostazione o un valore nel riquadro di destra e quindi selezionare o immettere il valore o la nuova impostazione.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
## <a name="next-steps"></a>Passaggi successivi  
Il passaggio successivo nel processo di migrazione dipende dalle esigenze del progetto:  
  
-   Per personalizzare il mapping dei tipi di dati di origine e di destinazione, vedere [Mapping tipi di origine e destinazione dati](http://msdn.microsoft.com/b362a075-16e7-423f-b63f-e1e9f02844a9)  
  
-   Per personalizzare il mapping dei database di origine e destinazione, vedere [mapping dei database di origine e destinazione](http://msdn.microsoft.com/69bee937-7b2c-49ee-8866-7518c683fad4)  
  
-   In caso contrario, è possibile convertire le definizioni degli oggetti di database di Access in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o le definizioni degli oggetti di SQL Azure. Per altre informazioni, vedere [la conversione di oggetti di Database di Access](http://msdn.microsoft.com/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione dei database di Access a SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
