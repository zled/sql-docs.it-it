---
title: Installazione di Microsoft Connector per SAP BW | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 64b93604ae38ed74099d0c291007ecb68a650742
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47728829"
---
# <a name="installing-the-microsoft-connector-for-sap-bw"></a>Installazione di Microsoft Connector for SAP BW
  [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW per SQL Server 2016 è un componente del Feature Pack di SQL Server 2016. Per installare Connector for SAP BW e la relativa documentazione, scaricare ed eseguire il programma di installazione dalla [pagina Web del Feature Pack di SQL Server 2016](http://go.microsoft.com/fwlink/?LinkId=746297).  

> [!IMPORTANT]
> Microsoft non prevede di rendere disponibile una versione aggiornata del connettore per SAP BW. Microsoft non è proprietaria del codice sorgente dei componenti SAP BW, sviluppati da terze parti, e di conseguenza non può aggiornarli. Valutare l'acquisto dei componenti di connettività SAP più recenti presso un partner Microsoft ISV, ad esempio [Theobald Software](https://theobald-software.com/en/xtract-is-productinfo.html). I partner Microsoft ISV hanno adattato i propri componenti di connettività SAP per SSIS per l'installazione in Azure.

> [!IMPORTANT]  
>  La documentazione per Microsoft Connector for SAP BW presuppone la conoscenza dell'ambiente SAP Netweaver BW. Per ulteriori informazioni su SAP Netweaver BW o per informazioni su come configurare oggetti e processi di SAP Netweaver BW, vedere la documentazione SAP.  
  
> [!IMPORTANT]  
>  L'estrazione di dati da SAP Netweaver BW richiede licenze SAP aggiuntive. Contattare SAP per verificare questi requisiti.  
  
## <a name="required-sap-files"></a>File SAP richiesti  
 Per usare [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW, non è necessario installare il software front-end SAP (SAP GUI) nel computer locale.  
  
 È tuttavia necessario copiare il file del connettore SAP .NET, librfc32.dll, nella sottocartella di sistema nella cartella Windows. In genere, il percorso di questa cartella è **C:\Windows\system32**.  
  
## <a name="considerations-for-64-bit-computers"></a>Considerazioni relative ai computer a 64 bit  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW supporta completamente la versione a 64 bit di [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. In un computer a 64 bit, [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW prevede i requisiti aggiuntivi seguenti:  
  
-   Per eseguire pacchetti in modalità a 64 bit in qualsiasi sistema operativo Windows a 64 bit, copiare la versione a 64 bit del file SAP GUI, librfc32.dll, nella cartella **system32** della cartella Windows. In genere, il percorso di questo file è **C:\Windows\system32**.  
  
-   Per eseguire pacchetti in modalità a 32 bit in qualsiasi sistema operativo Windows a 64 bit, copiare la versione del file SAP GUI, librfc32.dll, nella cartella **SysWow64** della cartella Windows. In genere, il percorso di questa cartella è **C:\Windows\SysWow64**.  
  
  
