---
title: Destinazione di archivio Azure Data Lake | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSDEST.F1
- sql14.dts.designer.afpadlsdest.f1
ms.assetid: 4c4f504f-dd2b-42c5-8a20-1a8ad9a5d632
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5f8cfa5230a36a27a7e98fa6f336bcee56fa062e
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="azure-data-lake-store-destination"></a>Destinazione di Azure Data Lake Store
  Il componente **Destinazione di Azure Data Lake Store** consente a un pacchetto SSIS di scrivere dati in Azure Data Lake Store. I formati di file supportati sono testo, Avro e ORC. 
  
 Il **destinazione di archiviazione di Azure Data Lake** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
 
 >   [!NOTE]
 > Per assicurarsi che la Gestione connessioni di Azure Data Lake Store e che i componenti che la usano, cioè l'origine e la destinazione di Azure Data Lake Store, possano connettersi ai servizi, scaricare la versione del Feature Pack di Azure più recente da [qui](https://www.microsoft.com/download/details.aspx?id=49492). 

## <a name="configure-the-azure-data-lake-store-destination"></a>Configurare Destinazione di Azure Data Lake Store  
1. Trascinare **Destinazione di Azure Data Lake Store** nella finestra di progettazione del flusso di dati e fare doppio clic per visualizzare l'editor.  

2.  Nel campo **Gestione connessioni di Azure Data Lake Store** specificare un'istanza esistente di Gestione connessioni di Azure Data Lake Store o creare una nuova istanza che faccia riferimento a un servizio di Azure Data Lake Store.  
  
    1.  Per il campo **Percorso file** specificare il nome del file in cui si vogliono scrivere i dati. Se il file esiste già, il suo contenuto verrà sovrascritto.  
  
    2.  Per il campo **Formato file** specificare il formato file che si vuole usare.  
  
        Se il formato del file corrisponde a testo, è necessario impostare il valore **Carattere delimitatore di colonna** . Selezionare anche **Nomi di colonne nella prima riga di dati** se la prima riga nel file contiene i nomi di colonna.  

        Se il formato del file corrisponde a ORC, è necessario installare JRE per la piattaforma corrispondente. 
  
3.  Dopo aver specificato le informazioni di connessione, passare alla pagina **Colonne** per eseguire il mapping delle colonne di origine alle colonne di destinazione per il flusso di dati SSIS.  
  
  

