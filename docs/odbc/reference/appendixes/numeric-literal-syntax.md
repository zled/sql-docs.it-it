---
title: Sintassi del valore letterale numerica | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 317b9753912c937399480473bca78bc7e11b7ce8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="numeric-literal-syntax"></a>Sintassi del valore letterale numerica
Per i valori letterali numerici in ODBC, viene utilizzata la sintassi seguente:  
  
 *valore letterale numerico* :: = *letterale numeric firmati &#124; letterale numerico senza segno*  
  
 *literal numeric firmati* :: = [*sign*] *letterale numerico senza segno*  
  
 *letterale numerico senza segno* :: = *letterale numerico esatto &#124; letterale numerici approssimati*  
  
 *letterale numerico esatto* :: = *intero senza segno* [*periodo*[*intero senza segno*]] *&#124; periodo di unsigned integer*  
  
 *accesso* :: = *segno &#124; meno (-)*  
  
 *literal numerici approssimati* :: = *esponente mantissa E*  
  
 *mantissa* :: = *letterale numerico esatto*  
  
 *esponente* :: = *integer firmato*  
  
 *integer firmato* :: = [*sign*] *intero senza segno*  
  
 *intero senza segno* :: = *cifre...*  
  
 *segno* :: =*+*  
  
 *segno di sottrazione* :: = -  
  
 *cifra* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 6 5 &#124; &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *periodo* :: =.
