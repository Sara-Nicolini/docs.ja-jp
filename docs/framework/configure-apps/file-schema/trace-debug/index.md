---
title: "トレースおよびデバッグ設定のスキーマ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
caps.latest.revision: 14
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4c74874519d992985c49b49542c0c7fb63e8557b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---
# <a name="trace-and-debug-settings-schema"></a>トレースおよびデバッグ設定のスキーマ
トレースおよびデバッグの設定により、メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。  
  
 次の表に、トレース設定とデバッグ設定の各要素の機能を示します。  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|トレース ソースの `Listeners` コレクションにリスナーを追加します。|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|`Listeners` コレクションにリスナーを追加します。|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|`sharedListeners` コレクションにリスナーを追加します。|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|トレース スイッチを設定するレベルを指定します。|  
|[\<assert>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> メソッドの呼び出し時にメッセージ ボックスを表示するかどうかを指定し、メッセージの書き込み先のファイルの名前も指定します。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|トレース ソースの `Listeners` コレクションを消去します。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|トレースの `Listeners` コレクションを削除します。|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|トレースの `Listeners` コレクションのリスナーにフィルターに追加します。|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|`sharedListeners` コレクションのリスナーにフィルターを追加します。|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|トレース ソースの `Listeners` コレクションにリスナーを指定します。|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|トレースの `Listeners` コレクションにリスナーを指定します。|  
|[\<performanceCounters>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|トレースの `Listeners` コレクションからリスナーを削除します。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|トレース ソースの `Listeners` コレクションからリスナーを削除します。|  
|[\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|任意の source 要素または trace 要素が参照できるリスナーを含みます。|  
|[\<sources>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|トレース メッセージを開始するトレース ソースを保持します。|  
|[\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|トレース メッセージを開始するトレース ソースを指定します。|  
|[\<switches>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|トレース スイッチと、トレース スイッチを設定するレベルを保持します。|  
|[\<system.diagnostics>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|[\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.TraceSource>   
 <xref:System.Diagnostics.Debug>   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)

