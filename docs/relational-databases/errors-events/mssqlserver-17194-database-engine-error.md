---
title: MSSQLSERVER_17194 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- "17194"
helpviewer_keywords:
- 17194 (Database Engine error)
ms.assetid: 0d03eb20-28a7-4ceb-8903-7f9420a620f7
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f33e6e16d4f62e7b39afe3b5cd9b57ce13d15a1a
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver17194"></a>MSSQLSERVER_17194
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17194|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico||  
|Testo del messaggio|Impossibile caricare la libreria di provider SSL necessaria per l'accesso. La connessione è stata chiusa. SSL viene utilizzato per crittografare la sequenza di accesso o tutte le comunicazioni, a seconda della configurazione del server. Consultare la documentazione online per informazioni su questo messaggio di errore:  0xXXXX. [CLIENT: 11.11.11.11]|  
  
## <a name="explanation"></a>Spiegazione  
Questo errore indica che la connessione è stata chiusa dal client. Questo errore potrebbe verificarsi poiché è scaduto il timeout della connessione. Nel messaggio di errore viene visualizzato un valore del sistema operativo che descrive il problema sottostante.  
  
## <a name="user-action"></a>Azione dell'utente  
Se il codice di errore nel messaggio è 0x2746 (valore decimale 10054), la connessione è stata reimpostata dal client, in genere a causa di un timeout. Per risolvere l'errore, aumentare il timeout della connessione nel client o nel programma che esegue la chiamata.  
  
Per determinare una possibile soluzione per altri valori del messaggio di errore, usare il comando **net helpmsg** del sistema operativo e specificare il valore decimale del codice di errore.  
  
Per altre informazioni sulla connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Configurazione di rete del server](~/database-engine/configure-windows/server-network-configuration.md) e [Configurazione di rete dei client](~/database-engine/configure-windows/client-network-configuration.md).  
  
## <a name="internal-only"></a>Solo interno  

