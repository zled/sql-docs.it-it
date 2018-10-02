---
title: Destinazione file HDFS | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfiledest.f1
ms.assetid: 4338ce9f-c077-4301-aca5-47ed070ec94d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: addb3312def505802aab695301f7cca170eab3d7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47799669"
---
# <a name="hdfs-file-destination"></a>Destinazione file HDFS
  Il componente Destinazione file HDFS consente a un pacchetto SSIS di scrivere dati in un file HDFS. I formati di file supportati sono testo, Avro e ORC.  
  
 Per configurare Destinazione file HDFS, trascinare e rilasciare Origine file HDFS nella finestra di progettazione del flusso di dati e fare doppio clic sul componente per aprire l'editor.  
  
 ![Editor destinazione file HDFS](../../integration-services/data-flow/media/hdfs-file-dest.png "Editor destinazione file HDFS")  
  
## <a name="options"></a>Opzioni  
 Configurare le opzioni seguenti nella scheda **Generale** della finestra di dialogo **Editor destinazione file HDFS** .  
  
|Campo|Descrizione|  
|-----------|-----------------|  
|**Connessione Hadoop**|Specificare un'istanza esistente di Gestione connessione Hadoop o crearne una nuova. Questa istanza di Gestione connessione indica dove sono ospitati i file HDFS.|  
|**Percorso file**|Specificare il nome del file HDFS.|  
|**Formato del file**|Specificare il formato del file HDFS. Le opzioni disponibili sono testo, Avro o ORC.|  
|**Carattere delimitatore di colonna**|Se si seleziona il formato testo, specificare il carattere delimitatore di colonna.|  
|**Nomi di colonna nella prima riga di dati**|Se si seleziona il formato testo, indicare se la prima riga del file contiene i nomi delle colonne.|  
  
 Dopo aver configurato queste opzioni, selezionare la scheda **Colonne** per eseguire il mapping delle colonne di origine alle colonne di destinazione del flusso di dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione connessione Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Origine file HDFS](../../integration-services/data-flow/hdfs-file-source.md)  
  
  
