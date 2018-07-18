---
title: "Passaggio 1: Configurare l'ambiente di sviluppo Python pyodbc | Microsoft Docs"
ms.custom: ''
ms.date: 07/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d591227354a950b36e085b350e207c4a8e89ff25
ms.sourcegitcommit: 974c95fdda6645b9bc77f1af2d14a6f948fe268a
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37890982"
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>Passaggio 1: Configurare l'ambiente di sviluppo per lo sviluppo Python con pyodbc

## <a name="windows"></a>Windows  
Connettersi al Database SQL tramite Python - pyodbc su Windows:
  
1. **Scarica programma di installazione di Python**.  
  Se il computer dispone di Python, è necessario installarlo. Andare alla [pagina di download di Python](https://www.python.org/downloads/windows/) e scaricare il programma di installazione appropriato. Ad esempio, se si usa un computer a 64 bit, scaricare il programma di installazione di Python 2.7 o 3.7 (x64).  
  
2. **Installare Python**.  Dopo aver scaricato il programma di installazione, procedere come segue: una. Fare doppio clic sul file per avviare il programma di installazione. B. Selezionare la lingua e accettare le condizioni. c. Seguire le istruzioni sullo schermo e Python devono essere installati nel computer. d. È possibile verificare che Python è installato, passare a `C:\Python27` oppure `C:\Python37` ed eseguire `python -v` o `py -v` (per 3.x) 
      
3. [**Installare Microsoft ODBC Driver for SQL Server in Windows**](../../odbc/windows/system-requirements-installation-and-driver-files.md#installing-microsoft-odbc-driver-for-sql-server)
  
4. **Aprire cmd.exe come amministratore**     

5. **Installare pyodbc tramite pip - Gestione pacchetti Python** (Sostituisci `C:\Python27\Scripts` con il percorso di Python installato)
```  
> cd C:\Python27\Scripts  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Connettersi al Database SQL tramite Python - pyodbc:
  
1. **Apri terminale**  

2. [**Installare Microsoft ODBC Driver for SQL Server in Linux**](../../odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

3.  **Installare pyodbc**  
```  
> sudo -H pip install pyodbc
```
