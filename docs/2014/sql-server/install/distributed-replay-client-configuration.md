---
title: Configurazione Client riesecuzione distribuita | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccf03e32-6bd9-43c0-b9b6-9fe0d9163339
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 330334330fd27459f19d3746187150e20900bd93
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067729"
---
# <a name="distributed-replay-client-configuration"></a>Configurazione client Riesecuzione distribuita
  Usare la pagina di **Configurazione client Riesecuzione distribuita** dell'Installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per specificare gli utenti a cui si desidera concedere autorizzazioni amministrative per il servizio client Riesecuzione distribuita.  
  
 Gli utenti che dispongono di autorizzazioni amministrative disporranno di accesso illimitato al servizio client Riesecuzione distribuita.  
  
## <a name="options"></a>Opzioni  
 **Nome del controller**  
 Questo parametro è facoltativo e il valore predefinito è \< *vuota*>.  
  
 Immettere il nome del controller che il computer client comunicherà con per il servizio client Riesecuzione distribuita. Si noti quanto segue:  
  
-   Il nome deve essere un nome di dominio completo. Ad esempio, è possibile che un host denominato server1 nella gerarchia dei prodotti di Microsoft disponga di un nome di dominio completo server1.products.microsoft.com.  
  
-   Se è già stato configurato un controller, immettere il nome del controller durante la configurazione di ciascuno client.  
  
-   In caso contrario, è possibile lasciare vuoto il nome del controller. Tuttavia, è necessario immettere manualmente il nome del controller nel file **configurazione client** .  
  
 **Directory di lavoro**  
 Specificare la directory di lavoro per il servizio client Riesecuzione distribuita.  
  
 La directory di lavoro predefinita è \<*lettera unità*>:\Programmi\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\.  
  
 **Directory dei risultati**  
 Specificare la directory dei risultati per il servizio client Riesecuzione distribuita.  
  
 La directory dei risultati predefinita è \<*lettera unità*>:\Programmi\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\.  
  
  