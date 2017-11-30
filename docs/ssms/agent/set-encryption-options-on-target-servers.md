---
title: Impostare le opzioni di crittografia nei server di destinazione | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d2f91c1117333f037d77d146000cf44ba885e292
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="set-encryption-options-on-target-servers"></a>Impostazione delle opzioni di crittografia nei server di destinazione
Se non è possibile utilizzare un certificato per le comunicazioni crittografate SSL (Secure Sockets Layer) tra server master e alcuni o tutti i server di destinazione e si desidera crittografare il canale di comunicazione, configurare i server di destinazione per l'utilizzo del livello di sicurezza necessario.  
  
Per configurare il livello di sicurezza appropriato necessario per uno specifico canale di comunicazione tra server master e server di destinazione, impostare la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]sottochiave del Registro di sistema di Agent **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\**\<*nome_istanza*>**\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)**nel server di destinazione su uno dei valori seguenti. Il valore di \<*nome_istanza*> è **MSSQL.***n*. Ad esempio, **MSSQL.1** o **MSSQL.3**.  
  
|Valore|Descrizione|  
|---------|---------------|  
|**0**|Disabilita la crittografia tra il server di destinazione e il server master. Selezionare questa opzione solo quando il canale tra il server di destinazione e il server master è protetto in altro modo.|  
|**1**|Attiva solo la crittografia tra il server di destinazione e il server master senza la convalida del certificato.|  
|**2**|Attiva la crittografia SSL completa, inclusa la convalida del certificato, tra il server di destinazione e il server master. Questa è l'impostazione predefinita. A meno che non ci siano motivi specifici per scegliere un valore diverso, è consigliabile non modificarla.|  
  
Se si specifica **1** o **2** , è necessario attivare la crittografia SSL sia nel server master sia nei server di destinazione. Se si specifica **2** , è necessario che nel server master sia presente un certificato firmato correttamente.  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry_md.md)]  
  
## <a name="see-also"></a>Vedere anche  
[Procedura: Abilitazione di connessioni crittografate al Motore di database (Gestione configurazione SQL Server)](http://msdn.microsoft.com/en-us/e1e55519-97ec-4404-81ef-881da3b42006)  
  
