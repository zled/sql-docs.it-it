---
title: "Proprietà di configurazione di SQL Server Native Client (scheda flag) | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59af121d-c8b9-4faa-91a1-b664f2c9b441
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 96cb3184afd9481f91ef9d08ad4ae112425cbaac
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-native-client-configuration-properties-flags-tab"></a>Proprietà - Configurazione SQL Server Native Client (scheda Flag)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] su questo computer, i client comunicano con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite i protocolli disponibili nel server di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file della libreria Client nativa. Questa scheda consente di configurare il computer client in modo che richieda una connessione crittografata mediante SSL (Secure Sockets Layer). Se non è possibile ottenere una connessione crittografata, la connessione non viene stabilita.  
  
 Il processo di accesso viene sempre crittografato. Le opzioni riportate di seguito si applicano solo a dati crittografati. Per ulteriori informazioni su come [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di crittografare le comunicazioni e per istruzioni su come configurare il client per considerare attendibile l'autorità radice del certificato del server, vedere "crittografia delle connessioni a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]" e "procedura: abilitare connessioni crittografate al [!INCLUDE[ssDE](../../includes/ssde-md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentazione Online.  
  
## <a name="options"></a>Opzioni  
 **ForceEncryption**  
 Richiede una connessione mediante SSL.  
  
 **TrustServerCertificate**  
 Se è impostato su **No**, il processo client tenta di convalidare il certificato server. Sia il client che il server devono disporre di un certificato emesso da un'autorità di certificazione pubblica. Se il certificato non è presente nel computer client o se non viene convalidato, la connessione viene terminata.  
  
 Se è impostato su **Sì**, il client non convalida il certificato server e pertanto consente di usare un certificato autofirmato.  
  
 **Certificato server attendibile** è disponibile solo se **Forza crittografia protocollo** è impostato su **Sì**.  
  
  
