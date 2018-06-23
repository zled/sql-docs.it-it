---
title: Creare un ruolo definito dall'utente | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4128993-2333-48c7-84b1-e51cdcea393d
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b8405be955cdfd4f0d8b9665665f8817c98b9d60
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169249"
---
# <a name="create-a-user-defined-role"></a>Creazione di un ruolo definito dall'utente
    
### <a name="to-create-a-user-defined-role"></a>Per creare un ruolo definito dall'utente  
  
1.  Aprire [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Scegliere **Esplora oggetti** dal menu **Visualizza** .  
  
3.  Nella barra degli strumenti di Esplora oggetti fare clic su **Connetti**e quindi su **Motore di database**.  
  
4.  Nella finestra di dialogo **Connetti al server** specificare un nome di server e selezionare una modalità di autenticazione. È possibile utilizzare un punto (.), (locale), o `localhost` per indicare il server locale.  
  
5.  Fare clic su **Connetti**.  
  
6.  Espandere i nodi Database, Database di sistema, msdb, Sicurezza e Ruoli.  
  
7.  Nel nodo Ruoli fare clic con il pulsante destro del mouse su Ruoli del database e quindi scegliere **Nuovo ruolo del database**.  
  
8.  Nella pagina Generale specificare un nome. Facoltativamente specificare un proprietario e gli schemi di proprietà e aggiungere i membri del ruoli.  
  
9. Facoltativamente, fare clic su **Autorizzazioni** e configurare le autorizzazioni per gli oggetti.  
  
10. Facoltativamente, fare clic su **Proprietà estese** e configurare le proprietà estese.  
  
11. Fare clic su **OK**.  
  
  