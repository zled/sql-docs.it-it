---
title: Proprietà personalizzate del file non elaborato | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e81f7e1-fac0-4b57-b145-8f1b9e4720bf
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ee1b5a26edc9c1335abf35dd2af23e7035b84809
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066132"
---
# <a name="raw-file-custom-properties"></a>Proprietà personalizzate del file non elaborato
  **Proprietà personalizzate delle origini**  
  
 L'origine file non elaborato include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate dell'origine file non elaborato. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (enumerazione)|Modalità utilizzata per accedere ai dati non elaborati. I valori possibili sono `File name` (0) e `File name from variable` (1). Il valore predefinito è `File name` (0).|  
|FileName|String|Percorso e nome del file di origine.|  
  
 L'output e le colonne di output dell'origine file non elaborato non includono proprietà personalizzate.  
  
 Per ulteriori informazioni, vedere [Raw File Source](raw-file-source.md).  
  
 **Proprietà personalizzate delle destinazioni**  
  
 La destinazione file non elaborato include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate della destinazione file non elaborato. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (enumerazione)|Valore che specifica se la proprietà FileName include un nome file o il nome di una variabile che contiene un nome file. Le opzioni valide sono `File name` (0) e `File name from variable` (1).|  
|FileName|String|Nome del file in cui la destinazione file non elaborato scrive.|  
|WriteOption|Integer (enumerazione)|Valore che specifica se la destinazione file non elaborato elimina un file esistente con lo stesso nome. Le opzioni sono `Create Always` (0), `Create Once` (1), `Truncate and Append` (3), e `Append` (2). Il valore predefinito di questa proprietà è `Create Always` (0).|  
  
> [!NOTE]  
>  È possibile eseguire un'operazione di aggiunta solo se i metadati dei dati aggiunti corrispondono a quelli dei dati già presenti nel file.  
  
 L'input e le colonne di input della destinazione file non elaborato non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Destinazione file non elaborato](raw-file-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](../common-properties.md)  
  
  