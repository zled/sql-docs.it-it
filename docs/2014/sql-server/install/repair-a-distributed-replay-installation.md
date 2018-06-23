---
title: Ripristinare un'installazione di Distributed Replay | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fcd8ca8-1ceb-457d-9545-096c74e274d7
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8adf917831b33c1603b3c0c4a1e7b678900cf7dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155709"
---
# <a name="repair-a-distributed-replay-installation"></a>Ripristinare un'installazione di Riesecuzione distribuita
  Il ripristino di un componente Riesecuzione distribuita (controller o client) comporta le operazioni seguenti:  
  
1.  Installare tutti i file associati sul disco e sostituire tutti i file esistenti.  
  
2.  Ricreare l'account del servizio Windows se l'account corrispondente è stato rimosso.  
  
 Non è possibile utilizzare l'operazione Ripristina per aggiungere o rimuovere componenti. Per aggiungere o rimuovere componenti, selezionare o deselezionare il componente corrispondente nell'albero delle funzionalità nella **Selezione funzionalità** pagina [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programma di installazione.  
  
### <a name="to-repair-a-failed-installation-of-distributed-replay"></a>Per ripristinare un'installazione con errori di Riesecuzione distribuita  
  
1.  Dal menu **Start** scegliere **Pannello di controllo**e quindi fare doppio clic su **Installazione applicazioni**.  
  
2.  Selezionare [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nella **Disinstalla o modifica programma** finestra, quindi nel [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] della finestra di dialogo fare clic su **correzione**.  
  
3.  Seguire i passaggi nel [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] procedura guidata e scegliere il **Selezione funzionalità** pagina, selezionare i componenti riesecuzione distribuita che si desidera ripristinare e quindi fare clic su **successivo.**.  
  
4.  Completare l'Installazione guidata di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per ripristinare le funzionalità di Riesecuzione distribuita selezionate.  
  
  