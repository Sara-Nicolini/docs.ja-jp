---
title: "C# 演算子 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "cs.operators"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "アドレス演算子 [C#]"
  - "算術演算子 [C#]"
  - "代入演算子 [C#]"
  - "ビット処理演算子 [C#]"
  - "ブール演算子 [C#]"
  - "式 [C#], 演算子"
  - "間接演算子 [C#]"
  - "キーワード [C#], 演算子"
  - "論理演算子 [C#]"
  - "演算子 [C#]"
  - "関係演算子 [C#]"
  - "シフト演算子 [C#]"
  - "Visual C#, 演算子"
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
caps.latest.revision: 40
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 38
---
# C# 演算子
C\# には、多くの演算子が用意されています。演算子とは、式で実行する演算 \(数値演算、インデックス作成、関数呼び出しなど\) を指定する記号のことです。  多くの演算子は、ユーザー定義型に適用する際に[オーバーロード](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)して、その意味を変更できます。  
  
 整数型に対する演算 \(`==`、`!=`、`<`、`>`、`&`、                  `|` など\) は、通常、列挙型 \(`enum`\) で使用できます。  
  
 ここでは、C\# の演算子を優先順位の高い順に示します。  各セクションの演算子の優先順位は同じです。  
  
## 主な演算子  
 優先順位が最も高い演算子です。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x.y](../../../csharp/language-reference/operators/member-access-operator.md) – メンバー アクセス。  
  
 [x?.y](../../../csharp/language-reference/operators/null-conditional-operators.md) – null 条件付きのメンバー アクセス。  左側のオペランドが null の場合に null を返します。  
  
 [f\(x\)](../../../csharp/language-reference/operators/invocation-operator.md) – 関数の呼び出し。  
  
 [a&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md) – 集約オブジェクトのインデックス作成。  
  
 [a?&#91;x&#93;](../../../csharp/language-reference/operators/null-conditional-operators.md) – null 条件付きのインデックス作成。  左側のオペランドが null の場合に null を返します。  
  
 [x\+\+](../../../csharp/language-reference/operators/increment-operator.md) – 後置インクリメント。  x の値を返した後、1 大きくなった \(通常は整数 1 が加算された\) x の値で格納場所を更新します。  
  
 [x\-\-](../../../csharp/language-reference/operators/decrement-operator.md) –  後置デクリメント。  x の値を返した後、1 小さくなった \(通常は整数 1 が減算された\) x の値で格納場所を更新します。  
  
 [New](../../../csharp/language-reference/keywords/new-operator.md) – 型のインスタンス化。  
  
 [Typeof](../../../csharp/language-reference/keywords/typeof.md) – オペランドを表す System.Type オブジェクトを返します。  
  
 [Checked](../../../csharp/language-reference/keywords/checked.md) – 整数演算のオーバーフロー チェックを有効にします。  
  
 [Unchecked](../../../csharp/language-reference/keywords/unchecked.md) – 整数演算のオーバーフロー チェックを無効にします。  これがコンパイラの既定の動作です。  
  
 [default\(T\)](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md) – 型 T の既定の初期値 \(参照型の場合は null、数値型の場合は 0、構造体型の場合は 0 または null が格納されたメンバー\) を返します。  
  
 [Delegate](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) – delegate インスタンスを宣言して返します。  
  
 [Sizeof](../../../csharp/language-reference/keywords/sizeof.md) – 型オペランドのサイズをバイト単位で返します。  
  
 [\-\>](../../../csharp/language-reference/operators/dereference-operator.md) – メンバー アクセスと組み合わせてポインターを逆参照します。  
  
## 単項演算子  
 これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [\+x](../../../csharp/language-reference/operators/addition-operator.md) – x の値を返します。  
  
 [\-x](../../../csharp/language-reference/operators/subtraction-operator.md) – 数値の否定。  
  
 [\!x](../../../csharp/language-reference/operators/logical-negation-operator.md) – 論理否定。  
  
 [~x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) – ビットごとの補数。  
  
 [\+\+x](../../../csharp/language-reference/operators/increment-operator.md) – 前置インクリメント。  1 大きくなった \(通常は整数 1 が加算された\) x の値で格納場所を更新した後に x の値を返します。  
  
 [\-\-x](../../../csharp/language-reference/operators/decrement-operator.md) – 前置デクリメント。  1 小さくなった \(通常は整数 1 が減算された\) x の値で格納場所を更新した後に x の値を返します。  
  
 [\(T\)x](../../../csharp/language-reference/operators/invocation-operator.md) – 型キャスト。  
  
 [Await](../../../csharp/language-reference/keywords/await.md) – `Task` を待機します。  
  
 [&x](../../../csharp/language-reference/operators/and-operator.md) – アドレス。  
  
 [\*x](../../../csharp/language-reference/operators/multiplication-operator.md) – 逆参照。  
  
## 乗算演算子  
 これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x \* y](../../../csharp/language-reference/operators/multiplication-operator.md) – 乗算。  
  
 [x \/ y](../../../csharp/language-reference/operators/division-operator.md) – 除算。  オペランドが整数の場合、結果は 0 に近い整数になるように切り捨てられます \(例: `-7 / 2 is -3`\)。  
  
 [x % y](../../../csharp/language-reference/operators/modulus-operator.md) – 剰余。  オペランドが整数の場合、x を y で除算した剰余を返します。  `q = x / y` で `r = x % y` の場合、`x = q * y + r` になります。  
  
## 加法演算子  
 これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x \+ y](../../../csharp/language-reference/operators/addition-operator.md) – 加算。  
  
 [x – y](../../../csharp/language-reference/operators/subtraction-operator.md) – 減算。  
  
## シフト演算子  
 これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x \<\<  y](../../../csharp/language-reference/operators/left-shift-operator.md) – ビットを左へシフトし、右側には 0 を格納します。  
  
 [x \>\> y](../../../csharp/language-reference/operators/right-shift-operator.md) – ビットを右へシフトします。  左側のオペランドが `int` または `long` の場合、左側のビットには符号ビットが格納されます。  左側のオペランドが `uint` または `ulong` の場合、左側のビットには 0 が格納されます。  
  
## 関係演算子と型検査演算子  
 これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x \< y](../../../csharp/language-reference/operators/less-than-operator.md) – より小さい \(x が y より小さい場合は true\)。  
  
 [x \> y](../../../csharp/language-reference/operators/greater-than-operator.md) – より大きい \(x が y より大きい場合は true\)。  
  
 [x \<\= y](../../../csharp/language-reference/operators/less-than-equal-operator.md) – 以下。  
  
 [x \>\= y](../../../csharp/language-reference/operators/greater-than-equal-operator.md) – 以上。  
  
 [Is](../../../csharp/language-reference/keywords/is.md) – 型の互換性。  評価される左側のオペランドを右側のオペランドで指定された型 \(静的な型\) にキャストできる場合は、true を返します。  
  
 [As](../../../csharp/language-reference/keywords/as.md) – 型変換。  左側のオペランドを右側のオペランドで指定された型 \(静的な型\) にキャストして返します。ただし、`(T)x` が例外をスローした場合、`as` は `null` を返します。  
  
## 等値演算子  
 これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x \=\= y](../../../csharp/language-reference/operators/equality-comparison-operator.md) – 等価比較。  既定では、`string` 以外の参照型の場合、参照の等価性を返します \(等価テスト\)。  ただし、型は `==` をオーバーロードできるため、同一性のテストが目的の場合は `object` で `ReferenceEquals` メソッドを使用することをお勧めします。  
  
 [x \!\= y](../../../csharp/language-reference/operators/not-equal-operator.md) – 等しくない。  `==` のコメントを参照してください。  型が `==` をオーバーロードする場合は、`!=` をオーバーロードする必要があります。  
  
## 論理 AND 演算子  
 この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x & y](../../../csharp/language-reference/operators/and-operator.md) – 論理またはビットごとの AND。  通常、整数型および `enum` 型で使用できます。  
  
## 論理 XOR 演算子  
 この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x ^ y](../../../csharp/language-reference/operators/xor-operator.md) – 論理またはビットごとの XOR。  通常、整数型と `enum` 型で使用できます。  
  
## 論理 OR 演算子  
 この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x &#124; y](../../../csharp/language-reference/operators/or-operator.md) – 論理またはビットごとの OR。  通常、整数型および `enum` 型で使用できます。  
  
## 条件 AND 演算子  
 この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x && y](../../../csharp/language-reference/operators/conditional-and-operator.md) – 論理 AND。  最初のオペランドが false の場合、C\# では 2 番目のオペランドが評価されません。  
  
## 条件 OR 演算子  
 この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x &#124;&#124; y](../../../csharp/language-reference/operators/conditional-or-operator.md) – 論理 OR。  最初のオペランドが true の場合、C\# では 2 番目のオペランドが評価されません。  
  
## Null 合体演算子  
 この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x ?? y](../../../csharp/language-reference/operators/null-conditional-operator.md) – `x` が `null` 以外の場合は x を返します。null の場合は `y` を返します。  
  
## 条件演算子  
 この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [t ? x : y](../../../csharp/language-reference/operators/conditional-operator.md) – テスト `t` が true の場合は `x` を評価して返します。それ以外の場合は `y` を評価して返します。  
  
## 代入演算子とラムダ演算子  
 これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。  各演算子をクリックすると、演算子の詳細と例が記載されたページに移動します。  
  
 [x \= y](../../../csharp/language-reference/operators/assignment-operator.md) – 代入。  
  
 [x \+\= y](../../../csharp/language-reference/operators/addition-assignment-operator.md) – インクリメント。  `y` の値を `x` の値に加算した結果を `x` に格納し、新しい値を返します。  `x` が `event` を指定した場合、`y` は、C\# によってイベント ハンドラーとして追加される適切な関数である必要があります。  
  
 [x \-\= y](../../../csharp/language-reference/operators/subtraction-assignment-operator-1.md) – デクリメント。  `y` の値を `x` の値から減算した結果を `x` に格納し、新しい値を返します。  `x` が `event` を指定した場合、`y` は、C\# によってイベント ハンドラーとして削除される適切な関数である必要があります。  
  
 [x \*\= y](../../../csharp/language-reference/operators/multiplication-assignment-operator.md) – 乗算代入。  `y` の値を `x` の値に乗算した結果を `x` に格納し、新しい値を返します。  
  
 [x \/\= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) – 除算代入。  `x` の値を `y` の値で除算した結果を `x` に格納し、新しい値を返します。  
  
 [x %\= y](../../../csharp/language-reference/operators/modulus-assignment-operator.md) – 剰余代入。  `x` の値を `y` の値で除算した剰余を `x` に格納し、新しい値を返します。  
  
 [x &\= y](../../../csharp/language-reference/operators/and-assignment-operator.md) – AND 代入。  `y` の値と `x` の値の AND 演算を行った結果を `x` に格納し、新しい値を返します。  
  
 [x &#124;\= y](../../../csharp/language-reference/operators/or-assignment-operator.md) – OR 代入。  `y` の値と `x` の値の OR 演算を行った結果を `x` に格納し、新しい値を返します。  
  
 [x &#124;\= y](../../../csharp/language-reference/operators/xor-assignment-operator.md) – XOR 代入。  `y` の値と `x` の値の XOR 演算を行った結果を `x` に格納し、新しい値を返します。  
  
 [x \<\<\= y](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) – 左シフト代入。  `x` の値を `y` で指定した分だけ左へシフトした結果を `x` に格納し、新しい値を返します。  
  
 [x \>\>\= y](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) – 右シフト代入。  `x` の値を `y` で指定した分だけ右へシフトした結果を `x` に格納し、新しい値を返します。  
  
 [\=\>](../../../csharp/language-reference/operators/lambda-operator.md) – ラムダ宣言。  
  
## 算術オーバーフロー  
 算術演算子 \([\+](../../../csharp/language-reference/operators/addition-operator.md)、[\-](../../../csharp/language-reference/operators/subtraction-operator.md)、[\*](../../../csharp/language-reference/operators/multiplication-operator.md)、[\/](../../../csharp/language-reference/operators/division-operator.md)\) を実行すると、結果が数値型の有効な値の範囲を超えることがあります。  詳細については、各演算子に関するセクションを参照してください。概要は、以下のとおりです。  
  
-   整数の算術オーバーフローでは、<xref:System.OverflowException> がスローされるか、または結果の最上位ビットが破棄されます。  0 による整数除算では、常に `DivideByZeroException` がスローされます。  
  
-   浮動小数点数の算術オーバーフローまたは 0 による浮動小数点除算では、例外はスローされません。これは、浮動小数点型が IEEE 754 に基づいており、無限大および NaN \(Not a Number\) を表現できるためです。  
  
-   [小数](../../../csharp/language-reference/keywords/decimal.md)の算術オーバーフローでは、常に <xref:System.OverflowException> がスローされます。  0 による小数除算では、常に <xref:System.DivideByZeroException> がスローされます。  
  
 整数のオーバーフローが発生したときの対処方法は、実行コンテキスト \([checked または unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)\) によって異なります。  checked コンテキストの場合は、<xref:System.OverflowException> がスローされます。  unchecked コンテキストの場合は、結果の最上位ビットが破棄され、実行が続行されます。  このように、C\# ではオーバーフローを処理するのか、それとも無視するのかをユーザーが選択できます。  
  
 算術演算子の場合だけでなく、整数型から整数型へのキャスト \([long](../../../csharp/language-reference/keywords/long.md) から [int](../../../csharp/language-reference/keywords/int.md) へのキャストなど\) でもオーバーフローは発生し、その場合も実行が checked または unchecked のいずれかによって対処が異なります。  ただし、ビット処理演算子とシフト演算子ではオーバーフローは発生しません。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\#](../../../csharp/csharp.md)   
 [オーバーロードされた演算子](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)