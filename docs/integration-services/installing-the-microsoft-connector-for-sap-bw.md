---
title: "Installazione di Microsoft Connector for SAP BW | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Installazione di Microsoft Connector for SAP BW
  [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW per SQL Server 2016 è un componente del Feature Pack di SQL Server 2016. Per installare Connector for SAP BW e la relativa documentazione, scaricare ed eseguire il programma di installazione dalla [pagina Web del Feature Pack di SQL Server 2016](http://go.microsoft.com/fwlink/?LinkId=746297).  
  
> [!IMPORTANT]  
>  La documentazione per Microsoft Connector for SAP BW presuppone la conoscenza dell'ambiente SAP Netweaver BW. Per ulteriori informazioni su SAP Netweaver BW o per informazioni su come configurare oggetti e processi di SAP Netweaver BW, vedere la documentazione SAP.  
  
> [!IMPORTANT]  
>  L'estrazione di dati da SAP Netweaver BW richiede licenze SAP aggiuntive. Contattare SAP per verificare questi requisiti.  
  
## File SAP richiesti  
 Per usare [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW, non è necessario installare il software front-end SAP (SAP GUI) nel computer locale.  
  
 È tuttavia necessario copiare il file del connettore SAP .NET, librfc32.dll, nella sottocartella di sistema nella cartella Windows. In genere, il percorso di questa cartella è **C:\Windows\system32**.  
  
## Considerazioni relative ai computer a 64 bit  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW supporta completamente la versione a 64 bit di [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. In un computer a 64 bit, [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW prevede i requisiti aggiuntivi seguenti:  
  
-   Per eseguire pacchetti in modalità a 64 bit in qualsiasi sistema operativo Windows a 64 bit, copiare la versione a 64 bit del file SAP GUI, librfc32.dll, nella cartella **system32** della cartella Windows. In genere, il percorso di questo file è **C:\Windows\system32**.  
  
-   Per eseguire pacchetti in modalità a 32 bit in qualsiasi sistema operativo Windows a 64 bit, copiare la versione del file SAP GUI, librfc32.dll, nella cartella **SysWow64** della cartella Windows. In genere, il percorso di questa cartella è **C:\Windows\SysWow64**.  
  
  