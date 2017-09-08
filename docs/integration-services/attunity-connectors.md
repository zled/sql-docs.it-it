---
title: Connettori Microsoft per Oracle e Teradata di attunity (SSIS) | Documenti Microsoft
ms.date: 05/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 926c0c51b5a55a2869b73666f5620fa56e139cca
ms.openlocfilehash: fd8b0177227167f6caa3417029bb2acb974fe181
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="microsoft-connectors-for-oracle-and-teradata-by-attunity-for-integration-services-ssis"></a>Connettori Microsoft per Oracle e Teradata di attunity per Integration Services (SSIS)

È possibile scaricare i connettori per i servizi di integrazione di Attunity che ottimizzare le prestazioni durante il caricamento di dati da Oracle o Teradata in un pacchetto SSIS.

## <a name="download-the-latest-attunity-connectors"></a>Scaricare i più recenti connettori di Attunity

Ottenere la versione più recente dei connettori di:  
[V 5.0 connettori Microsoft per Oracle e Teradata](https://www.microsoft.com/download/details.aspx?id=55179)

## <a name="issue---the-attunity-connectors-arent-visible-in-the-ssis-toolbox"></a>Problema: I connettori di Attunity non sono visibili nella casella degli strumenti SSIS

Per visualizzare i connettori di Attunity nella casella degli strumenti SSIS, è sempre necessario installare la versione dei connettori che destinazioni la stessa versione di SQL Server la versione di SQL Server Data Tools (SSDT) installato nel computer in uso. (L'utente potrebbe avere versioni precedenti dei connettori di cui è installati.) Questo requisito è indipendente dalla versione di SQL Server che si desidera indirizzare i progetti SSIS e pacchetti.

Ad esempio, se è installata la versione più recente di SSDT, è necessario versione 17 di SSDT con un numero di build che inizia con 14. Questa versione di SSDT aggiunge il supporto per SQL Server 2017. Per visualizzare e utilizzare il Attunity connettori SSIS pacchetto development - anche se si desidera destinazione una versione precedente di SQL Server, inoltre necessario installare la versione più recente dei connettori di Attunity, versione 5.0. Questa versione dei connettori aggiunge inoltre supporto per SQL Server 2017.

Controllare la versione installata di SSDT in Visual Studio da **Guida** | **su Microsoft Visual Studio**, o in **programmi e funzionalità** nel Pannello di controllo. Quindi installare la versione corrispondente dei connettori di Attunity dalla tabella seguente.

|Versione SSDT|Numero di build SSDT|Versione di SQL Server di destinazione|Versione richiesta di connettori|
|---------|---------|---------|---------|
|17|Inizia con 14|SQL Server 2017|[V 5.0 connettori Microsoft per Oracle e Teradata](https://www.microsoft.com/download/details.aspx?id=55179)|
|16|Inizia con 13|SQL Server 2016|[V 4.0 connettori Microsoft per Oracle e Teradata](https://www.microsoft.com/download/details.aspx?id=52950)|
||||

## <a name="download-the-latest-sql-server-data-tools-ssdt"></a>Scaricare il più recente SQL Server Data Tools (SSDT)

Ottenere la versione più recente di SSDT di seguito:  
[Scaricare SQL Server Data Tools (SSDT)](..//ssdt/download-sql-server-data-tools-ssdt.md)
