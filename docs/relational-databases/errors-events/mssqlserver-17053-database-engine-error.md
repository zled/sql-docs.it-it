---
title: MSSQLSERVER_17053 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17053 (Database Engine error)
ms.assetid: e0a01f3d-d0aa-4c38-8bcc-82e59de50512
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 07c215c0ae360a5b386909cd64e9f3dfb2893bcf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809569"
---
# <a name="mssqlserver17053"></a>MSSQLSERVER_17053
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17053|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|OS_ERROR|  
|Testo del messaggio|%ls: è stato rilevato l'errore del sistema operativo %ls.|  
  
## <a name="explanation"></a>Spiegazione  
Si è verificato un errore del sistema operativo generico.  Lo stato risultante non è chiaro.  
  
## <a name="user-action"></a>Azione dell'utente  
In genere questo errore si verifica con altri errori e deve essere utilizzato per consentire di diagnosticare gli errori specifici. Alcuni esempi potrebbero essere costituiti da letture o scritture in file di dati o di log non eseguite in modo corretto, da operazioni di lettura o scrittura nel Registro di sistema o da altri errori relativi all'API Win32 non previsti.  
  
