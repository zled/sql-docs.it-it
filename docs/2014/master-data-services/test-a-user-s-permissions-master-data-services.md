---
title: Testare le autorizzazioni di un utente (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: eb64dc4c49d39fd39cca2b67bb1ad187a96b12bb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170591"
---
# <a name="test-a-user39s-permissions-master-data-services"></a>Testare le autorizzazioni di un utente (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]è possibile creare un utente test e accedere all'applicazione Web per testare le autorizzazioni, Quando un utente tenta di accedere all'URL di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , le credenziali dell'utente vengono autenticate. In Internet Explorer le impostazioni di sicurezza controllano se l'autenticazione viene eseguita automaticamente o se l'utente deve immettere nome utente e password. Per modificare queste impostazioni, effettuare i passaggi seguenti:  
  
### <a name="to-test-a-users-security"></a>Per testare la sicurezza di un utente  
  
1.  In Internet Explorer 7 o versione successiva scegliere **Opzioni Internet**dal menu **Strumenti**, quindi fare clic sulla scheda **Sicurezza** .  
  
2.  Fare clic su **Intranet locale** e quindi sul pulsante **Livello personalizzato** .  
  
3.  Nella sezione **Autenticazione utente** scegliere **Richiedi nome utente e password**.  
  
4.  Alla successiva apertura della finestra del browser, verrà richiesto di immettere un nome utente e una password.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza &#40;Master Data Services&#41;](security-master-data-services.md)  
  
  