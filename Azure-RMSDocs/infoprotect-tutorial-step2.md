---
title: クイック スタート チュートリアルの手順 2 - AIP
description: Azure Information Protection を簡単に試すためのチュートリアルの手順 2 - ポリシーの構成。
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/21/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
ms.openlocfilehash: daf2f9054576e5c1584b694b2358966b18e22fda
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2018
ms.locfileid: "42808019"
---
# <a name="step-2-configure-the-azure-information-protection-policy"></a>手順 2: Azure Information Protection ポリシーを構成する

>*適用対象: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Azure Information Protection には構成しないで使用できる既定のポリシーが付属していますが、ここではそのポリシーを確認し、いくつか変更を行います。

1. [手順 1](infoprotect-tutorial-step1.md) から引き続き、Azure Portal で **[分類]** > **[ポリシー]** > **[グローバル]** を選択して **[ポリシー: グローバル]** ブレードを開きます。 このブレードには、テナントに対して作成された既定の Azure Information Protection ポリシーが表示されます。

2. 表示されるラベルをよく理解しておいてください。
    
    - 分類用のラベル: **[Personal (個人)]**、**[Public (公開)]**、**[General (全般)]**、**[Confidential (社外秘)]**、**[Highly Confidential (非常に機密性の高い社外秘)]**。 最後の 2 つのラベルを展開するとサブラベルが表示されます。これは、分類にサブカテゴリを設定できることを示す例となります。
    
       > [!NOTE]
       > 実際の既定のポリシーは、このチュートリアルの既定のポリシーとは若干異なる場合があります。 たとえば、ラベル名が **[全般]** ではなく **[内部]** である場合や、**[非常に機密性の高い社外秘]** ではなく **[秘密]** である場合があります。 **[受信者のみ]** という名前のサブラベルがない場合、またはラベルがまったくない場合があります。 これらの違いは、テナントに対して作成された時期によっては既定のポリシーにさまざまなバージョンが存在するためです。 または、このチュートリアルを開始する前に、自分で編集した可能性があります。
       > 
       > 使用する既定のポリシーが異なる場合でも、このチュートリアルを使用することはできますが、この後に示す手順や図を参照するときに、これらの変更に注意してください。 最新の既定のポリシーに合わせて既定のポリシーを変更する場合は、「[Azure Information Protection の既定のポリシー](configure-policy-default.md)」を参照してください。
    
    - 既定の構成では、一部のラベルには視覚的なマーキングが構成されていることに注意してください。 視覚的なマーカーとは、フッター、ヘッダー、および透かしです。 既定のポリシーによっては、一部のラベルに保護が設定されていることもあります。 次に例を示します。 
    
    ![Azure Information Protection クイック スタート チュートリアル手順 3 - 既定ポリシー](./media/info-protect-policy-default-labelsv2.png)
    
3. ラベルの後、**[表示する設定を構成して、Information Protection のエンド ユーザーに適用する]** セクションに、ポリシー設定の一部も表示されます。 たとえば、既定のラベル セットはなく、ドキュメントと電子メールはラベルが必須ではなく、ユーザーがラベルを変更するときに理由を示す必要はありません。
    
    ![Azure Information Protection クイック スタート チュートリアル手順 3 - 既定ポリシー](./media/info-protect-policy-default-settings.png)

## <a name="changing-the-settings-for-a-default-label-and-prompt-for-justification"></a>既定のラベルと理由を求めるプロンプトの設定の変更

このチュートリアルでは、動作を確認するために各ポリシー設定のいくつかを変更します。

1. **[既定のラベルを選択]** で、**[全般]** を選択します。 

    以前のバージョンのポリシーを使用しているために、このラベルがない場合は、同等のラベルとして **[内部]** を選択します。

2. **[分類ラベルを低くする、ラベルを削除する、保護を削除する場合、ユーザーは理由を提供する必要があります]** オプションを **[オン]** に設定します。

3. さらに、**[Make the custom permissions option available to users]\(ユーザーがカスタム アクセス許可オプションを使用できるようにする\)** の設定を見つけます。 この設定が **[オフ]** になっている場合は、**[オン]** に変更します。
    
    既定値はいつサブスクリプションを取得したかに応じて異なるため、この設定を変更する必要がない場合があります。 チュートリアルの後半で保護されたドキュメントをユーザーと共有するために、カスタム アクセス許可を使用します。共有するユーザーは、お客様がエクスプローラーのファイルを右クリックするときに指定できます。

4. この **[ポリシー: グローバル]** ブレードで **[保存]** を選択します。操作を確認するメッセージが表示されたら **[OK]** を選択します。 このブレードを閉じます。

## <a name="creating-a-new-label-for-protection-visual-markers-and-a-condition-to-prompt-for-classification"></a>分類にプロンプトを出すために保護、視覚的なマーカー、および条件に新しいラベルを作成する

ここでは、**社外秘**に新しいサブラベルを作成します。

1. **[分類]** > **[ラベル]** メニュー オプションから、**[社外秘]** ラベルを右クリックし、**[サブラベルの追加]** を選択します。
    
    **[社外秘]** という名前のラベルがない場合は、代わりに別のラベルを選択するか、新しいラベルを作成し、それに応じてチュートリアルの手順を変更してかまいません。

2. **[サブラベル]** ブレードで、**[財務]** のラベル名を指定し、**従業員のみに制限される財務情報が含まれる機密データ**という説明を追加します。
    
    このテキストは、選択したラベルがどのような使用目的であるかを示しており、ユーザーに対してはツールヒントとして表示され、ユーザーがどのラベルを選択するかを決定するのに役立ちます。

3. **[このラベルを含むドキュメントやメールに対するアクセス許可の設定]** では、**[保護]** を選択してから、再び **[保護]** を選択します。
    
    ![Azure Information Protection ラベルに構成された保護](./media/info-protect-protection-bar-configured.png) 
    
4. **[保護]** ブレードで、**[Azure (cloud key)]\(Azure (クラウド キー)\)** が選択されていることを確認します。 このオプションが選択されていると、Azure Rights Management サービスによって文書と電子メールが保護されます。 また、**[アクセス許可の設定]** オプションが選択されていることを確認します。 次に、**[アクセス許可の追加]** を選択します。

5. **[アクセス許可の追加]** ブレードで、**[\<組織名> の追加 - すべてのメンバー]** を選択します。 たとえば、組織名が VanArsdel Ltd の場合、次のようなオプションが表示されます。
    
    ![すべてのメンバーに Azure Information Protection ラベルの保護アクセス許可を付与する](./media/info-protect-protection-all-members.png) 
    
    このオプションは、アクセス許可を付与できる組織内のすべてのユーザーを自動的に選択します。 ただし、他のオプションでテナントからグループまたはユーザーを検索して参照することができます。 または、**[詳細の入力]** オプションを選択すると、個別のメール アドレスや、別の組織のすべてのユーザーも指定することができます。

6. アクセス許可に対し、プリセット オプションから **[レビュー担当者]** を選択します。 このアクセス許可レベルが全部のアクセス許可ではなく一部のアクセス許可を自動的に付与することがわかります。
    
    ![共同作成者に Azure Information Protection ラベルの保護アクセス許可を付与する](./media/info-protect-protection-reviewer.png)
    
    **[カスタム]** オプションを使って、異なるアクセス許可レベルを選択したり、個々の使用権限を指定したりできます。 ただし、このチュートリアルでは、**[レビュー担当者]** オプションのままにします。 後で別のアクセス許可を調べて、指定したユーザーが保護されたドキュメントまたはメールでできることを制限する方法を確認してください。

7. **[OK]** をクリックして **[アクセス許可の追加]** ブレードを閉じると、**[保護]** ブレードが構成を反映するように更新されます。 次に例を示します。
    
     ![Azure Information Protection ラベルのアクセス許可構成を示す [保護] ブレード](./media/info-protect-protection-configured.png)
    
    **[アクセス許可の追加]** を選択すると、このアクションによって **[アクセス許可の追加]** ブレードが再び開き、さらにユーザーを追加して、別のアクセス許可を付与できます。 たとえば、特定のグループに表示アクセスだけを付与します。 このチュートリアルでは、すべてのユーザーに 1 つのアクセス許可セットのままにします。

8. コンテンツの有効期限とオフライン アクセスを確認して既定値のままにし、**[OK]** をクリックして保存して、**[保護]** ブレードを閉じます。

8. **[サブラベル]** ブレードに戻り、 **[視覚的なマーキングの設定]** セクションを見つけます。
    
    **[このラベルが付いたドキュメントにはフッターをつける]** 設定で、**[オン]** をクリックし、**[テキスト]** ボックスに「**Classified as Confidential**」と入力します。 
    
    **[Documents with this label have a watermark]** (このラベルのあるドキュメントに透かしを付ける) 設定では、**[On]** (オン) をクリックし、**[Text]** (テキスト) ボックスに組織の名前を入力します。 たとえば、「**VanArsdel, Ltd**」と入力します。 
    
    これらの視覚的なマーカーの外観を変更できますが、ここでは設定は既定値のままにしておきます。
    
9. **[Configure conditions for automatically applying this label]** (このラベルに自動的に適用する条件を構成する) セクションを見つけます。
    
    **[新しい条件の追加]** をクリックし、**[条件]** ブレードで次のように選択します。
    
    」を参照します。 **[条件のタイプを選択]**: 既定値の **[情報の種類]** のままにします。
    
    b. **[情報の種類を選択]** 検索ボックス: 「**クレジット カード番号**」と入力します。 検索結果から **[クレジット カード番号]** を選択します。
    
    c. **[Minimum number of occurrences]** (最小出現回数): 既定値の **1** のままにしておきます。
    
    d. **[Count occurrences with unique values only]** (一意の値のみを持つ出現回数のカウント): 既定値の **[Off]** (オフ) のままにしておきます。
    
    ![Azure Information Protection クイック スタート チュートリアル手順 3 - クレジット カードの条件を構成する](./media/step2-configure-condition.png)
    
    **[保存]** をクリックして **[サブラベル]** ブレードに戻ります。

10. **[サブラベル]** ブレードでは、以下のように、**[条件名]** に **[クレジット カード番号]** と表示され、**[出現回数]** に **1** が設定されています。
    
    ![Azure Information Protection クイック スタート チュートリアル手順 3 - クレジット カードの条件を構成する](./media/step2-see-condition.png)

11. **[このラベルの適用方法を選択]**: 既定値の **[推奨]** のままにします。既定のポリシー ヒントは変更しないでください。 

12. **[Enter notes for internal housekeeping]** (内部ハウスキーピング処理向けのメモを入力) ボックスに、「**For testing purposes only**」 (テスト用のみ) と入力します。

13. **[サブラベル]** ブレードで **[保存]** をクリックします。 確認するメッセージが表示されたら、**[OK]** をクリックします。 新しいラベルが作成され、保存されますが、まだポリシーには追加されていません。

14. **[分類]** > **[ポリシー]** メニュー オプションから **[グローバル]** をもう一度選択し、ラベルの横にある **[ラベルの追加または削除]** リンクを選択します。

15. **[ポリシー: ラベルの追加または削除]** ブレードから、作成したラベルを選択し、**[財務]** というサブラベルを選択して **[OK]** をクリックします。

16. **[ポリシー: グローバル]** ブレードにグローバル ポリシーの新しいサブラベルが表示されます。このサブラベルは、視覚的なマーキングと保護のために構成されています。 次に例を示します。

    ![Azure Information Protection クイック スタート チュートリアル手順 3 - 既定ポリシー構成済み](./media/info-protect-policy-configuredv2.png)
    
    設定は既定のラベルと妥当性の変更内容に従って構成されることもわかります。
    
    ![Azure Information Protection クイック スタート チュートリアル手順 3 - 設定構成済み](./media/info-protect-settings-configuredv2.png)
    

17. この **[ポリシー: グローバル]** ブレードで **[保存]** をクリックします。 操作を確認するメッセージが表示されたら、**[OK]** をクリックします。

Azure Portal を閉じても、開いたままにしておきこのチュートリアルが終わった後でさらにオプションを構成してみてもかまいません。

既定のポリシーの確認と変更が済んだので、次の手順では Azure Information Protection をインストールします。

|必要な詳細情報|追加情報|
|--------------------------------|--------------------------|
|既定のポリシーと異なるバージョンについて|[Azure Information Protection の既定のポリシー](configure-policy-default.md)|
|ポリシーの構成について|[Azure Information Protection ポリシーの構成](configure-policy.md)|
|保護のラベルを構成する詳細な手順|[Rights Management による保護でラベルを構成する方法](configure-policy-protection.md)|
|アクセス許可に関する詳細情報|[Azure Rights Management の使用権限を構成する](configure-usage-rights.md)|



>[!div class="step-by-step"]
[&#171; 手順 1](infoprotect-tutorial-step1.md)
[手順 3 &#187;](infoprotect-tutorial-step3.md)